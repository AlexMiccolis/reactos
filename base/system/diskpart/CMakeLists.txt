
include_directories(${REACTOS_SOURCE_DIR}/sdk/lib/conutils)

list(APPEND SOURCE
    active.c
    add.c
    assign.c
    attach.c
    attributes.c
    automount.c
    break.c
    clean.c
    compact.c
    convert.c
    create.c
    delete.c
    detach.c
    detail.c
    diskpart.c
    dump.c
    expand.c
    extend.c
    filesystems.c
    format.c
    gpt.c
    help.c
    import.c
    inactive.c
    interpreter.c
    list.c
    merge.c
    misc.c
    offline.c
    online.c
    partlist.c
    recover.c
    remove.c
    repair.c
    rescan.c
    retain.c
    san.c
    select.c
    setid.c
    shrink.c
    uniqueid.c
    diskpart.h)

add_executable(diskpart ${SOURCE} diskpart.rc)
set_module_type(diskpart win32cui UNICODE)
target_link_libraries(diskpart conutils ${PSEH_LIB})
add_importlibs(diskpart advapi32 msvcrt kernel32 ntdll)

if(MSVC)
    add_importlibs(diskpart ntdll)
endif()

add_pch(diskpart diskpart.h SOURCE)
add_cd_file(TARGET diskpart DESTINATION reactos/system32 FOR all)

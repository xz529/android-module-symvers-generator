# Changelog extract_symvers.py

## v2 (current)
- Automatic detection of EXPORT_SYMBOL_GPL by matching the Ndx of the __ksymtab_<name> symbol with the __ksymtab_gpl section index
- CRC is now taken from the exporter module's OWN __kcrctab(_gpl) (matched by ascending symbol offset in the section), rather than
borrowed from the first available importer — more accurate and allows
to find real version conflicts
- Sanity-check: filtering out crc==0 and non-identifier names
(including a bug fixed with the false "gpl" symbol — the service
SECTION symbol __ksymtab_gpl was erroneously exported)
- Statistics at the end of the output (files/symbols/conflicts/vmlinux-only)
- --verbose: conflict warnings  CRC between modules
- Arch-check: readelf -h, error when mixing architectures in a single run

## Result on TECNO LJ9 firmware
- Files scanned: 528 (all .ko files from system_dlkm/vendor_dlkm/vendor_ramdisk,
including duplicate paths)
- Total symbols: 8277 (was 5545 in v1 — more precisely, due to honest GPL accounting
and extracting CRCs from real exporters, not just importers)
- Conflicts found: 3 — all between conninfra.ko and conninfra_mt6653.ko
(two modules export identically named symbols
connv3_coredump_get_issue_info/connv3_coredump_init/
connv3_sub_drv_ops_register with different CRCs — a real find,
important when attempting a rebuild: it indicates that these
are mutually exclusive alternative implementations for different revisions
of the connectivity chip, and not  compatible modules)
- Symbols resolved to vmlinux: 3050 (meaning the remaining ~5227 symbols are the internal connectivity of the firmware itself between vendor modules,
an indicator of the deep customization of MediaTek/Transsion on top of GKI)
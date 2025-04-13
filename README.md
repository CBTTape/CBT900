# CBT900
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 900 is a set of programs which run under either old MVS   *   FILE 900
//*           or z/OS to calculate MD5 checksums.  Please see the   *   FILE 900
//*           member called @FILEMD5, which contains descriptions   *   FILE 900
//*           of all the MD5**  pds members found in this file.     *   FILE 900
//*                                                                 *   FILE 900
//*      support:  sbgolob@cbttape.org                              *   FILE 900
//*                                                                 *   FILE 900
//*      SHA-1 and SHA-2 support added, May 2016.                   *   FILE 900
//*                                                                 *   FILE 900
//*      SHA-384 and SHA-512 support added, Aug 2016.               *   FILE 900
//*                                                                 *   FILE 900
//*      Fixed for 8-character TSO prefixes in z/OS 2.3.            *   FILE 900
//*                                                                 *   FILE 900
//*      Fixed by Peter Glanzmann for Extended Address Volumes.     *   FILE 900
//*                                                                 *   FILE 900
//*      More new members for File 900.                             *   FILE 900
//*                                                                 *   FILE 900
//*      SHA1PGM  - batch version of SHA1SUM.                       *   FILE 900
//*      SHA1PGM$ - JCL to assemble SHA1PGM.                        *   FILE 900
//*      SHA2PGM  - batch version of SHA2SUM.                       *   FILE 900
//*      SHA2PGM$ - JCL to assemble SHA2PGM.                        *   FILE 900
//*      MD5P24$  - JCL to assemble MD5P24 (24 bit version)         *   FILE 900
//*                 with IFOX00, using an MVS3.8 copy of            *   FILE 900
//*                 SYS1.MACLIB. IFOX00 can't handle new            *   FILE 900
//*                 macro features in z/OS SYS1.MACLIB.             *   FILE 900
//*                                                                 *   FILE 900
//*      And more new members for File 900.                         *   FILE 900
//*                                                                 *   FILE 900
//*      CKSPGM   - assembler source for the CKSPGM batch           *   FILE 900
//*                 program which is independent from the           *   FILE 900
//*                 CKSUM TSO command.                              *   FILE 900
//*                                                                 *   FILE 900
//*      CKSPGM$  - JCL to assemble CKSPGM and the CKSUMR           *   FILE 900
//*                 subprogram.                                     *   FILE 900
//*                                                                 *   FILE 900
//*      CKSUM    - assembler source for the 31-bit CKSUM TSO       *   FILE 900
//*                 command.  It calls the CKSUMR subprogram.       *   FILE 900
//*                                                                 *   FILE 900
//*      CKSUM$   - JCL to assemble CKSUM and the CKSUMR            *   FILE 900
//*                 subprogram.                                     *   FILE 900
//*                                                                 *   FILE 900
//*      CKSUM#   - TSO HELP text for the CKSUM TSO command.        *   FILE 900
//*                                                                 *   FILE 900
//*      CKSUMR   - assembler source for CKSUMR subprogram          *   FILE 900
//*                 This must be linked with the CKSUM TSO          *   FILE 900
//*                 command, and the CKSPGM program.                *   FILE 900
//*                                                                 *   FILE 900
//*      CKSUMR24 - assembler source for same CKSUMR subprogram,    *   FILE 900
//*                 with AMODE and RMODE removed for IFOX00         *   FILE 900
//*                 assembler.                                      *   FILE 900
//*                 Intended for MVS 3.8 systems.                   *   FILE 900
//*                                                                 *   FILE 900
//*      CKSUM24  - assembler source for the 24-bit CKSUM TSO       *   FILE 900
//*                 command.  Intended for MVS 3.8 systems.         *   FILE 900
//*                                                                 *   FILE 900
//*      CKSUM24$ - JCL to assemble CKSUM24 and CKSUMR24 using      *   FILE 900
//*                 the MVS 3.8 IFOX00 assembler, and link as       *   FILE 900
//*                 the 24-bit CKSUM TSO command.                   *   FILE 900
//*                                                                 *   FILE 900
//*      - - - - - - - - - - - - - - - - - - - - - - - - - - -      *   FILE 900
//*                                                                 *   FILE 900
//*      SHA1SUM  - Assembler source for SHA-1 generating command   *   FILE 900
//*                       (Fix. DS1LSTAR is always 0 for a PDSE,    *   FILE 900
//*                        so always read the dataset even if       *   FILE 900
//*                        DS1LSTAR is 0.)                          *   FILE 900
//*                                                                 *   FILE 900
//*      SHA2SUM  - Assembler source for SHA-2 generating command   *   FILE 900
//*                       (Fix. DS1LSTAR is always 0 for a PDSE,    *   FILE 900
//*                        so always read the dataset even if       *   FILE 900
//*                        DS1LSTAR is 0.)                          *   FILE 900
//*                                                                 *   FILE 900
//*      SHA3SUM  - Assembler source for SHA-384 generating command *   FILE 900
//*                       (Fix. DS1LSTAR is always 0 for a PDSE,    *   FILE 900
//*                        so always read the dataset even if       *   FILE 900
//*                        DS1LSTAR is 0.)                          *   FILE 900
//*                                                                 *   FILE 900
//*      SHA5SUM  - Assembler source for SHA-512 generating command *   FILE 900
//*                       (Fix. DS1LSTAR is always 0 for a PDSE,    *   FILE 900
//*                        so always read the dataset even if       *   FILE 900
//*                        DS1LSTAR is 0.)                          *   FILE 900
//*                                                                 *   FILE 900
//*      MD5      - Assembler source for MD5 subprogram, which      *   FILE 900
//*                 is a modification of the MD5 program for        *   FILE 900
//*                 REXX.  This must be linked with the MD5SUM      *   FILE 900
//*                 TSO command.                                    *   FILE 900
//*                                                                 *   FILE 900
//*      MD5A     - Assembler source for same MD5 subprogram,       *   FILE 900
//*                 with inline macros changed for IFOX00           *   FILE 900
//*                 assembler.  Intended for MVS370 systems.        *   FILE 900
//*                                                                 *   FILE 900
//*      MD5R     - Assembler source for same MD5 subprogram,       *   FILE 900
//*                 with 8 STCM instructions replaced with 2        *   FILE 900
//*                 STRV.  STRV is comparatively new, from circa    *   FILE 900
//*                 2002.  STRV is like ST but the bytes are        *   FILE 900
//*                 stored in reverse order, as in hex 12345678     *   FILE 900
//*                 being stored as hex 78563412. The MVS 3.8       *   FILE 900
//*                 assembler IFOX00 does not support the STRV      *   FILE 900
//*                 op code.                                        *   FILE 900
//*                                                                 *   FILE 900
//*      MD5COB$  - JCL to compile and run an Enterprise Cobol      *   FILE 900
//*                 program that calls the MD5 subroutine.          *   FILE 900
//*                                                                 *   FILE 900
//*      MD5DATA  - JCL to create test data for MD5SUM, the same    *   FILE 900
//*                 test data used in MD5REXX                       *   FILE 900
//*                                                                 *   FILE 900
//*      MD5FORT$ - JCL to compile and run a Fortran G program      *   FILE 900
//*                 that calls the MD5 subroutine.                  *   FILE 900
//*                                                                 *   FILE 900
//*      MD5PGM   - Batch program to produce the same output as     *   FILE 900
//*                 the MD5SUM command.                             *   FILE 900
//*                                                                 *   FILE 900
//*      MD5P24   - 24-bit version of MV5PGM.                       *   FILE 900
//*                                                                 *   FILE 900
//*      MD5PLI$  - JCL to compile and run an Enterprise PL/I       *   FILE 900
//*                 program that calls the MD5 subroutine.          *   FILE 900
//*                                                                 *   FILE 900
//*      MD5REXX  - A copy of the source code for the MD5 for       *   FILE 900
//*                 REXX by Leland Lucius, which was the base       *   FILE 900
//*                 from which member MD5 was created.              *   FILE 900
//*                                                                 *   FILE 900
//*      MD5SUM   - assembler source for the 31-bit MD5SUM TSO      *   FILE 900
//*                 command.  It calls the MD5 subprogram.          *   FILE 900
//*                       (Fix. DS1LSTAR is always 0 for a PDSE,    *   FILE 900
//*                        so always read the dataset even if       *   FILE 900
//*                        DS1LSTAR is 0.)                          *   FILE 900
//*                                                                 *   FILE 900
//*      MD5SUM$  - JCL to assemble MD5SUM and the MD5              *   FILE 900
//*                 subprogram.                                     *   FILE 900
//*                                                                 *   FILE 900
//*      MD5SUM#  - TSO HELP text for the MD5SUM TSO command.       *   FILE 900
//*                                                                 *   FILE 900
//*      MD5SUMA$ - JCL to assemble MD5SUM24 and MD5A using         *   FILE 900
//*                 IFOX00.  Intended for MVS370 systems.           *   FILE 900
//*                                                                 *   FILE 900
//*      MD5SUM2$ - JCL to assemble MD5SUM24 and MD5 using          *   FILE 900
//*                 ASMA90.                                         *   FILE 900
//*                                                                 *   FILE 900
//*      MD5SUM24 - Assembler source for the 24-bit MD5SUM TSO      *   FILE 900
//*                 command, which is the base from which the       *   FILE 900
//*                 31-bit version was converted. Much of this      *   FILE 900
//*                 code was borrowed from the COUNT TSO command    *   FILE 900
//*                 in File 300.  Intended for MVS 3.8 systems.     *   FILE 900
//*                                                                 *   FILE 900
//*      MD5URL   - Information about testing Leland Lucius's code  *   FILE 900
//*                 in MD5REXX                                      *   FILE 900
//*                                                                 *   FILE 900
```

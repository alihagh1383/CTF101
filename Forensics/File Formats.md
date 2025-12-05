# IDENTIFYING
Most of files have file signature ( Magic Number ) 
We can use Magic Numbers to identify

### Auto Identify 
One of linux commands is `file` 
file command scan file and show what is it ( most of the times ) 
```bash
file <file>
```
#Example-out
```
<file>: JPEG image data, JFIF standard 1.01, resolution (DPI), density 96x96, segment length 16, comment: "CREATOR: gd-jpeg v1.0 (using IJG JPEG v80), quality = 90", baseline, precision 8, 1024x576, components 3
```

### Manual Identify
other linux command is `xxd` or `hexdump`
xxd command show file bytes in hex and we can check the Magic Numbers 
```bash
xxd <file> | head  
```
#Example-out
```
00000000: 2550 4446 2d31 2e37 0a25 b5ed aefb 0a34  %PDF-1.7.%.....4
00000010: 2030 206f 626a 0a3c 3c20 2f4c 656e 6774   0 obj.<< /Lengt
00000020: 6820 3520 3020 520a 2020 202f 4669 6c74  h 5 0 R.   /Filt
00000030: 6572 202f 466c 6174 6544 6563 6f64 650a  er /FlateDecode.
00000040: 3e3e 0a73 7472 6561 6d0a 789c ed7d cb8e  >>.stream.x..}..
00000050: 2439 92d8 3dbe 228e d502 2ada f972 928b  $9..=."...*..r..
00000060: 421e 162b 0958 4080 566a 600f bd7b e8ca  B..+.X@.Vj..{..
00000070: ae5c 6191 2561 5607 e9f3 656f a37b b87b  .\a.%aV...eo.{.{
00000080: 6444 55f5 48ea 9c99 ee09 5ad2 8da4 f161  dDU.H.....Z....a
00000090: 0f1a cdc2 7982 ff7e 0cf0 af10 633e 3f7f  ....y..~....c>?.
```


[Magic Numbers](https://en.wikipedia.org/wiki/List_of_file_signatures)
### Others
- **binwalk**
	- `binwalk <file>`
- **stat**
	- `stat --format=%F <file>`
- **mimetype**
	- `mimetype <file>`‍‍‍‍‍
- **xdg-mime**
	- `xdg-mime query filetype <file>`

### Magic Numbers
| File Type                   | Magic Number (Hex)                    | ASCII        | Notes                                        |
| --------------------------- | ------------------------------------- | ------------ | -------------------------------------------- |
| **JPEG (JFIF/EXIF)**        | `FF D8 FF`                            | ÿØÿ          | Common JPEG header                           |
| JPEG (raw)                  | `FF D8 FF E0`                         | ÿØÿà         | JFIF                                         |
| JPEG (raw EXIF)             | `FF D8 FF E1`                         | ÿØÿá         | EXIF                                         |
| **PNG**                     | `89 50 4E 47 0D 0A 1A 0A`             | .PNG....     | Standard PNG signature                       |
| **GIF87a**                  | `47 49 46 38 37 61`                   | GIF87a       | GIF format                                   |
| **GIF89a**                  | `47 49 46 38 39 61`                   | GIF89a       | GIF format                                   |
| **BMP**                     | `42 4D`                               | BM           | Windows Bitmap                               |
| **TIFF (Little-Endian)**    | `49 49 2A 00`                         | II*.         | Intel byte order                             |
| **TIFF (Big-Endian)**       | `4D 4D 00 2A`                         | MM.*         | Motorola byte order                          |
| **WebP**                    | `52 49 46 46 ?? ?? ?? ?? 57 45 42 50` | RIFF....WEBP | RIFF-based WebP                              |
| **ICO**                     | `00 00 01 00`                         | ....         | Windows Icon File                            |
| **CUR**                     | `00 00 02 00`                         | ....         | Cursor file                                  |
| **MP3 (ID3)**               | `49 44 33`                            | ID3          | MP3 with ID3v2                               |
| **MP3 (Frame sync)**        | `FF FB` or `FF F3` or `FF F2`         | ÿû           | Raw MP3 frame                                |
| **FLAC**                    | `66 4C 61 43`                         | fLaC         | FLAC audio                                   |
| **WAV (RIFF)**              | `52 49 46 46`                         | RIFF         | Use with "WAVE" 8 bytes later                |
| **Ogg**                     | `4F 67 67 53`                         | OggS         | Ogg container                                |
| **MIDI**                    | `4D 54 68 64`                         | MThd         | MIDI music file                              |
| **MP4**                     | `00 00 00 ?? 66 74 79 70`             | ftyp         | ISO Base Media container                     |
| MP4 (QuickTime)             | `66 74 79 70 71 74`                   | ftypqt       | MOV/QuickTime                                |
| **MKV / WebM**              | `1A 45 DF A3`                         | ....         | EBML header                                  |
| **AVI**                     | `52 49 46 46 ?? ?? ?? ?? 41 56 49 20` | RIFF....AVI  | AVI chunk                                    |
| **PDF**                     | `25 50 44 46 2D`                      | %PDF-        | PDF document                                 |
| **PostScript**              | `25 21 50 53`                         | %!PS         | PostScript                                   |
| **EPS**                     | `C5 D0 D3 C6`                         | ....         | EPS binary format                            |
| **ZIP**                     | `50 4B 03 04`                         | PK..         | Standard ZIP file                            |
| ZIP (empty archive)         | `50 4B 05 06`                         | PK..         | Empty ZIP                                    |
| ZIP (spanned)               | `50 4B 07 08`                         | PK..         | Multi-part ZIP                               |
| **APK (Android)**           | `50 4B 03 04`                         | PK..         | Actually a ZIP                               |
| **JAR**                     | `50 4B 03 04`                         | PK..         | ZIP container                                |
| **RAR v1.5**                | `52 61 72 21 1A 07 00`                | Rar!....     | Legacy RAR                                   |
| **RAR v5.0**                | `52 61 72 21 1A 07 01 00`             | Rar!....     | New RAR format                               |
| **7-Zip**                   | `37 7A BC AF 27 1C`                   | 7z...'       | 7z archive                                   |
| **GZIP**                    | `1F 8B`                               | ..           | Gzip                                         |
| **BZIP2**                   | `42 5A 68`                            | BZh          | Bzip2                                        |
| **XZ**                      | `FD 37 7A 58 5A 00`                   | .7zXZ.       | xz compression                               |
| **Zstandard**               | `28 B5 2F FD`                         | (°/ý         | Zstd compressed                              |
| **ELF**                     | `7F 45 4C 46`                         | .ELF         | Linux executable                             |
| **EXE / MZ**                | `4D 5A`                               | MZ           | DOS/Windows PE starter                       |
| **PE (Windows Executable)** | `4D 5A` then later `50 45 00 00`      | PE..         | PE signature at offset                       |
| **Mach-O (32-bit)**         | `FE ED FA CE`                         | ....         | macOS executable                             |
| Mach-O (64-bit)             | `FE ED FA CF`                         | ....         | macOS executable                             |
| Mach-O Universal (Fat)      | `CA FE BA BE`                         | ....         | Fat binary                                   |
| **Class File (Java)**       | `CA FE BA BE`                         | ....         | Same bytes as Fat Mach-O but context differs |
| **Python .pyc**             | `42 0D 0D 0A` (varies)                | B...         | Depends on Python version                    |
| **SQLite**                  | `53 51 4C 69 74 65 20`                | SQLite       | SQLite DB header                             |
| **MySQL .frm**              | `FE FE FE FE`                         | ....         | MySQL table                                  |
| **DBF**                     | `03`                                  | .            | dBase file                                   |
| **ISO9660**                 | At offset 0x8001: `43 44 30 30 31`    | CD001        | ISO image                                    |
| **VHD**                     | `63 6F 6E 65 63 74 69 78`             | "conectix"   | Virtual Hard Disk                            |
| **VMDK**                    | `4B 44 4D 56`                         | KDMV         | VMware disk                                  |
| **QCOW2**                   | `51 46 49 FB`                         | QFIú         | QEMU image                                   |
| **BMP**                     | `42 4D`                               | BM           | Bitmap image                                 |
| **ICO**                     | `00 00 01 00`                         | ....         | Windows icon                                 |
| **PCAP**                    | `A1 B2 C3 D4`                         | ....         | Network capture                              |
| PCAP (swapped endian)       | `D4 C3 B2 A1`                         | ....         |                                              |
| PCAP-NG                     | `0A 0D 0D 0A`                         | ....         | New capture format                           |
| **XML**                     | `3C 3F 78 6D 6C`                      | <?xml        | Optional whitespace before                   |
|**HTML**|`3C 21 44 4F 43 54 59 50 45`|<!DOCTYPE|Standard HTML5|
|**RTF**|`7B 5C 72 74 66`|{\rtf|RTF document|
|**Microsoft Office (old)**|`D0 CF 11 E0 A1 B1 1A E1`|....|OLE Compound Document|
|**DOCX / XLSX / PPTX**|`50 4B 03 04`|PK..|Actually ZIP containing XML|
|**TrueType Font (TTF)**|`00 01 00 00 00`|.....|TTF|
|**OpenType Font (OTF)**|`4F 54 54 4F`|OTTO|OTF|
|**WOFF**|`77 4F 46 46`|wOFF|Web Open Font|
|**WOFF2**|`77 4F 46 32`|wOF2|Compressed WOFF|
|**.DS_Store (macOS)**|`00 00 00 01 42 75 64 31`|....Bud1|Apple DS_Store|
|**Regedit (.REG)**|`FF FE` or `EF BB BF`|BOM|Often starts with BOM|
|**Shell Script**|`23 21`|#!|Shebang (various interpreters)|
|**Unix Script**|`23 21 2F 62 69 6E 2F`|#!/bin/|bash, sh, python, etc.|
|**SSH private key**|`2D 2D 2D 2D 2D`|-----|"-----BEGIN "|
|**PGP signature**|`99` or `98`|.|Depends on version|
|**OpenSSH key (new)**|`6F 70 65 6E 73 73 68`|openssh|“openssh-key-v1”|


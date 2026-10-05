# ctf'in Codespace

A shareable x86-64 linux environment and workspace that comes with common testing and forensic tools installed

## How to Use

## Tools Included

### BINARY ANALYSIS / REVERSE ENGINEERING

file
  Identifies a file's type from its contents rather than its filename extension.
  Often one of the first commands to run on an unknown CTF file.

strings
  Extracts printable strings from binaries and other files.

objdump
  Displays information from object files and executables, including assembly,
  sections, and headers.

gdb
  GNU Debugger. Debug Linux programs, set breakpoints, inspect registers and
  memory, disassemble code, and step through program execution.

gcc / g++
  GNU C and C++ compilers. Compile source code and small test programs.

readelf
  Displays detailed information about ELF executables, including headers,
  sections, symbols, and program segments.

nm
  Lists symbols from object files and executables.

binutils
  Collection of binary utilities including objdump, readelf, nm, strings,
  objcopy, and related tools.

strace
  Traces Linux system calls made by a running program.

ltrace
  Traces calls a program makes to shared libraries.

checksec
  Checks binary security features such as NX, PIE, stack canaries, RELRO,
  and executable-stack protections.


### NETWORK / PACKET ANALYSIS

nmap
  Network scanner used to identify hosts, open ports, services, and service
  versions. Only scan systems you are authorized to test.

nc (netcat)
  General-purpose TCP/UDP connection utility.

tshark
  Command-line version of Wireshark. Reads and filters PCAP/PCAPNG captures
  using Wireshark display fields and can extract packet data.

dnsutils
  Package containing DNS investigation tools such as dig and nslookup.

whois
  Queries WHOIS registration information for domains and IP address ranges.



### FORENSICS / FILE INVESTIGATION

<!-- binwalk (binwalk3)
  Binwalk 3. Scans files for embedded files, compressed data, filesystem
  structures, firmware components, and known file signatures. Useful for
  extracting data hidden or concatenated inside other files. -->

jpeginfo
  Examines JPEG files and reports structural information and corruption.

pngcheck
  Checks PNG files for validity and displays PNG chunk information.

steghide
  Steganography tool that can embed and extract hidden data from supported
  image and audio files.

exiftool
  Reads and writes metadata in many file formats. Especially useful for
  examining image, document, audio, and video metadata.

foremost
  File-carving utility that extracts files based on headers, footers, and
  known file structures.

zbarimg (zbar-tools)
  Reads QR codes and common barcodes from image files.

7z (p7zip-full)
  Creates, extracts, and inspects many archive formats including 7z, ZIP,
  TAR, and others.

unzip
  Lists and extracts ZIP archives.


### CRYPTOGRAPHY / ENCODING

openssl
  Cryptographic command-line toolkit. Useful for hashes, certificates,
  encryption/decryption, TLS investigation, and key inspection.

gpg
  GNU Privacy Guard. Handles OpenPGP encryption, decryption, signatures,
  public keys, and private keys.

base64
  Encodes and decodes Base64 data.

xxd
  Creates hexadecimal dumps of files and converts hexadecimal data back
  into binary.


### DATA / SEARCH / SCRIPTING

python3
  Python interpreter. Useful for CTF scripting, decoding, parsing, automation,
  exploit development, and quick data analysis.

pip
  Python package installer.

jq
  Command-line JSON processor for querying, filtering, and transforming JSON.

sqlite3
  Command-line interface for inspecting and querying SQLite databases.

rg (ripgrep)
  Fast recursive text-search utility. Similar to grep but particularly useful
  for searching large directory trees and source-code collections.

grep
  Searches text for matching strings or regular expressions.

sed
  Stream editor useful for transforming and extracting text.

awk
  Text-processing language useful for extracting and manipulating structured
  command-line output.


### DOWNLOAD / TRANSFER

curl
  Transfers data using HTTP, HTTPS, and many other protocols. Useful for
  interacting with web applications and APIs.

wget
  Downloads files and web resources from URLs.


### COMMON USAGE AND FIRST-STEPS

For an unfamiliar file, useful starting commands include:

  file mysteryFile
  strings mysteryFile | less
  xxd mysteryFile | less
  exiftool mysteryFile
  binwalk mysteryFile

For an ELF binary:

  file someFile
  checksec --file=someFile
  strings someFile | less
  readelf -h someFile
  nm someFile
  gdb someFile

For packet captures: (examples)

  tshark -r capture.pcap -q -z io,phs (show protocol summary)
  tshark -r capture.pcap -Y dns ( show just dns packets)


For an image:

  file image.png
  exiftool image.png
  binwalk image.png
  pngcheck -v image.png

or for JPEG:

  jpeginfo -c image.jpg
  steghide info image.jpg



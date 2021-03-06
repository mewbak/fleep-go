# fleep

[![Go Report Card](https://goreportcard.com/badge/github.com/floyernick/fleep-go)](https://goreportcard.com/report/github.com/floyernick/fleep-go) [![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/floyernick/fleep-go/blob/master/LICENSE)

File format determination package for Go

## Getting Started

**fleep** is a package that determines file format by file signature (also known as "magic number").

## Installation

You can download the source using `go get` command:

```
go get github.com/floyernick/fleep-go
```

## Usage

Main function `GetInfo()` determines file format. It takes byte sequence (>=128) as an argument and returns `Info` structure.

`Info` has the following fields:

-  `Type` ([]string) -> list of suitable file types
-  `Extension` ([]string) -> list of suitable file extensions
-  `Mime` ([]string) -> list of suitable file MIME types

Also `Info` has the following methods:

-  `TypeMatches()` -> checks if file type matches with given type as an argument
-  `ExtensionMatches()` -> checks if file extension matches with given extension as an argument
-  `MimeMatches()` -> checks if file MIME type matches with given MIME type as an argument

There is an example:

```
package main

import (
	"fleep"
	"fmt"
	"io/ioutil"
)

func main() {
	file, _ := ioutil.ReadFile("gopher.png")      // Reads PNG file
	info, _ := fleep.GetInfo(file)                // Gets file format
	fmt.Println(info.Type)                        // Prints [raster-image]
	fmt.Println(info.Extension)                   // Prints [png]
	fmt.Println(info.Mime)                        // Prints [image/png]
	fmt.Println(info.TypeMatches("raster-image")) // Prints true
	fmt.Println(info.ExtensionMatches("jpg"))     // Prints false
	fmt.Println(info.MimeMatches("image/png"))    // Prints true
}

```

## Supported Formats

There is a list of supported formats (in alphabetical order):

*Raster Image:*

-  BMP
-  GIF
-  ICO
-  JP2
-  JPEG
-  PNG
-  PSD
-  TIFF
-  WEBP

*Raw Image:*

-  ARW
-  CR2
-  CRW
-  DNG
-  ERF
-  NEF
-  NRW
-  ORF
-  PEF
-  RAF
-  RAW
-  RW2
-  SRW
-  X3F

*Vector Image:*

-  AI
-  EPS

*3D Image:*

-  C4D
-  FBX
-  MA
-  MS3D
-  MTL
-  OBJ
-  PLY
-  WRL
-  X3D
-  XSI

*Audio:*

-  AAC
-  AC3
-  AIFF
-  AMR
-  AU
-  FLAC
-  M4A
-  MIDI
-  MKA
-  MP3
-  OGA
-  RA
-  VOC
-  WAV
-  WMA

*Video:*

-  3G2
-  3GP
-  ASF
-  AVI
-  FLV
-  M4V
-  MKV
-  MOV
-  MP4
-  MPG
-  OGV
-  SWF
-  VOB
-  WEBM
-  WMV

*Document:*

-  DOC
-  DOCX
-  EPUB
-  KEY
-  NUMBERS
-  ODP
-  ODS
-  ODT
-  PAGES
-  PDF
-  PPS
-  PPT
-  PPTX
-  RTF
-  XLS
-  XLSX
-  XML

*Archive:*

-  7Z
-  DMG
-  GZ
-  ISO
-  RAR
-  TAR.Z
-  ZIP

*Executable:*

-  COM
-  EXE
-  JAR

*Font:*

-  OTF
-  TTF
-  WOFF
-  WOFF2

*System:*

-  CAB
-  CAT
-  DLL
-  DRV
-  REG
-  SDB
-  SYS

*Database:*

-  SQLITE

## Contribute

We would be happy to receive your propositions of improvement! Read [Contributing Guide](https://github.com/floyernick/fleep-go/blob/master/CONTRIBUTING.md) for more details.

## License

This project is licensed under the **MIT License**.

## Authors

**Mykyta Paliienko** - [GitHub profile](https://github.com/floyernick)
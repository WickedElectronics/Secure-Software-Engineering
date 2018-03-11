# Project 7 - WordPress Pentesting

Time spent: **10** hours spent in total

> Objective: Find, analyze, recreate, and document **three vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Authenticated Cross-Site Scripting (XSS) via Media File Metadata CVE-2017-6814
- Summary: This vulnerability allows for XSS due to the improper handling of metadata of MP3 files when added to a playlist and attached to a post by an administrator. 
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.2.13
    - GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-7/mp3%20xss.gif "MP3 XSS Vulnerability")
  - Steps to recreate: 1) Log in as the admin.
				2) Create a new post
				3) Attach media to the post
				4) Drop in the special MP3 file
				5) Add the MP3 file to a playlist
				6) Attach this playlist to the post
				7) View the post to execute the vulnerability
  -Affected source code: 
 
 

2. (Required) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
1. (Required) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

## Assets

[1] – Specially crafted MP3 file - https://securify.nl/advisory/SFY20160742/xss.mp3

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


# Project 7 - WordPress Pentesting

Time spent: **10** hours spent in total

> Objective: Find, analyze, recreate, and document **three vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) [Authenticated Cross-Site Scripting (XSS) via Media File Metadata CVE-2017-6814](https://www.cvedetails.com/cve/CVE-2017-6814/)
- Summary: This vulnerability allows for XSS due to the improper handling of metadata of MP3 files when added to a playlist and attached to a post by an administrator.

    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.2.13
    
- [ ] GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-7/mp3%20xss.gif "MP3 XSS Vulnerability")
    
- [ ] Steps to recreate: First, log in as the admin. Next, create a new post. Click on "attach media" in the editor. Drag and drop in the special MP3 file. Once uploaded, Add the MP3 file to a playlist. Attach this playlist to the post that is being created. Finally, view the post to execute the vulnerability.
			
- [ ] Affected source code: wp_playlist_shortcode() method (/wp-includes/media.php): 
![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-7/mp3%20code1.png "MP3 XSS Vulnerability 1")

  renderTracks() method (/wp-includes/js/mediaelement/wp-playlist.js): 
  ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-7/mp3%20code2.png "MP3 XSS Vulnerability 2")
 
 

2. (Required) [Authenticated Shortcode Tags Cross-Site Scripting CVE-2015-5714](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5714)
  - [ ] Summary: 
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.3.1
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
    
3. (Required) Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: 
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

## Assets

[1 – Specially crafted MP3 file](https://securify.nl/advisory/SFY20160742/xss.mp3)

## Resources

- [1 - Sumofpwn advisory on "WordPress audio playlist functionality is affected by Cross-Site Scripting"](https://sumofpwn.nl/advisory/2016/wordpress_audio_playlist_functionality_is_affected_by_cross_site_scripting.html)
- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work


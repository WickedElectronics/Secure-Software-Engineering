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
  - [ ] Summary: This vulnerability allows for XSS due to the improper handling of the whitelist when publishing content. The shortcode is similar to HTML. Once the whitelist is defeated, a simple XSS is used and can maintain persistence. It is activated when any user hovers over the newly created link in the name of the post.
  
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.3.1
    
  - [ ] GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-7/post%20xss.gif "MP3 XSS Vulnerability")
  
  - [ ] Steps to recreate: First, log in as the administrator (or anyone that can publish a post). Next, create a new post. For the title, make it _TEST!!![caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">Click me</a>_. Save the post and be sure it is public and publised. Now, navigate to this post on the site, and hover the mouse over the text that says "Click me" to execute the vulnerability.
  
    
3. (Required) Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: This vulnerability allows for XSS due to the max length of an unauthenticated user's comment. Once the user hits this max length, the comment is truncated before it is stored into the database. If an administrator views this malicious comment, code can be executed on the server.
  
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
    
  - [ ] GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-7/comment%20xss.gif "MP3 XSS Vulnerability")
  
  - [ ] Steps to recreate: Simply have the site running with the capability for a user to post a comment. A user can then simply post a comment such as _<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 KB]..AAA'></a>_ where the AAA...AAA part takes up more than 64KB. Once an administrator views this malicious comment, it executes. For the sake of simplicity, I posted the comment and viewed it from the same administrator account. I have linked the actual content of my comment below.
  

## Assets

[1 – Specially crafted MP3 file](https://securify.nl/advisory/SFY20160742/xss.mp3)
[3 - Content of XSS comment for Unauthenticated Stored Cross-Site Scripting](https://pastebin.com/SMnhZHgG)

## Resources

- [1 - Sumofpwn advisory on "WordPress audio playlist functionality is affected by Cross-Site Scripting"](https://sumofpwn.nl/advisory/2016/wordpress_audio_playlist_functionality_is_affected_by_cross_site_scripting.html)
- [2 - wpvulndb proof of cencept of Authenticated Shortcode Tags Cross-Site Scripting](https://wpvulndb.com/vulnerabilities/8186)
- [3 - Klikki proof of concept on Unauthenticated Stored Cross-Site Scripting (XSS)](https://klikki.fi/adv/wordpress2.html)
- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

This lab was very challenging because of my unfamiliarity with PHP, WordPress, and generally finding and exploiting vulnerabilities. Sadly, what it really came down to was running WPScan, and going down the list with trail and error. Many of the known vulnerable plugins and themes are no longer available, so those attacks could not be reasonably setup in my test enviornment. Finding these three core exploits was a challenge, and definitely has given me a new appreciation for the hard work that security professionals put into finding these vulnerabilities as well as maintaining up-to-date databases of known exploits.

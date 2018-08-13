# rally-tracks-ingest

[Rally](https://github.com/elastic/rally) tracks to help macro benchmark Elasticsearch ingest node. 

Add the ingest tracks to ~/.rally/rally.ini
```
[tracks]
default.url = https://github.com/elastic/rally-tracks
ingest.url = https://github.com/jakelandis/rally-tracks-ingest
```

```
 esrally list tracks  --track-repository=ingest
```

Usage:

via track-repository
```bash
esrally --track=http_logs_for_ingest --track-repository=ingest --challenge=baseline
esrally --track=http_logs_for_ingest --track-repository=ingest --challenge=grok
esrally --track=http_logs_for_ingest --track-repository=ingest --challenge=dissect
``` 
 
testing locally (first run is very slow, but subsequent are fast):
```bash
esrally list tracks --track-path=~/workspace/rally-tracks-ingest/http_logs_for_ingest
esrally --track-path=~/workspace/rally-tracks-ingest/http_logs_for_ingest --target-hosts=localhost:9200 --pipeline=benchmark-only --challenge=baseline-manual
esrally --track-path=~/workspace/rally-tracks-ingest/http_logs_for_ingest --target-hosts=localhost:9200 --pipeline=benchmark-only --challenge=grok-manual
esrally --track-path=~/workspace/rally-tracks-ingest/http_logs_for_ingest --target-hosts=localhost:9200 --pipeline=benchmark-only --challenge=dissect-manual

``` 

 
### Data
 
Modifications from the [Web server logs from the 1998 Football world cup](http://ita.ee.lbl.gov/html/contrib/WorldCup.html): 
 
 * Applied "127.0.0.1" for all IP conversions (replaced the integer placeholder)
 * Skipped any log entry that would not result in valid UTF-8 encoding  
 * Transformed the source data to a bulk-friendly JSON format, with "message" as key
 
 ### Example Documents
 
 ```json
 { "message" : "127.0.0.1 - - [30/Apr/1998:21:30:17 +0000] \"GET /images/hm_bg.jpg HTTP/1.0\" 200 -"}
 { "message" : "127.0.0.1 - - [30/Apr/1998:21:30:53 +0000] \"GET /images/hm_bg.jpg HTTP/1.0\" 200 -"}
 { "message" : "127.0.0.1 - - [30/Apr/1998:21:31:12 +0000] \"GET /images/hm_bg.jpg HTTP/1.0\" 200 -"}
 ```
 
### License

Original license text:

               Copyright (C) 1997, 1998, 1999 Hewlett-Packard Company
                             ALL RIGHTS RESERVED.
     
      The enclosed software and documentation includes copyrighted works
      of Hewlett-Packard Co. For as long as you comply with the following
      limitations, you are hereby authorized to (i) use, reproduce, and
      modify the software and documentation, and to (ii) distribute the
      software and documentation, including modifications, for
      non-commercial purposes only.
          
      1.  The enclosed software and documentation is made available at no
          charge in order to advance the general development of
          the Internet, the World-Wide Web, and Electronic Commerce.
     
      2.  You may not delete any copyright notices contained in the
          software or documentation. All hard copies, and copies in
          source code or object code form, of the software or
          documentation (including modifications) must contain at least
          one of the copyright notices.
     
      3.  The enclosed software and documentation has not been subjected
          to testing and quality control and is not a Hewlett-Packard Co.
          product. At a future time, Hewlett-Packard Co. may or may not
          offer a version of the software and documentation as a product.
      
      4.  THE SOFTWARE AND DOCUMENTATION IS PROVIDED "AS IS".
          HEWLETT-PACKARD COMPANY DOES NOT WARRANT THAT THE USE,
          REPRODUCTION, MODIFICATION OR DISTRIBUTION OF THE SOFTWARE OR
          DOCUMENTATION WILL NOT INFRINGE A THIRD PARTY'S INTELLECTUAL
          PROPERTY RIGHTS. HP DOES NOT WARRANT THAT THE SOFTWARE OR
          DOCUMENTATION IS ERROR FREE. HP DISCLAIMS ALL WARRANTIES,
          EXPRESS AND IMPLIED, WITH REGARD TO THE SOFTWARE AND THE
          DOCUMENTATION. HP SPECIFICALLY DISCLAIMS ALL WARRANTIES OF
          MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE.
      
      5.  HEWLETT-PACKARD COMPANY WILL NOT IN ANY EVENT BE LIABLE FOR ANY
          DIRECT, INDIRECT, SPECIAL, INCIDENTAL OR CONSEQUENTIAL DAMAGES
          (INCLUDING LOST PROFITS) RELATED TO ANY USE, REPRODUCTION,
          MODIFICATION, OR DISTRIBUTION OF THE SOFTWARE OR DOCUMENTATION.
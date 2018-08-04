# rally-tracks-ingest

Add the ingest tracks to ~/.rally/rally.ini
```
[tracks]
default.url = https://github.com/elastic/rally-tracks
ingest.url = https://github.com/jakelandis/rally-tracks-ingest
```

```
 esrally list tracks  --track-repository=ingest
```
 
 See the [sample-data](https://github.com/jakelandis/sample-data/tree/master/world-cup-98#create-a-json-lines-compressed-file) instructions for how to create the /tmp/wc_day5*.json.lines.bz2 files referenced in the tracks. 
 
 TODO: put .bz2 files somewhere that we can leverage thee base_url and download them as needed  
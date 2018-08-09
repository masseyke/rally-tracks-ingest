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

```bash
esrally --track=http_logs_baseline --track-repository=ingest
esrally --track=http_logs_with_grok --track-repository=ingest
esrally --track=http_logs_with_dissect --track-repository=ingest
``` 
 

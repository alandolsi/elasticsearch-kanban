# Backup and Restore Elasticsearch Indices with Snapshots
## Register a Snapshot Repository
```
PUT https://isonbgvm138.isoad.isogmbh.de:9200/_snapshot/daily_snap?pretty
{
  "type": "fs",
  "settings": {
    "location": "/usr/share/elasticsearch/backups",
    "compress": true
  }
}
```
## Get Registred Repositories
```
GET https://isonbgvm138.isoad.isogmbh.de:9200/_cat/repositories?v
```
## Create a Snapshot
```
PUT https://isonbgvm138.isoad.isogmbh.de:9200/_snapshot/daily_snap/snapshot_1?wait_for_completion=true&pretty
```
## Get Snapshot Status
```
GET https://isonbgvm138.isoad.isogmbh.de:9200/_snapshot/daily_snap/snapshot_1?pretty
```
## Get All Snapshots
```
GET https://isonbgvm138.isoad.isogmbh.de:9200/_snapshot/daily_snap/_all?pretty
```
## Close all Indices
```
POST https://isonbgvm138.isoad.isogmbh.de:9200/_all/_close?pretty
```
## Restore a Snapshot
```
POST https://isonbgvm138.isoad.isogmbh.de:9200/_snapshot/daily_snap/snapshot_1/_restore?pretty
{
    "indices": "filebeat-*",
    "ignore_unavailable": true,
    "include_global_state": true
}
```
## Get Restore Status
```
GET https://isonbgvm138.isoad.isogmbh.de:9200/_snapshot/daily_snap/snapshot_1/_restore?pretty
```

## Open all Indices
```
POST https://isonbgvm138.isoad.isogmbh.de:9200/_all/_open?pretty
```
## Get All Indices
```
GET https://isonbgvm138.isoad.isogmbh.de:9200/_cat/indices?v
```
## Get CLuster Health
```
GET https://isonbgvm138.isoad.isogmbh.de:9200/_cluster/health?pretty
```
## Get Cluster State
```
GET https://isonbgvm138.isoad.isogmbh.de:9200/_cluster/state?pretty
```

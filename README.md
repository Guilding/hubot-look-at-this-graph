# Graphite graphs for Hubot (meme version)

Obnoxious fork of https://github.com/rick/hubot-graphme

Renders images like this:
![](http://i.imgur.com/GaatEim.png)

See upstream meme for more information:
https://www.youtube.com/watch?v=sIlNIVXpIns

## Installation

In your hubot project repo, run:

`npm install hubot-look-at-this-graph --save`

Then add **hubot-look-at-this-graph** to your `external-scripts.json`:

```json
[
  "hubot-look-at-this-graph"
]
```

## Configuration Variables


 - `HUBOT_GRAPHITE_URL` - Location where graphite web interface can be found (e.g., "https://graphite.domain.com")
 - `HUBOT_GRAPHITE_S3_BUCKET` - Amazon S3 bucket where graph snapshots will be stored
 - `HUBOT_GRAPHITE_S3_ACCESS_KEY_ID` - Amazon S3 access key ID for snapshot storage
 - `HUBOT_GRAPHITE_S3_SECRET_ACCESS_KEY` - Amazon S3 secret access key for snapshot storage
 - `HUBOT_GRAPHITE_S3_REGION` - (optional) Amazon S3 region (default: "us-east-1")
 - `HUBOT_GRAPHITE_S3_IMAGE_PATH` - (optional) Subdirectory in which to store S3 snapshots (default: "hubot-graphme")

Example:

```
export HUBOT_GRAPHITE_URL=http://graphite.example.com/
export HUBOT_GRAPHITE_S3_BUCKET=mybucket
export HUBOT_GRAPHITE_S3_ACCESS_KEY_ID=ABCDEF123456XYZ
export HUBOT_GRAPHITE_S3_SECRET_ACCESS_KEY=aBcD01234dEaDbEef01234
export HUBOT_GRAPHITE_S3_PREFIX=graphs
export HUBOT_GRAPHITE_S3_REGION=us-standard
```

## Sample Interaction

```
user1>> hubot look at this graph -1day vmpooler.usage.avg
hubot>> http://graphite.example.com/render?target=vmpooler.usage.avg&from=-1day&format=png
```

## All Commands

 - `hubot look at this graph vmpooler.running.*` - show a graph for a graphite query using a target
 - `hubot look at this graph -1h vmpooler.running.*` - show a graphite graph with a target and a from time
 - `hubot look at this graph -6h..-1h vmpooler.running.*` - show a graphite graph with a target and a time range
 - `hubot look at this graph -6h..-1h foo.bar.baz + summarize(bar.baz.foo,"1day")` - show a graphite graph with multiple targets


## Running tests

```
% npm install
% npm test
```

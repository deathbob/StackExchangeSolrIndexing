Getting Started
===============

(See bottom for Mac Getting Started)

1. Download a StackExchange dump of your choosing:
   http://www.clearbits.net/torrents/2076-aug-2012 (or the start
immediatly with the posts.xml.gz file)
1. Unzip the data set you're interested in (7-zip format) Or `gunzip
   posts.xml.gz`
1. Download Solr: http://lucene.apache.org/solr/
1. Start Solr:
```
cd apache-solr-x.x.x/example
java -jar -Dsolr.solr.home=<full_path_to_this_dir>/solr_home start.jar
```
1. Index documents (currently only works for posts):
```
python extractDocs.py "<full_path_to_stack_exchange_dump>/posts.xml"
```
(Configuration details can be found in solr_home/collection1/conf/schema.xml)
1. Commit the changes
```
http://localhost:8983/solr/update?commit=true
```
1. Search!
```
localhost:8983/solr/collection1/select?q=Tags:star-wars
```
1. And for a neat visual, try `file://localhost<full_path_to_this_dir>/plot.html?q=*:*` in your browser

If you want git to stop bothering you about the gunzipped and therefore missing post.xml.gz file, try `git update-index --assume-unchanged -z posts.xml.gz`



Getting Started, Mac Edition
===

1. Download a StackExchange dump of your choosing: http://www.clearbits.net/torrents/2076-aug-2012
1. Download something to open the damn 7z format. I used http://wakaba.c3.cx/s/apps/unarchiver.html
1. Extract the stack exchange dump
1. Install solr, `brew install solr`
1. Start Solr:
```
cd /usr/local/opt/solr/libexec/example
java -jar -Dsolr.solr.home=/Users/lovebob/src/StackExchangeSolrIndexing/solr_home start.jar
```
1. Index documents (currently only works for posts):
```
python extractDocs.py /Users/lovebob/src/StackExchangeSolrIndexing/data/scifi.stackexchange.com/posts.xml
```
(Configuration details can be found in solr_home/collection1/conf/schema.xml)
1. Commit the changes
```
http://localhost:8983/solr/update?commit=true
```
1. Search!
```
localhost:8983/solr/collection1/select?q=Tags:star-wars
(as an interesting aside, is there a stack exchange site that does not return any results for the tag 'star-wars'? I bet not)
```
1. And for a neat visual, try `file://localhost/Users/lovebob/src/StackExchangeSolrIndexing/plot.html?q=*:*` in your browser

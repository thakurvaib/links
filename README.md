DBpedia-Links
=============
A repo that contains links and alternative classifications for DBpedia. Other database owners can contribute links into the links folder. The link framework is run each day and validates all link contributions. An overiew and current errors can be seen at the [LinkViz](http://dbpedia.github.io/links/tools/linkviz/). 

# About

Links are the key enabler for retrieval of related information on the Web of Data and DBpedia is one of the central interlinking hubs in the Linked Open Data (LOD) cloud. The DBpedia-Links repository maintains linksets between DBpedia and other LOD datasets. System for maintenance, update and quality assurance of the linksets are in place and can be explored further.

In this README, we will include descriptions on how to download and use the links, run all available tools as well as pointers to the most important documentation. if questions remain please use the [GitHub Issue tracker](http://github.com/dbpedia/dbpedia-links/issues). If you want to give us more feedback, feel free to use the [DBpedia Discussion mailinglist](http://lists.sourceforge.net/lists/listinfo/dbpedia-discussion).

## Why upload your links?
All links you are contributing will be loaded (after a quality check) into the main DBpedia datasets and therefore will link to your data. Users of DBpedia can then better find your data. Also we will be able to tell you, which other external databases link to your data. 

# Repository license
All data in the repository links folder is provided as CC-0. All software is provided under Apache 2.0 License.

Please cite our [paper](http://ceur-ws.org/Vol-1695/paper21.pdf) :
```
@inproceedings{DojchinovskiDBpediaLinks,
  author = {Dojchinovski, Milan and Kontokostas, Dimitris and R{\"o}ßling, Robert and Knuth, Magnus and Hellmann, Sebastian},
  booktitle = {Proceedings of the SEMANTiCS 2016 Conference (SEMANTiCS 2016)},
  title = {DBpedia Links: The Hub of Links for the Web of Data},
  year = 2016
}
```

# How to contribute links to DBpedia?
If you're interested in contributing links and to learn more about the project, please visit the [how to wiki page](https://github.com/dbpedia/links/wiki/How-To-Contribute-Links-to-DBpedia) for more detailed informations. 


# How to download the monthly link release
If you want to download the current, or older, releases of the given links, please go [here](http://downloads.dbpedia.org/links/) and click at the corresponding month.

# How to download the daily link snapshot

The publishing process is automated via a cronjob which will run all given downloads, scripts, LIMES/SILK configurations, patches, etc. to generate the linksets. It is executed daily on our own server and published (http://downloads.dbpedia.org/links/snapshot)

Please check out the [how to](https://github.com/dbpedia/links/wiki/How-To-Contribute-Links-to-DBpedia#automated-process) for more informations regarding the automated process, how to set it up, run it and customize it.

# How to update links for one dataset
If you want to update links for one dataset, either create a new pull request to update the old linkset or follow the [how to](https://github.com/dbpedia/links/wiki/How-To-Contribute-Links-to-DBpedia) to learn more about how to create a patch for the dataset which will be applied automatically on the next release.

To make sure that your dataset is following proper conventions as mentioned in the [how to](https://github.com/dbpedia/links/wiki/How-To-Contribute-Links-to-DBpedia), you can run the `validate.sh` script in `tools/java-maven/bin/`.

For more information regarding the validating, generating and patching aspects check out the README from the [java-maven](https://github.com/dbpedia/links/tree/master/tools/java-maven)

# Overview of current linksets
An overiew and current errors can be seen at the [LinkViz}(http://dbpedia.github.io/links/tools/linkviz/). 

# How to run the link extraction framework

## Install
```
mvn clean install

# tests are deactivated by default, tests will test the links, so activating tests will make a full run of the software 
mvn clean install -DskipTests=true
```

## Running
```
# create a snapshot
mvn exec:java -Dexec.mainClass="org.dbpedia.links.CLI" -Dexec.args="--generate"

# create a snapshot, also running scripts (increase runtime, immensely)
mvn exec:java -Dexec.mainClass="org.dbpedia.links.CLI" -Dexec.args="--generate --scripts true"

# run everything for one folder, e.g. your contributed link folder:
mvn exec:java -Dexec.mainClass="org.dbpedia.links.CLI" -Dexec.args="--generate --scripts true --basedir links/dbpedia.org/YOUR_PROJECT"
```

# description of further tools in the repo and how to access/execute them

* `backlinks.py` This script can be executed via python 3 (please note that [rdflib](https://github.com/RDFLib/rdflib) needs to be installed). On start it will prompt for a full folder path, please insert the full path to the linkset destinated main folder. All n-triple files will be read in there and compared to every other linkset within the `links` folder and check if certain subjects within the given linkset are contained in other linksets. All the triples will be stored within a `backlinks.nt` file


# Contributors (alphabetically)

- Sarven Capadisli, AKSW, Uni Leipzig (Csarven)
- Pascal Christoph, (dr0i)
- Christopher Gutteridge (cgutteridge)
- Amy Guy, BBC / Uni Edinburgh (rhiaro)
- Sebastian Hellmann, AKSW, Uni Leipzig (kurzum)
- Anja Jentzsch, HPI Potsdam (ajeve)
- Barry Norton (BarryNorton)
- Heiko Paulheim, Uni Mannheim (HeikoPaulheim)
- Petar Ristoski, Uni Mannheim (petarR)
- Robert Rößling, AKSW, Uni Leipzig (rpod)
- Søren Roug, (sorenroug)

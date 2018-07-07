# semantic-bridge
A "[semantic](https://en.wikipedia.org/wiki/Semantic_Web) bridge" between [OpenStreetMap](http://openstreetmap.org) (OSM) and [Wikidata](http://wikidata.org) (WD) by **reciprocal** identification.

[ ![](assets/wdOsm-semanticBridge-480px.jpeg) ](assets#credits)

## Basics

All relevant feature at OSM can be tagged with [`key:wikidata`](https://wiki.openstreetmap.org/wiki/Key:wikidata), pointing to its Wikidata semantic.

When, at Wikidata infrastructure, at the pointed semantic (a Wikidata ID) there are also a pointer to OSM, the "semantic bridge" has been built (!), so there are a complete [authority control with reciprocal use](https://www.wikidata.org/wiki/Q24075706). The [`lookup.csv` table](data/lookup.csv) list the OSM features that offers this reciprocity.

At July 2018 there are:
* [**~63000** Wikidata entities](https://query.wikidata.org/#SELECT%20%28COUNT%28DISTINCT%20%3Fitem%29%20AS%20%3Fcount%29%20WHERE%20%7B%3Fitem%20wdt%3AP402%20%5B%5D.%7D%0A) with the [OSM relation ID (`P402`)](http://wikidata.org/entity/P402) property pointing to OSM.
* 10 checked items at the lookup table, ensuring that each OSM feature was really tagged with a reciprocal Wikidata identification.

## The lookup as certification

Some examples and fields description for the [`lookup.csv`](data/lookup.csv) main dataset of this project.

wdId|osm_type|osm_id|isReciprocal|check_date
----|--------|------|------|-------
[Q155](http://wikidata.org/entity/Q155)|R|[59470](https://www.openstreetmap.org/relation/59470) ([js](https://nominatim.openstreetmap.org/details.php?format=json&osmtype=R&osmid=59470))|y|2018-07-06
[Q17061](http://wikidata.org/entity/Q17061)|R|[23092](https://www.openstreetmap.org/relation/23092) ([js](https://nominatim.openstreetmap.org/details.php?format=json&osmtype=R&osmid=23092) fail)|y|2018-07-06
[Q2880208](http://wikidata.org/entity/Q2880208)|W|[75488634](https://www.openstreetmap.org/way/75488634) ([js](https://nominatim.openstreetmap.org/details.php?format=json&osmtype=W&osmid=75488634))|n|2018-07-06
[Q2500246](http://wikidata.org/entity/Q2500246)|N|[817882603](https://www.openstreetmap.org/node/817882603) ([js](https://nominatim.openstreetmap.org/details.php?format=json&osmtype=N&osmid=817882603))|n|2018-07-06
...|...|...|...|...

* `wdId`: the Wikidata ID, can be resolved by `http://wikidata.org/entity/{wdId}` 
* `osm_type`: the OSM datatype used to represent the feature. `R`=Relation (polygon), `W`=Way (line), `N`=Node (point).
* `osm_id`: the ID attributed to OSM feature in the check_date.
* `isReciprocal`: a flag to say that the Wikidata and OSM indications are reciprocal or not (`y` or `n`).
* `check_date`: an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date, when last checking procedure was performed.

The lookup is generated by software, see [`/src`](src).

------

[&#160; Contents and data of this project are dedicated to<br/> ![](assets/CC0-logo-200px.png) ](LICENSE.md)

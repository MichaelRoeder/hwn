# HWN to c:geo

[Harzer Wandernadel](https://www.harzer-wandernadel.de/) locations that can be importated to [c:geo](https://github.com/cgeo/cgeo). It contains the 222 stamp locations and some locations of special stamps. If a stamp belongs to one of the following groups, it is written in the stamps description:

| Stempeltyp | Symbol | Link | OSM |
|---|---|---|---|
| Harzer Wandernadel | 🥾 | [🔗](https://www.harzer-wandernadel-shop.de/Wanderpass-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/148007#map=10/51.7026/10.7865) |
| Altenauer Herzweg | 💓 | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Herzweg-Altenau) | [🔗](https://www.openstreetmap.org/relation/17730084#map=14/51.80453/10.44753) |
| Baudensteig | 🏡 | [🔗](https://www.harzinfo.de/erlebnisse/wandern/fernwanderungen-durch-den-harz/harzer-baudensteig) | [🔗](https://www.openstreetmap.org/relation/14139496#map=11/51.7153/10.4865) |
| Bernsteinkönig | B | [🔗](https://bernstein-hotels.de/aktivitaeten-bernstein-schlosshotel-ballenstedt/) |  |
| Burgen & Schlösser | 🏰 | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Harzer-Geschichtsorte-Burgen-Schloesser-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/9820471#map=10/51.8282/11.0089) |
| Goethe im Harz | ✍ | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Goethe-im-Harz-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/14137225#map=10/51.7236/10.6562) |
| Grenzweg | 🚩 | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Harzer-Grenzweg-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/14137757#map=11/51.7963/10.6284) |
| Harzer Hexenstieg | ⚝ | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Harzer-Hexen-Stieg-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/14137773#map=10/51.7532/10.6359) |
| Harzer Steiger | 💎 | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Harzer-Steiger-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/14137782#map=10/51.7056/10.7833) |
| Huy-Fallstein | H | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Huy-Fallstein-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/17927261#map=11/51.9885/10.8331) |
| Klosterwanderweg | 🕀 | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Klosterwanderweg-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/14139494#map=10/51.8421/10.7808) |
| Lutherweg | L | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Natur-Erleben-am-Lutherweg-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/14139495#map=10/51.5524/11.2707) |
| Selketal-Stieg | S | [🔗](https://www.harzer-wandernadel-shop.de/Begleitheft-Selketal-Stieg-DIN-A6) | [🔗](https://www.openstreetmap.org/relation/15902555#map=11/51.6679/11.1011) |
| Sonderstempel | 🏅 |  | [🔗](https://www.openstreetmap.org/relation/13056506#map=9/51.812/10.941) |
| Kostenpflichtige Sonderstempel | 💰 |  | [🔗](https://www.openstreetmap.org/relation/13056506#map=9/51.812/10.941) |
| Teil mehrerer Hefte | ⭐ | | |

## Usage

1. Download the [hwn.gpx](https://raw.githubusercontent.com/MichaelRoeder/hwn/main/hwn.gpx) file with the locations of the stamps. In addition, you can load the other gpx files for additional stamps of other books.
2. Import it to c:geo as gpx file.
3. Enjoy your hiking tour :smile:

## Creation of the file

This is more or less a documentation for myself. A typical user shouldn't read further :wink:

1. Download gpx file from https://www.harzer-wandernadel.de/stempelstellen/gps-download/
2. Create a new file with the following root XML:
```xml
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<gpx version="1.0" xsi:schemaLocation="http://www.topografix.com/GPX/1/0 http://www.topografix.com/GPX/1/0/gpx.xsd http://www.groundspeak.com/cache/1/0/1 http://www.groundspeak.com/cache/1/0/1/cache.xsd http://www.gsak.net/xmlv1/6 http://www.gsak.net/xmlv1/6/gsak.xsd" xmlns="http://www.topografix.com/GPX/1/0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:groundspeak="http://www.groundspeak.com/cache/1/0/1" xmlns:gsak="http://www.gsak.net/xmlv1/6" xmlns:cgeo="http://www.cgeo.org/wptext/1/0">

</gpx>
```
3. Copy all `wpt` elements from the downloaded gpx file into the root element of this new file.
4. Use an editor to search with the regular expression:
```
  <wpt([^>]+)>([^<]*<ele>[^<]*</ele>)?([^<]*<time>[^<]*</time>)?[^<]*<name>([^<]*)</name>([^<]*<cmt>[^<]*</cmt>)?[^<]*<desc>([^<]*)</desc>([^<]*<link[^<]*/>)?([^<]*<sym>[^<]*</sym>)?[^<]*<extensions>[^<]*<gpxx:([^<]*<gpxx:([^<]*<gpxx:[^<]*</gpxx:)*[^<]*</gpxx:)*[^<]*</gpxx:[^<]*</extensions>[^<]*</wpt>
```
and replace all occurrences with 
```
  <wpt\1>\n    <name>\4</name>\n    <desc>\6</desc>\n    <sym>Geocache</sym>\n    <type>Geocache|User defined cache</type>\n    <groundspeak:cache id="" available="True" archived="False">\n      <groundspeak:name>\4</groundspeak:name>\n      <groundspeak:placed_by>HWN</groundspeak:placed_by>\n      <groundspeak:owner></groundspeak:owner>\n      <groundspeak:type>User defined cache</groundspeak:type>\n      <groundspeak:container>Unknown</groundspeak:container>\n      <groundspeak:difficulty>0</groundspeak:difficulty>\n      <groundspeak:terrain>0</groundspeak:terrain>\n      <groundspeak:country>Germany</groundspeak:country>\n      <groundspeak:state></groundspeak:state>\n      <groundspeak:short_description html="False">\6</groundspeak:short_description>\n      <groundspeak:long_description html="True">\6</groundspeak:long_description>\n      <groundspeak:encoded_hints></groundspeak:encoded_hints>\n    </groundspeak:cache>\n    <gsak:wptExtension>\n      <gsak:Watch>false</gsak:Watch>\n      <gsak:IsPremium>false</gsak:IsPremium>\n      <gsak:FavPoints>-1</gsak:FavPoints>\n      <gsak:GcNote></gsak:GcNote>\n    </gsak:wptExtension>\n    <cgeo:cacheExtension>\n      <cgeo:assignedEmoji>0</cgeo:assignedEmoji>\n    </cgeo:cacheExtension>\n  </wpt>
``` 
(Group `\1` are the coordinates, `\4` is the name and `\6` is the description)

5. Check whether all elements have been transformed (e.g., search for `<time>`, `<cmt>` or one of the other tags that should have been removed).
6. Some of the stamps belong to special stamp groups. Use the following regex expression pairs to update their description:
    * Harzer Grenzweg: replace `<groundspeak:name>HWN(001|002|003|004|009|010|011|018|019|046|090|136|156|159|164|165|166|167|168|170)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description html="True">([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description html="True">\4&lt;br/&gt;Teil des Harzer Grenzwegs</groundspeak:long_description>`
    * Harzer Hexenstieg: replace `<groundspeak:name>HWN(009|013|017|022|040|041|042|052|060|062|063|069|123|128|133|136|137|140|155|178)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description html="True">([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description html="True">\4&lt;br/&gt;Teil des Harzer Hexenstiegs</groundspeak:long_description>`
    * Harzer Steiger: replace `<groundspeak:name>HWN(037|039|060|061|085|091|107|113|126|127|128|133|137|146|155|172|175|179|190|193|194|217|222)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description html="True">([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description html="True">\4&lt;br/&gt;Teil des Harzer Steigers</groundspeak:long_description>`
    * Goethe im Harz: replace `<groundspeak:name>HWN(009|013|014|031|038|041|042|062|069|071|078|080|085|088|091|095|099|101|105|116|117|129|132|136|140|144|155|188)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description html="True">([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description html="True">\4&lt;br/&gt;Teil von "Goethe im Harz"</groundspeak:long_description>`
    * Burgen &amp; Schlösser: replace `<groundspeak:name>HWN(080|084|187|197|200|201)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description\4&lt;br/&gt;Teil von Burgen &amp; Schlösser</groundspeak:long_description>`
    * Selketal-Stiegs: replace `<groundspeak:name>HWN(055|172|173|175|176|177|179|180|181|183|185|195|197|200|203|204|207)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description\4&lt;br/&gt;Teil des Selketal-Stiegs</groundspeak:long_description>`
    * Bernsteinkönig: replace `<groundspeak:name>HWN(061|180|181|199|200|202|204|207)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description\4&lt;br/&gt;Teil des Bernsteinkönigs</groundspeak:long_description>`
    * Quedlinburg: replace `<groundspeak:name>HWN(183|184|185|186|196)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description\4&lt;br/&gt;Teil des Begleitheft Festjahr Quedlinburg</groundspeak:long_description>`
    * Lutherweg: replace `<groundspeak:name>HWN(215|216|219)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description\4&lt;br/&gt;Teil des Lutherwegs</groundspeak:long_description>`
    * Altenauer Herzweg: replace `<groundspeak:name>HWN149([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description\4&lt;br/&gt;Teil des Altenauer Herzwegs</groundspeak:long_description>`
    * Baudensteig: replace `<groundspeak:name>HWN(101|115|130|144|150|151)([^<]*</groundspeak:name>([^<]*<groundspeak:[^l][^<]*</groundspeak:)*[^<]*)<groundspeak:long_description([^<]*)</groundspeak:long_description>` with `<groundspeak:name>HWN\1\2<groundspeak:long_description\4&lt;br/&gt;Teil des Baudensteigs</groundspeak:long_description>`
7. Add symbols
* replace `<cgeo:assignedEmoji>0</cgeo:assignedEmoji>` with `<cgeo:assignedEmoji>129406</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil des Altenauer Herzwegs[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>128681</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil des Baudensteigs[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>127969</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil des Bernstein[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>66</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil von Burgen[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>127984</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil von "Goethe im Harz"[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>9997</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil des Harzer Grenzwegs[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>128681</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil des Harzer Hexenstiegs[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>9885</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil des Harzer Steigers[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>128142</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil des Lutherwegs[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>76</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil des Selketal[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>83</cgeo:assignedEmoji>`
* replace `(<groundspeak:long_description[^<]*Teil[^<]*Teil[^<]*<\/groundspeak:long_description>)([^<]*)((<\/?[^c][^<]*)+)(<cgeo:cacheExtension>[^<]*)<cgeo:assignedEmoji>[^<]*<\/cgeo:assignedEmoji>` with `\1\2\3\4\5<cgeo:assignedEmoji>11088</cgeo:assignedEmoji>`

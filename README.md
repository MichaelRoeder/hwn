# HWN to c:geo

[Harzer Wandernadel](https://www.harzer-wandernadel.de/) locations that can be importated to [c:geo](https://github.com/cgeo/cgeo). It contains the 222 stamp locations and some locations of special stamps. If a stamp belongs to one of the following groups, it is written in the stamps description:
* Harzer Grenzweg
* Harzer Hexenstieg
* Harzer Steiger
* Goethe im Harz

## Usage

1. Download the [hwn.gpx](https://raw.githubusercontent.com/MichaelRoeder/hwn/main/hwn.gpx) file with the locations of the stamps (the special stamps are already included).
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
7. Add the special stamp locations from `special.gpx_part` to the file.

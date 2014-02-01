<a id="top"></a>
Metadata
================================================================================

Before files are processed, doctape collects metadata depending on the file
type, which you can access via the API. Each file object contains a `meta`
object with one ore more of the following fields:

Document
--------------------------------------------------------------------------------
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>title</td>
    <td>document title</td>
  </tr>
  <tr>
    <td>author</td>
    <td>document author</td>
  </tr>
  <tr>
    <td>doctag</td>
    <td>see <a target="_blank" href="http://www.doctag.org">doctag.org</a></td>
  </tr>
</table>

-----
> [back to top](#top)

-----

Image
--------------------------------------------------------------------------------
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
    <td>width</td>
    <td>image width in px</td>
  </tr>
  <tr>
    <td>height</td>
    <td>image height in px</td>
  </tr>
  <tr>
    <td>orientation</td>
    <td>orientation of image</td>
  </tr>
  <tr>
    <td>iso</td>
    <td>iso value</td>
  </tr>
  <tr>
    <td>flash</td>
    <td>image taken with or without flash?</td>
  </tr>
  <tr>
    <td>vendor</td>
    <td>camera vendor</td>
  </tr>
  <tr>
    <td>model</td>
    <td>camera model</td>
  </tr>
  <tr>
    <td>gps_latitude</td>
    <td>GPS latitude</td>
  </tr>
  <tr>
    <td>gps_latitude_reference</td>
    <td>GPS latitude reference (N or S)</td>
  </tr>
  <tr>
    <td>gps_longitude</td>
    <td>GPS longitude</td>
  </tr>
  <tr>
    <td>gps_longitude_reference</td>
    <td>GPS longitude reference (E or W)</td>
  </tr>
  <tr>
    <td>gps_altitude</td>
    <td>GPS altitude</td>
  </tr>
</table>

-----
> [back to top](#top)

-----

Audio
--------------------------------------------------------------------------------
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>title</td>
    <td>track title</td>
  </tr>
  <tr>
    <td>album</td>
    <td>track album</td>
  </tr>
  <tr>
    <td>artist</td>
    <td>track artist</td>
  </tr>
  <tr>
    <td>year</td>
    <td>track year</td>
  </tr>
  <tr>
    <td>genre</td>
    <td>track genre</td>
  </tr>
  <tr>
    <td>duration</td>
    <td>audio duration</td>
  </tr>
</table>

-----
> [back to top](#top)

-----

Video
--------------------------------------------------------------------------------
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>width</td>
    <td>video width in px</td>
  </tr>
  <tr>
    <td>height</td>
    <td>video height in px</td>
  </tr>
  <tr>
    <td>title</td>
    <td>title of video</td>
  </tr>
  <tr>
    <td>author</td>
    <td>video author</td>
  </tr>
  <tr>
    <td>rotation</td>
    <td>video rotation</td>
  </tr>
  <tr>
    <td>duration</td>
    <td>video duration</td>
  </tr>
</table>

-----
> [back to top](#top)

-----

Archive
--------------------------------------------------------------------------------
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>encrypted</td>
    <td>whether an archive is encrypted or not</td>
  </tr>
  <tr>
    <td>bytesComp</td>
    <td>size of compressed archive in bytes</td>
  </tr>
  <tr>
    <td>bytesUncomp</td>
    <td>size of uncompressed archive files in bytes</td>
  </tr>
  <tr>
    <td>numFiles</td>
    <td>number of files in archive</td>
  </tr>
</table>

-----
> [back to top](#top)

-----

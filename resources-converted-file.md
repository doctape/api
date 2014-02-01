<a href="top"></a>
Converted File
================================================================================

 - [Retrieve document (pdf)](#retrieve-document)
 - [Retrieve image (jpg)](#retrieve-image)
 - [Retrieve audio (mp3)](#retrieve-audio)
 - [Retrieve video (mp4)](#retrieve-video)
 - [Retrieve HD video (mp4)](#retrieve-video-hd)
 - [Retrieve poster (jpg)](#retrieve-poster)
 - [Retrieve HD poster (jpg)](#retrieve-poster-hd)


<a id="retrieve-document"></a>
Retrieve document (pdf)
--------------------------------------------------------------------------------
This works for all document files
### Route
    GET https://api.doctape.com/v1/doc/{id}/document.pdf
    
### Required scopes
    file.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
</table>

### Response (Binary)

-----
> [back to top](#top)

-----


<a id="retrieve-image"></a>
Retrieve image (jpg)
--------------------------------------------------------------------------------
This works for all image files

### Route
    GET https://api.doctape.com/v1/doc/{id}/image.jpg
    
### Required scopes
    file.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
</table>

### Response (Binary)

-----
> [back to top](#top)

-----

<a id="retrieve-audio"></a>
Retrieve audio (mp3)
--------------------------------------------------------------------------------
This works for all audio files

### Route
    GET https://api.doctape.com/v1/doc/{id}/audio.mp3
    
### Required scopes
    file.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
</table>

### Response (Binary)

-----
> [back to top](#top)

-----

<a id="retrieve-video"></a>
Retrieve video (mp4)
--------------------------------------------------------------------------------
This works for all video files

### Route
    GET https://api.doctape.com/v1/doc/{id}/video_640.mp4
    
### Required scopes
    file.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
</table>

### Response (Binary)

-----
> [back to top](#top)

-----

<a id="retrieve-video-hd"></a>
Retrieve HD video (mp4)
--------------------------------------------------------------------------------
This only works for video files that have a HD version

### Route
    GET https://api.doctape.com/v1/doc/{id}/video_1280.mp4
    
### Required scopes
    file.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
</table>

### Response (Binary)

-----
> [back to top](#top)

-----

<a id="retrieve-poster"></a>
Retrieve poster (jpg)
--------------------------------------------------------------------------------
This works for all video and audio files
### Route
    GET https://api.doctape.com/v1/doc/{id}/poster_640.jpg
    
### Required scopes
    file.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
</table>

### Response (Binary)

-----
> [back to top](#top)

-----

<a id="retrieve-poster-hd"></a>
Retrieve HD poster (jpg)
--------------------------------------------------------------------------------
This only works for video files that have a HD version

### Route
    GET https://api.doctape.com/v1/doc/{id}/poster_1280.mp4
    
### Required scopes
    file.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
</table>

### Response (Binary)

-----
> [back to top](#top)

-----
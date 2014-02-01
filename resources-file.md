<a id="top"></a>
File
================================================================================

 - [List files](#list-files)
 - [Retrieve file info](#retrieve-file-info)
 - [Update file info](#update-file-info)
 - [Retrieve file (original)](#retrieve-file)
 - [Retrieve file thumbnail (jpg)](#retrieve-file-thumbnail)
 - [Retrieve file thumbnail large (jpg)](#retrieve-file-thumbnail-large)
 - [Upload file(s)](#upload-file)
 - [Clone file](#clone-file)
 - [(Un-)publish file](#publish-file)
 - [Delete file](#delete-file)

 - [Extract archive (zip)](#extract-archive)


<a id="list-files"></a>
List files
--------------------------------------------------------------------------------
### Route
    GET https://api.doctape.com/v1/doc

### Required scopes
    file.read

### Parameters (Query string)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>include_meta</td>
    <td>include meta data for each file</td>
  </tr>
</table>

### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
  <tr>
    <td>public_url</td>
    <td>public file url</td>
  </tr>
  <tr>
    <td>name</td>
    <td>file name without extension</td>
  </tr>
  <tr>
    <td>extension</td>
    <td>file extension</td>
  </tr>
  <tr>
    <td>size</td>
    <td>file size in bytes</td>
  </tr>
  <tr>
    <td>time_added</td>
    <td>unix timestamp</td>
  </tr>
  <tr>
    <td>media_type</td>
    <td>
      one of the following: document, image, audio, video, archive, unknown
    </td>
  </tr>
  <tr>
    <td>tags</td>
    <td>tag array</td>
  </tr>
  <tr>
    <td>origin</td>
    <td>one of the following: webupload, dropbox, mail, mobile or tapename</td>
  </tr>
  <tr>
    <td>starred</td>
    <td>true | false</td>
  </tr>
  <tr>
    <td>shared</td>
    <td>0: own document, 1: personal share, uid: tape share</td>
  </tr>
  <tr>
    <td>processing_status</td>
    <td>ok, failed, processing</td>
  </tr>
  <tr>
    <td>meta</td>
    <td>take a look at <a href="/metainformation.md">metadata</a></td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "2224c539-e5d6-425a-8e0d-9516db6dc462": {
          "id": "2224c539-e5d6-425a-8e0d-9516db6dc462",
          "public_url": "http://dt.pe/w23Oj9",
          "name": "example017872",
          "extension": "jpg",
          "size": 730782,
          "time_added": 1358457759,
          "media_type": "image",
          "tags": ["+bobby", "#bobby/wallpaper"],
          "origin": "bobby/wallpaper",
          "shared": 0,
          "processing_status": "ok",
          "meta": {}
        },
        ...
      }
    }

-----
> [back to top](#top)

-----

<a id="retrieve-file-info"></a>
Retrieve file info
--------------------------------------------------------------------------------
### Route
    GET https://api.doctape.com/v1/doc/{id}

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

### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
  <tr>
    <td>public_url</td>
    <td>public file url</td>
  </tr>
  <tr>
    <td>name</td>
    <td>file name without extension</td>
  </tr>
  <tr>
    <td>extension</td>
    <td>file extension</td>
  </tr>
  <tr>
    <td>size</td>
    <td>file size in bytes</td>
  </tr>
  <tr>
    <td>time_added</td>
    <td>unix timestamp</td>
  </tr>
  <tr>
    <td>media_type</td>
    <td>
      one of the following: document, image, audio, video, archive, unknown
    </td>
  </tr>
  <tr>
    <td>tags</td>
    <td>tag array</td>
  </tr>
  <tr>
    <td>origin</td>
    <td>one of the following: webupload, dropbox, mail, mobile or tapename</td>
  </tr>
  <tr>
    <td>starred</td>
    <td>true | false</td>
  </tr>
  <tr>
    <td>shared</td>
    <td>0: own document, 1: personal share, uid: tape share</td>
  </tr>
  <tr>
    <td>processing_status</td>
    <td>ok, failed, processing</td>
  </tr>
  <tr>
    <td>meta</td>
    <td>take a look at <a href="/metainformation.md">metadata</a></td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "id": "2224c539-e5d6-425a-8e0d-9516db6dc462",
        "public_url": "http://dt.pe/w23Oj9",
        "name": "example017872",
        "extension": "jpg",
        "size": 730782,
        "time_added": 1358457759,
        "media_type": "image",
        "tags": ["+bobby", "#bobby/wallpaper"],
        "origin": "bobby/wallpaper",
        "shared": 0,
        "processing_status": "ok",
        "meta": {}
      }
    }

-----
> [back to top](#top)

-----

<a id="update-file-info"></a>
Update file info
--------------------------------------------------------------------------------
### Route
    POST https://api.doctape.com/v1/doc/{id}

### Required scopes
    file.update file.read 

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

### Parameters (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>name</td>
    <td>file name</td>
  </tr>
  <tr>
    <td>tags</td>
    <td>array containing all tags including shares and tapes</td>
  </tr>
  <tr>
    <td>starred</td>
    <td>true | false</td>
  </tr>
</table>

### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
  <tr>
    <td>public_url</td>
    <td>public file url</td>
  </tr>
  <tr>
    <td>name</td>
    <td>file name without extension</td>
  </tr>
  <tr>
    <td>extension</td>
    <td>file extension</td>
  </tr>
  <tr>
    <td>size</td>
    <td>file size in bytes</td>
  </tr>
  <tr>
    <td>time_added</td>
    <td>unix timestamp</td>
  </tr>
  <tr>
    <td>media_type</td>
    <td>
      one of the following: document, image, audio, video, archive, unknown
    </td>
  </tr>
  <tr>
    <td>tags</td>
    <td>tag array</td>
  </tr>
  <tr>
    <td>origin</td>
    <td>one of the following: webupload, dropbox, mail, mobile or tapename</td>
  </tr>
  <tr>
    <td>starred</td>
    <td>true | false</td>
  </tr>
  <tr>
    <td>shared</td>
    <td>0: own document, 1: personal share, uid: tape share</td>
  </tr>
  <tr>
    <td>processing_status</td>
    <td>ok, failed, processing</td>
  </tr>
  <tr>
    <td>meta</td>
    <td>take a look at <a href="/metainformation.md">metadata</a></td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "id": "2224c539-e5d6-425a-8e0d-9516db6dc462",
        "public_url": "http://dt.pe/w23Oj9",
        "name": "example017872",
        "extension": "jpg",
        "size": 730782,
        "time_added": 1358457759,
        "media_type": "image",
        "tags": ["+bobby", "#bobby/wallpaper"],
        "origin": "bobby/wallpaper",
        "shared": 0,
        "processing_status": "ok",
        "meta": {}
      }
    }

-----
> [back to top](#top)

-----

<a id="retrieve-file"></a>
Retrieve file (original)
--------------------------------------------------------------------------------
### Route
    GET https://api.doctape.com/v1/doc/{id}/original
    
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

<a id="retrieve-file-thumbnail"></a>
Retrieve file thumbnail (jpg)
--------------------------------------------------------------------------------
### Route
    GET https://api.doctape.com/v1/doc/{docid}/thumb_120.jpg
    
### Required scopes
    file.read

### Response (Binary)

-----
> [back to top](#top)

-----

<a id="retrieve-file-thumbnail-large"></a>
Retrieve file thumbnail large (jpg)
--------------------------------------------------------------------------------
### Route
    GET https://api.doctape.com/v1/doc/{docid}/thumb_320.jpg
    
### Required scopes
    file.read

### Response (Binary)

-----
> [back to top](#top)

-----

<a id="upload-file"></a>
Upload file(s)
--------------------------------------------------------------------------------
### Route
    POST https://api.doctape.com/v1/doc/upload

### Required scopes
    file.create

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>tags</td>
    <td>String of tags (separated with ",")</td>
  </tr>
  <tr>
    <td>starred</td>
    <td>true | false</td>
  </tr>
</table>


### Parameters (Body)
multiparted body with file

### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id</td>
  </tr>
  <tr>
    <td>name</td>
    <td>file name</td>
  </tr>
  <tr>
    <td>size</td>
    <td>file size</td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "2224c539-e5d6-425a-8e0d-9516db6dc462": {
          "id": "2224c539-e5d6-425a-8e0d-9516db6dc462",
          "name": "017872.jpg",
          "size": "730782",
        },
      }
    }
    
-----
> [back to top](#top)

-----

<a id="clone-file"></a>
Clone file
--------------------------------------------------------------------------------
None of the former tags is added to the clone.

### Route
    POST https://api.doctape.com/v1/doc/{id}/clone

### Required scopes
    file.create file.read

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

### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>file id of the cloned file</td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "cloned": true,
        "id": "1bde02fd-4082-4321-b210-7fe75a6e94ba"
      }
    }

-----
> [back to top](#top)

-----

<a id="publish-file"></a>
(Un-)publish file
--------------------------------------------------------------------------------
### Route
    POST https://api.doctape.com/v1/doc/{id}/public

### Required scopes
    file.update file.read

### Parameters (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>public</td>
    <td>true / false</td>
  </tr>
</table>

### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>public</td>
    <td>true / false</td>
  </tr>
  <tr>
    <td>public_url</td>
    <td>public url or empty string</td>
  </tr>
</table>

### Response (JSON)
    {
      "error": null,
      "result": {
        "published": false,
        "public_url": ""
      }
    }

-----
> [back to top](#top)

-----

<a id="delete-file"></a>
Delete file
--------------------------------------------------------------------------------
### Route
    DELETE https://api.doctape.com/v1/doc/{id}

### Required scopes
    file.delete file.read

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

### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>deleted</td>
    <td>true</td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "deleted": true
      }
    }

-----
> [back to top](#top)

-----

<a id="extract-archive"></a>
Extract archive (zip)
--------------------------------------------------------------------------------
After unzipping, all files will be added to the processing queue as if they were
uploaded directly. When processing finished, extracted files will appear in the
doc-listing.

### Route
    POST https://api.doctape.com/doc/{id}/extract

### Required scopes
    file.create file.read

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

### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>extracted</td>
    <td>true</td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "extracted": true
      }
    }

-----
> [back to top](#top)

-----

<a id="top"></a>
Tape
================================================================================
 
 - [List tapes](#list-tapes)
 - [Retrieve tape info](#retrieve-tape-info)
 - [Update tape info](#update-tape-info)


<a id="list-tapes"></a>
List tapes
--------------------------------------------------------------------------------
### Route
    GET https://api.doctape.com/v1/tape

### Required scopes
    tape.read file.read

### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>tape id</td>
  </tr>
  <tr>
    <td>name</td>
    <td>tape name</td>
  </tr>
  <tr>
    <td>live</td>
    <td>true / false</td>
  </tr>
  <tr>
    <td>shared_with</td>
    <td>array containing all usernames a tape is shared with</td>
  </tr>
  <tr>
    <td>files</td>
    <td>file ids</td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "c2b3b6cb-d9ae-47a5-9971-c8e99a0940b7": {
		  "id": "c2b3b6cb-d9ae-47a5-9971-c8e99a0940b7",
          "name": "bobby/nodesummit",
          "live": false,
          "shared_with": [ ],
          "files": [
            "2224c539-e5d6-425a-8e0d-9516db6dc462",
            "3f113968-1a84-4126-af6f-616008b208d9",
            "af905468-d2bb-4acc-a393-5aa952ef423d",
            "b42006b7-8833-4fbf-9b0b-eeb2efc6ed54"
          ]
        },
        "f48c2e69-d782-42e4-a25f-b6f3a1254e7d": {
		  "id": "f48c2e69-d782-42e4-a25f-b6f3a1254e7d",
          "name": "lastparty",
          "live": true,
          "shared_with": ["alice", "bob"],
          "files": [
            "2224c539-e5d6-425a-8e0d-9516db6dc462",
            "3f113968-1a84-4126-af6f-616008b208d9",
            "af905468-d2bb-4acc-a393-5aa952ef423d",
            "b42006b7-8833-4fbf-9b0b-eeb2efc6ed54"
          ]
        }
      }
    }

-----
> [back to top](#top)

-----

<a id="retrieve-tape-info"></a>
Retrieve tape info
--------------------------------------------------------------------------------
### Route
    GET https://api.doctape.com/v1/tape/{id}

### Required scopes
    tape.read file.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>tape id</td>
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
    <td>tape id</td>
  </tr>
  <tr>
    <td>name</td>
    <td>tape name</td>
  </tr>
  <tr>
    <td>live</td>
    <td>true / false</td>
  </tr>
  <tr>
    <td>shared_with</td>
    <td>array containing all usernames a tape is shared with</td>
  </tr>
  <tr>
    <td>files</td>
    <td>file ids</td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "id": "3f113968-e5d6-4fbf-8e0d-616008b208d9",
        "name": "bobby/wallpaper",
        "live": true,
        "shared_with": [ ],
        "files": [
          "2224c539-e5d6-425a-8e0d-9516db6dc462",
          "3f113968-1a84-4126-af6f-616008b208d9",
          "af905468-d2bb-4acc-a393-5aa952ef423d",
          "b42006b7-8833-4fbf-9b0b-eeb2efc6ed54"
        ]
      }
    }

-----
> [back to top](#top)

-----

<a id="update-tape-info"></a>
Update tape info
--------------------------------------------------------------------------------
### Routes
    POST https://api.doctape.com/v1/tape/{id}

### Required scopes
    tape.update tape.read file.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>tape id</td>
  </tr>
</table>

### Parameters (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>live</td>
    <td>true / false</td>
  </tr>
  <tr>
    <td>shared_with</td>
    <td>array containing all usernames a tape is shared with</td>
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
    <td>tape id</td>
  </tr>
  <tr>
    <td>name</td>
    <td>tape name</td>
  </tr>
  <tr>
    <td>live</td>
    <td>true / false</td>
  </tr>
  <tr>
    <td>shared_with</td>
    <td>array containing all usernames a tape is shared with</td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        "id": "3f113968-e5d6-4fbf-8e0d-616008b208d9",
        "name": "bobby/wallpaper",
        "live": true,
        "shared_with": [ ],
        "files": [
          "2224c539-e5d6-425a-8e0d-9516db6dc462",
          "3f113968-1a84-4126-af6f-616008b208d9",
          "af905468-d2bb-4acc-a393-5aa952ef423d",
          "b42006b7-8833-4fbf-9b0b-eeb2efc6ed54"
        ]
      }
    }
    
-----
> [back to top](#top)

-----

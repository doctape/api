<a id="top"></a>
Account
================================================================================

 - [Retrieve user data](#retrieve-user-data)
 - [Retrieve user avatar](#retrieve-user-avatar)


<a id="retrieve-user-data"></a>
Retrieve user data
--------------------------------------------------------------------------------
### Route

    GET https://api.doctape.com/v1/account

### Required scopes

    account.read

#### Response (JSON)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>quota</td>
    <td>memory quota</td>
  </tr>
  <tr>
    <td>username</td>
    <td>username</td>
  </tr>
  <tr>
    <td>firstname</td>
    <td>firstname</td>
  </tr>
  <tr>
    <td>lastname</td>
    <td>lastname</td>
  </tr>
  <tr>
    <td>email</td>
    <td>email</td>
  </tr>
  <tr>
    <td>country_code</td>
    <td>country code (e.g. EN or DE)</td>
  </tr>
  <tr>
    <td>avatar</td>
    <td>url to retrieve avatar</td>
  </tr>
  <tr>
    <td>quota_used</td>
    <td>used memory quota</td>
  </tr>
  <tr>
    <td>quota_free</td>
    <td>free memory quota</td>
  </tr>
  <tr>
    <td>type</td>
    <td>basic or pro user</td>
  </tr>
</table>

### Response (Example)
    {
      "error": null,
      "result": {
        quota: 5000000000,
		username: "bob",
		firstname: "",
		lastname: "",
		email: "bob@bobsdomain.com",
		country_code: "EN",
		avatar: "https://my.doctape.com/v1/account/avatar/50",
		quota_used: 3121749,
		quota_free: 4996878251,
		type: "basic"
      }
    }

-----
> [back to top](#top)

-----

<a id="retrieve-user-avatar"></a>
Retrieve user avatar
--------------------------------------------------------------------------------
### Route
    GET https://api.doctape.com/v1/account/avatar/{size}

### Required scopes
    account.read

### Parameters (Route)
<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>size</td>
    <td>supported pixel sizes: 50, 300, 600</td>
  </tr>
</table>

### Response (Binary)

-----
> [back to top](#top)

-----

# CMS API Documentation
## Frontend

### Subscriber Register

#### Request
- Method: **POST**
- URL:  ```{{domain}}/Subscriber/register```
- Headers：
- Body:

Key | Value | Remark
--- | --- | ---
**email** | `example@gmail.com` | user email
**password** | `examplepwd` | user password
**birthday** | `2000-01-20` | user birthday (YYYY-MM-DD)
**gender** | `M` | user gender (M/F)
```
{
    "email" : "example@gmail.com",
    "password": "examplepwd",
    "birthday": "2000-10-20",
    "gender": "M"
}
```

#### Response

##### Success
```
{
    "status": true,
    "msg": "Register Success",
}
```
##### Failed
```
{
    "status": false,
    "msg": "Register Failed",
}
```

### Subscriber Login

#### Request
- Method: **POST**
- URL:  ```{{domain}}/Subscriber/login```
- Headers：
- Body:

Key | Value | Remark
--- | --- | ---
**email** | `example@gmail.com` | user email
**password** | `examplepwd` | user password
```
{
    "email" : "example@gmail.com",
    "password": "examplepwd"
}
```
#### Response

##### Success
The `data` value is `{{user_token}}`.

```
{
	"status": true,
	"msg": "Login Success",
	"data": "sdsaiudsaduisaduiasyui328468923"
}
```
##### Failed
```
{
    "status": false,
    "msg": "Login Failed",
    "data": ""
}
```

### Subsciber Change Password

#### Request
- Method: **POST**
- URL:  ```{{domain}}/Subscriber/changePassword```
- Headers：
- Body:

Key | Value | Remark
--- | --- | ---
**token** | `{{user_token}}` | user token
**current_password** | `{{current_password}}` | current password
**new_password** | `{{new_password}}` | new password
```
{
    "token": "{{user_token}}",
    "current_password": "{{current_password}}",
    "new_password": "{{new_password}}"
}
```

#### Response

##### Success
```
{
    "status": true,
    "data": "",
    "msg": "Update Password Success"
}
```
##### Failed
```
{
    "status": false,
    "data": "",
    "msg": "Update Password Failed"
}
```
### Subsciber Profile

#### Request
- Method: **POST**
- URL:  ```{{domain}}/User/info```
- Headers：
- Body:

Key | Value | Remark
--- | --- | ---
**token** | `{{user_token}}` | user token
```
{
    "token": "{{user_token}}"
}
```

#### Response

##### Success
```
{
    "status": true,
    "msg": "",
    "data": {
        "username": "",
        "email": "",
        "birthday": "",
        "gender": {},
        "status": false,
        "created_date": "",
        "updated_time": ""
    }
}
```
##### Failed
```
{
    "status": false,
    "msg": "No Data Found"
}
```

### Default Theme File

#### Request
- Method: **GET**
- URL:  ```{{domain}}/Theme/Default```
- Headers：
- Body:

#### Response

##### Success

```
{
    "status": true,
    "data": ["https://cms-theme1.s3.amazonaws.com/Style_01/css/all.min.css", "https://cms-theme1.s3.amazonaws.com/Style_01/css/select2.min.css"],
    "msg": ""
}
```
##### Failed
```
{
    "status": "false",
    "msg": "No Theme File Found, Please check theme manager setting."
}
```
### Category Lisitng

#### Request
- Method: **GET**
- URL:  ```{{domain}}/Category/Listing```
- Headers：
- Body:

#### Response

##### Success
```
{
    "status": true,
    "data": [{
        "folder_path": "Category/war/"
    }, {
        "folder_path": "Category/romance/"
    }],
    "msg": ""
}
```
##### Failed
```
{
    "status": true,
    "data": [],
    "msg": ""
}
```

### Get Movie By Category

#### Request
- Method: **GET**
- URL:  ```{{domain}}/Category/get?category={{category file name}}```
- Headers：
- Body:
- Query:

Key | Value | Remark
--- | --- | ---
**category** | `renders` | file category name

#### Response

##### Success
```
{
    "status": true,
    "data": [{
        "file_name": "5_6264607317619114308.doc.jpg",
        "xTitle": "Fast And Furious 8",
        "xDesc": "Movie Desc",
        "xUpdated_date": "2021-03-25 10:33:58",
        "xBucketId": 17,
        "xUrl": "https://mix-content.s3.amazonaws.com/Category/Adventure/5_6264607317619114308.doc",
        "folder_path": "Category/war/"
    }],
    "msg": ""
}
```
##### Failed
```
{
    "status": true,
    "data": [],
    "msg": ""
}
```
## 微信小程序 置创明匠OA
### 1. 登录

**简要描述：**

*   用户登录接口

**请求URL：**

*   `http://xx.com/api/user/login`

**请求方式：**

*   POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :-- | :-- | :-- | --- |
| openid | 是 | string | 微信唯一标识 |


> 注意

**返回示例**

```
    {
    "result": "success",
    "msg": "登陆成功!",
    "data": {
        "uid":"1",
        "username":"张杰",
        "department":"商务部",
        "auth":["leave","auth_2","auth_3"],
        "groupid": 2 ,
        "reg_time": "1436864169",
        "last_login_time": "0"
        }
    }

```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :-- | :-- | --- |
| msg | string| success:登陆成功！error：未注册！ |
| uid | string | 用户id |
| username | string | 真实姓名 |
| department | string | 所属部门 |
| groupid | int | 用户组id，1：超级管理员；2：普通用户 |
| auth |Array<string> |用户权限集合，leave、报销、考勤等；不同职责使用不同功能 |
| reg_time |string|注册时间 |
| last_login_time |string|上次登录时间 |

**备注**
> 

---
### 2. 发送邮箱验证码


**简要描述：**

*   发送邮箱验证码接口

**请求URL：**

*   `http://xx.com/api/user/send_email_code`

**请求方式：**

*   POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :-- | :-- | :-- | --- |
| email | 是 | string | 待验证邮箱 |

> 注意

**返回示例**

```
    {
    "result": "success",
    "msg": "验证码已发送!",
    "data": ""
    }

```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :-- | :-- | --- |
| msg | string| success:验证码已发送!  error：1.企业邮箱不存在；2.验证码发送失败! |

**备注**

> 

---
### 3. 注册

**简要描述：**

*   用户注册接口

**请求URL：**

*   `http://xx.com/api/user/register`

**请求方式：**

*   POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :-- | :-- | :-- | --- |
| openid | 是 | string | 微信唯一标识 |
| email | 是 | string | 待注册邮箱|
| code | 是 | string |用户输入的验证码|

> 注意

**返回示例**

```
    {
    "result": "success",
    "msg": "注册成功!",
    "data": {
        "uid":"1",
        "username":"张杰",
        "department":"商务部",
        "auth":["leave","auth_2","auth_3"],
        "groupid": 2 ,
        "reg_time": "1436864169",
        "last_login_time": "0"
        }
    }

```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :-- | :-- | --- |
| msg | string| success:注册成功！error：验证码错误！ |
| uid | string | 用户id |
| username | string | 真实姓名 |
| department | string | 所属部门 |
| groupid | int | 用户组id，1：超级管理员；2：普通用户 |
| auth |Array<string> |leave、报销、考勤等； 用户权限，不同职责使用不同功能 |
| reg_time |string|注册时间 |
| last_login_time |string|上次登录时间 |

**备注**
> 

---
### 4. 请求请假列表

**简要描述：**

*   请求请假列表

**请求URL：**

*   `http://xx.com/api/leave/list`

**请求方式：**

*   POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :-- | :-- | :-- | --- |
| openid | 是 | string | 微信唯一标识 |
| username | 是 | string | 用户名 |



**返回示例**

```
  {
  "result":"success",
  "msg":"",
  "data":"[
            { id:1,
              style:"病假",
              application_date:"2017-9-30",
              date:[
                     {day:"2017-10-1",time:1},
                     {day:"2017-10-2",time:0.5}
                   ],
              attach:".",
              audit:true,
              status:true
            },
            { id:2,
              style:"事假",
              application_date:"2017-9-30",
              date:[
                     {day:"2017-10-1",time:1},
                     {day:"2017-10-2",time:0.5}
                   ],
              attach:"",
              audit:true,
              status:true
            }
          ]"
      
  }

```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :-- | :-- | --- |
| id | int | 请假单id |
| style | String | 请假类型,病假/事假 |
| application_date | String | 申请时间 |
| date| Array| day：请假日期  , time:请假时间   1/0.5(天) |
| attach | Base64 | 病假条图片 |
| audit | boolean | 是否可以删除请假单 true:可以,flase:不可以 |
| status | boolean | 请假单是否通过领导审批  true:通过,flase:没通过|



---
### 5. 删除请假单


**简要描述：**

*   删除请假单

**请求URL：**

*   `http://xx.com/api/leave/delete`

**请求方式：**

*   POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :-- | :-- | :-- | --- |
| openid | 是 | string | 微信唯一标识 |
| username | 是 | string | 用户名 |
| id | 是 | int | 请假单id |

> 注意

**返回示例**

```
 {
   "result":"success",
   "msg":"删除成功！",
   "data":""
 }

```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :-- | :-- | --- |
| result | String | 删除是否成功 success:成功,error:失败 |
| msg | String | 返回提示 |


---
### 6. 请求添加请假单

**简要描述：**

*   请求添加请假单

**请求URL：**

*   `http://xx.com/api/leave/add`

**请求方式：**

*   POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :-- | :-- | :-- | --- |
| openid | 是 | string | 微信唯一标识 |
| username | 是 | string | 用户名 |
| department | 是 | string | 用户所属部门 |
| style | 是|String | 请假类型,病假/事假 |
| date|

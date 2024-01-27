# 用户基本信息

> <https://gateway.acgo.cn/acgoAccount/openapi/user/detail>

*请求方式：GET*

**url参数：**

| 参数名 | 类型 | 内容        | 必要性  | 备注         |
| ------ | ---- | ---------- | ------ | ------------ |
| uid    | num  | 目标用户uid | 必要   |              |

**json回复：**

根对象：

| 字段      | 类型 | 内容     | 备注                                                          |
| --------- | ---- | -------- | ------------------------------------------------------------ |
| code      | num  | 返回值   | 0：成功<br />500：用户不存在（如注销账号）                      |
| message   | str  | 错误信息 | 默认为success                                                 |
| data      |  obj  | 信息本体 |                                                              |
| timestamp | num | 当前的Unix时间戳 |                                                        |

`data`对象：

| 字段             | 类型 | 内容              | 备注                                                         |
| ---------------- | ---- | ---------------- | ------------------------------------------------------------ |
| uid              | num  | uid              |                                                              |
| blockStatus      | num  | 未知             | 默认为1                                                       |
| nickName         | str  | 昵称             |                                                               |
| avata            | str  | 头像链接         | 若未设置则是https://attach.acgo.cn/picture/default.png         |
| sex              | num  | 性别             | 0：未知<br />1：男<br />2：女                                  |
| birthday         | num  | 生日             | 0：未知<br />若有则是生日的Unix时间戳                           |
| registerTime     | num  | 注册时间         | Unix时间戳                                                     |
| school           | 未知  | 学校（?）        | null：未知<br />暂未发现有`school`字段的用户                    |
| city             | 未知  | 城市（?）        |  null：未知<br />暂未发现有`city`字段的用户                     |
| autograph        | str  | 个性签名         | 若未设置则是love acgo                                           |
| followNumber     | num  | 关注人数         |                                                               |
| fanNumber        | num  | 粉丝人数         |                                                               |
| registerTime     | num  | 注册时间         | Unix时间戳                                                     |
| honorary         | ？   | 荣誉（？）        | 未知                                                          |
| rankId           | ？   | 未知             | 未知                                                           |
| userRankVo       | obj  | 排名信息         |                                                                |
| isCreateTeam     | bool | 是否创建团队      | true：已创建<br />false：未创建<br />默认为false                |


`data`中的`userRankVo`对象：

| 字段             | 类型  | 内容             | 备注                                                          |
| ---------------- | ---- | ---------------- | ------------------------------------------------------------  |
| userRankScore    | num  | 用户排名分数      | 可通过竞赛获得（？）                                            |
| honorary         | str  | 荣誉             | 默认为 倔强青铜                                                 |
| rankRing         | num  | 用户排名         | 用户排名，若为200则不计入排名                                    |
| rankId           | num  | 排名id           | 默认为1                                                        |


**示例：**
查询用户`uid=1`的详细信息
```shell
curl -G 'https://gateway.acgo.cn/acgoAccount/openapi/user/detail' \
	--data-urlencode 'uid=1'
```

<details>
<summary>查看响应示例：</summary>
  
```json
{
    "code": 200,
    "message": "success",
    "data": {
        "uid": 1,
        "blockStatus": 1,
        "nickName": "130****6960",
        "avatar": "https://attach.acgo.cn/picture/default.png",
        "sex": 0,
        "birthday": 0,
        "registerTime": 1687846398,
        "school": null,
        "city": null,
        "autograph": "love acgo",
        "followNumber": 0,
        "fanNumber": 1,
        "followStatus": 4,
        "userRankScore": 0,
        "honorary": null,
        "rankRing": null,
        "rankId": null,
        "userRankVo": {
            "userRankScore": null,
            "honorary": "倔强青铜",
            "rankRing": null,
            "rankId": 1
        },
        "isCreateTeam": false
    },
    "timestamp": 1706385645
}
```

</details>

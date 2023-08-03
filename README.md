#  vxarticle_spider
微信公众号文章采集
采集目标：
微信公众号文章的阅读数、在看数、评论数、评论列表，还有微信公众号的账号基本信息。
# 微信视频号采集
## 1.采集视频地址 
## 2.用户主页数据   
## 3 视频评论数据

采集难点： 采集以上数据需要客户端的一些参数，比如 x-wechat-key 、 __biz 、appmsg_token 、pass_ticket等。
#### 服务地址 联系qq:   1095087360



##### 一、获取微信公众号历史数据（可采全）

* Post:/wxapi/get_page

| 名称  | 类型   | 含义                                   |
| ----- | ------ | -------------------------------------- |
| biz   | String | 微信唯一用户标识                       |
| page  | int    | 页数从0起 ，每次还回10组公众号发文数据 |
| token | String | 用户标识                               |

* 返回：

```json
 {
    "code": 0,
    "msg": "ok",
    "list": [
        {
            "title": "好消息 ！我市再添1个自治区级服务业集聚区",
            "time_str": "2022-08-04 21:19:10",
            "time": 1659619150,
            "nick_name": "石嘴山发布",
            "url": "https://mp.weixin.qq.com/s?__biz=MzUzMTg1NDY2Ng==&mid=2247565667&idx=1&sn=61d0fa012ef21d760505338cd8313b87&chksm=fabfa546cdc82c505d67595f90f3737e8dd5276f315352a8f5b7a8ef4aaa45e60a463d18eda6&scene=58&subscene=0#rd"
        }, 
        ...
        {
            "title": "@学生，居家安全知识来了 | 暑期安全课",
            "time_str": "2022-07-23 17:22:47",
            "time": 1658568167,
            "nick_name": "石嘴山发布",
            "url": "https://mp.weixin.qq.com/s?__biz=MzUzMTg1NDY2Ng==&mid=2247564451&idx=2&sn=11153758fb24ba05a4efdafc1e936da4&chksm=fabf9886cdc811906d2380a6bbab8b1b175647d807ebf50c1b93d1a81da7a07021adb1791086&scene=58&subscene=0#rd"
        }
    ]
}
```

##### 二、获取阅读点赞再看数(评论数获取)

* Post:/wxapi/readnum  
* 请求参数:   

| 名称  | 类型   | 含义     |
| ----- | ------ | -------- |
| url   | String | 地址     |
| token | String | 用户标识 |

* 返回：

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "readnum": 100001, //阅读
        "likenum": 5124,  //点赞
        "oldlikenum": 2748, //再看
        "biz": "MzI5ODE4Nzk3Mw=="
    }
}
```

##### 三、获取评论数据

* Post:/wxapi/wxcoment

* 请求参数: 

  | 名称  | 类型   | 含义     |
  | ----- | ------ | -------- |
  | url   | String | 地址     |
  | token | String | 用户标识 |

  

* 返回：

```json
{
    "code": 0,
    "msg": "ok",
    "data": [
        {
            "id":  3,
            "my_id": 15481,
            "nick_name": "杨正文",
            "logo_url": "http://mmsns.qpic.cn/mmsns/iaxNB5XaibCeLTYWIUGCYm7cS1kFxTx4ibUSEBZJ6VnOdXPDItJ9PaGRg/0",
            "content": "可喜可贺，长沙十三家进入世界品牌五佰强！👍 ",
            "create_time": 1659940713,
            "content_id": "3375202195590503545",
            "like_id": 0,
            "like_num": 7,
            "like_status": 0,
            "is_from_friend": 0,
            "is_from_me": 0,
            "is_top": 0,
            "reply_new": {
                "reply_list": [],
                "max_reply_id": 1,
                "reply_total_cnt": 0
            },
            "ip_wording": {
                "country_name": "中国",
                "country_id": "156",
                "province_name": "湖南",
                "province_id": "",
                "city_name": "",
                "city_id": ""
            },
            "segment": {
                "start_offset": 0,
                "end_offset": 0
            }
        },
        {
            "id": 1,
            "my_id": 918,
            "nick_name": "时光如金",
            "logo_url": "http://mmsns.qpic.cn/mmsns/iaxNB5XaibCeLTYWIUGCYm7cS1kFxTx4ibUSEBZJ6VnOdXPDItJ9PaGRg/0",
            "content": "长沙加油",
            "create_time": 1659940193,
            "content_id": "4931301107466349462",
            "like_id": 0,
            "like_num": 2,
            "like_status": 0,
            "is_from_friend": 0,
            "is_from_me": 0,
            "is_top": 0,
            "reply_new": {
                "reply_list": [],
                "max_reply_id": 1,
                "reply_total_cnt": 0
            },
            "ip_wording": {
                "country_name": "中国",
                "country_id": "156",
                "province_name": "湖南",
                "province_id": "",
                "city_name": "",
                "city_id": ""
            },
            "segment": {
                "start_offset": 0,
                "end_offset": 0
            }
        }
    ]
}
```

##### 四、搜狗转永久链接

* Post:/wxapi/tmp2forever

* 请求参数: 

  | 名称      | 类型   | 含义     |
  | --------- | ------ | -------- |
  | sogou-url | String | 地址     |
  | token     | String | 用户标识 |

  

* 返回：

```json
{
    "code": 0,
    "msg": "ok",
    "data": {
        "sogou_url": "https://mp.weixin.qq.com/s?src=11&timestamp=1657699201&ver=3917&signature=GMjzziSigdLf19dLcNgJz6fikNR3pk5sHYAKCsv5BIJDqPZu8eW6lFIp5XoUNEWDdlysD7NULuqBitG8nNzpO9yl89lUxpD6suod9zJHK6E9gNDM1SR57RxSdcHNTyWM&new=1",  
        "weixin_url": "http://mp.weixin.qq.com/s?__biz=MjM5NzI1MTY0MQ==&mid=2654933236&idx=1&sn=8f81afaf1f954bbbef6bbab962cdaef3&scene=0#wechat_redirect"
    }
}
```

##### 五、关键词搜索（搜狗微信近一天）

* Post:/wxapi/sogou_search

* 请求参数:   

  | 名称     | 类型   | 含义                    |
  | -------- | ------ | ----------------------- |
  | keywords | String | 关键词                  |
  | token    | String | 用户标识                |
  | page     | int    | 页数                    |
  | type     | String | 类型 （近一天，近一周） |

  

* 返回：

```json
{
    "code": 0,
    "msg": "ok",
    "list": [
        {
            "title": "北京二级造价师考试调整为10月16日举行",
            "time_str": "2022-08-09 09:17:29",
            "time": 1660007849,
            "nick_name": "北京永乐教育",
            "url": "https://weixin.sogou.com/link?url=dn9a_-gY295K0Rci_xozVXfdMkSQTLW6cwJThYulHEtVjXrGTiVgS4gGbFyTkWFiSnmBF04ovaUrm48PZ4FKI1qXa8Fplpd90VjZ3NC3iCW9667DVwNv8QPKlPVval3QRSTbtAZmbQh28YK1qPAqkZbSV3d0Etjbd0ZVYq1Tx1lO4qCybObheniVj7ooASwqCpiir-e1rq7Teb5IU2YbHO2MHN-OsDG4-QCDWMcALpDDMYG5qKs7HmLJyhujKqEHBAN_o3tsiz5r1dbZWbKUeQ..&type=2&query=%E5%8C%97%E4%BA%AC&token=null"
        },
        ...
        {
            "title": "北京快招聘为您推荐优选职位 | 08月第09期",
            "time_str": "2022-08-09 09:20:52",
            "time": 1660008052,
            "nick_name": "北京快招聘",
            "url": "https://weixin.sogou.com/link?url=dn9a_-gY295K0Rci_xozVXfdMkSQTLW6cwJThYulHEtVjXrGTiVgS4gGbFyTkWFiSnmBF04ovaUrm48PZ4FKI1qXa8Fplpd9eJlWvu9i1rMbKvZFVZbUyMnwqEeVYQjAZXR2DEkzJX0owq6_QFbtXjaPl7uc6TYlDJIv3g6YxvIx1V5DG8iIcGjc2hK1BquOTZ3tX_Ijg3PkOJCuFpCrUIXEWDRdLD91Rvqy-0Nogf03u34cxwWFuIrApMU0qNvfET-cbm7TDDICYioxHkzTmA..&type=2&query=%E5%8C%97%E4%BA%AC&token=null"
        }
    ]
}
```


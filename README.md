1. [登录获取token](https://github.com/wtgg/ghxc_doc/blob/main/1.登录获取token.md)
2. [~~验证社交网络人物账号~~](https://github.com/wtgg/ghxc_doc/blob/main/2.验证社交网络人物账号.md)
3. [新增任务 GET](https://github.com/wtgg/ghxc_doc/blob/main/3.新增任务GET.md)
3. [新增任务 POST](https://github.com/wtgg/ghxc_doc/blob/main/3.新增任务POST.md)
4. [修改任务](https://github.com/wtgg/ghxc_doc/blob/main/4.修改任务.md)
5. ~~新增执行 je_id~~
6. [切换任务状态：正在运行/暂停](https://github.com/wtgg/ghxc_doc/blob/main/6.切换任务状态.md)
7. [终止正在运行的爬虫](https://github.com/wtgg/ghxc_doc/blob/main/7.终止正在运行的爬虫.md)
8. [新增信息源](https://github.com/wtgg/ghxc_doc/blob/main/8.新增信息源.md)
9. 数据示例及说明
    [1.任务信息](####1.任务信息)
    [2.任务执行信息](####2.任务执行信息)
    [3.视频信息](####3.视频信息)


### RabbitMQ
#### 1.任务信息
> queue:`job_instance`
###### 1.1新增数据示例
```json
{
  "id": "1440",  // 本条数据在zdk采集系统中任务表的主键id
  "act": "c",  // 数据操作类型
  "act_desc": "增",  
  "db": "cs_cp",
  "table": "job_instance",
  "for_test": 1,
  "event_type": 1,
  "row_data": {
    "id": "1440",
    "date_created": "2021-02-02 14:10:53",
    "date_modified": "2021-02-02 14:10:53",
    "job_name": "测试666",  // 任务名称
    "data_type": "视频数据",  // 采集数据类型，可设死
    "spider_type": "关键词采集",  // 采集形式，可设死
    "keywords": "[\"小米\", \"华为\"]",  
    "site_name": "bilibili.com",  // 源网站名称
    "spider_name": "bili",  // 爬虫名称
    "start_date": "2021-02-02",  // 任务运行的开始时间
    "end_date": "2222-02-02",  // 当日期为2222-02-02时表示结束时间无限久远
    "how_often": "隔天采集",
    "sleep_days": "1", // 间隔天数
    "frequency": "",
    "excute_hours": "[\"不指定\"]",  // 可设死
    "resolution": "480P",
    "else_prefer": "最高分辨率",
    "video_all_info": "[\"5-10\"]",
    "info_except_video": "[\"<5\", \">10\"]",
    "upload_time_type": "任务运行周期内最新",
    "upload_time_start_date": "2021-02-02",
    "upload_time_end_date": "2222-02-02",
    "run_type": "长期",
    "enabled": "0",
    "pri": "常规",
    "is_deleted": "0",  // 本条数据是否被隐藏
    "finish_reason": "",
    "source_ids": "[14]"  // 信息源id
  }
}
```

###### 1.2修改数据示例：
```json
{
  "id": "61630",
  "act": "u",
  "act_desc": "改",
  "db": "cs_cp",
  "table": "videoitems",
  "for_test": 1,
  "event_type": 2,
  "row_data": {
    "id": "61630",
    "video_time": "212.76666",
    "status": "2",
    "download_finished": "2021-02-02 11:51:57",
    "fps": "30",
    "frame_counter": "6383",
    "width": "1920",
    "height": "1080"
  },
  "related_data": {
    "job_execution_id": 20038,
    "job_instance_id": 1437
  }
}

```


#### 2.任务执行信息
> queue:`job_execution`
###### 2.1新增数据示例：
```json

{
  "id": "20047", // 本条数据在zdk采集系统中执行表的主键id
  "act": "c",  // 数据操作类型
  "act_desc": "增",
  "db": "cs_cp",
  "table": "job_execution",
  "for_test": 1,  // 测试数据
  "event_type": 1,
  "row_data": {   // 数据内容
    "id": "20047",
    "date_created": "2021-02-02 14:07:43",  // 本条数据生成时间
    "date_modified": "2021-02-02 14:07:43",  // 本条数据最近被修改的时间
    "job_instance_id": "1436",  // 本条数据对应的 zdk采集系统中执行表的主键id
    "spider_name": "bili",  // 爬虫名字
    "keywords": "英雄联盟",  // 此次爬虫采集的目标关键词
    "start_time": "2021-02-02 14:07:44",  // 此次爬虫的启动时间
    "end_time": "",  // 此次爬虫的结束时间
    "running_status": "0",  // 此次爬虫的运行状态： 0即将运行, 1正在运行，2已完成, 3被中止
    "finish_reason": "",  // 此次爬虫完成原因
    "succeed": "1",  // 此次爬虫启动是否成功
    "error_msg": "",  // 此次爬虫报错信息
    "source_id": "",
    "retry": "0"  // 此次爬虫重试次数，默认为0，每重试1次+1，最多重试2次
  },
  "related_data": {
    "job_instance_id": 1437
  }
}

```
###### 2.2修改数据示例：
```json
{
  "id": "20047",
  "act": "u",
  "act_desc": "改",
  "db": "cs_cp",
  "table": "job_execution",
  "for_test": 1,
  "event_type": 2,
  "row_data": {
    "id": "20047",
    "date_modified": "2021-02-02 14:07:48",
    "start_time": "2021-02-02 14:07:42",
    "running_status": "1"
  },
  "related_data": {
    "job_instance_id": 1437
  }
}

```

#### 3.视频信息
> queue:`videoitems`
###### 3.1新增数据示例：

```json

{
  "id": "61873",  // 本条数据在zdk采集系统中视频表的主键id
  "act": "c",
  "act_desc": "增",
  "db": "cs_cp",
  "table": "videoitems",
  "for_test": 1,
  "event_type": 1,
  "related_data": {  // 本条视频数据对应的执行和任务id
    "job_execution_id": 20047,  // 对应的执行id
    "job_instance_id": 1436  // 对应的任务id
  },
  "row_data": {  // 本条视频数据
    "id": "61873",
    "title": "【伽耳】爆杀流恶魔小丑对阵明凯打野",
    "title_cn": "【伽耳】爆杀流恶魔小丑对阵明凯打野",
    "url": "http://www.bilibili.com/video/av756452546",  // 视频url
    "keywords": "英雄联盟",
    "tags": "LOL,英雄联盟,小丑,电子竞技,萨科,恶魔小丑,打卡挑战,游戏练级挑战,我的游戏假期,游戏知识分享官",  // 视频标签
    "video_category": "电子竞技",  // 视频分类
    "upload_time": "2021-02-02 14:03:41",  // 视频发布时间
    "spider_time": "2021-02-02 14:07:48",  // 视频被采集时间
    "info": "B站直播：伽耳   欢迎大家前来关注~\n兄弟们可以一起探讨小丑的各种玩法 请多多指教~\n如有不足 还望海涵",  // 视频简介
    "site_name": "bilibili.com",  // 视频来源网站
    "video_time": "1065.0",    // 视频时长，单位秒，float类型
    "status": "0",  // 视频状态： 0初始值,已获取,待服务器下载;1服务器正在下载;2服务器下载完成;3上传到服务器hdfs完成;4前面的过程报错;31客户端正在同步;32客户端同步完成;34客户端同步出错
    "play_count": "0",  // 播放次数
    "lg": "简体中文",  // 语种
    "is_delete": "0", // 本条数据是否被隐藏
    "download_start": "",  // 本条数据在服务器开始下载的时间
    "download_finished": "", // 本条数据在服务器下载完成的时间
    "download_time": "",  // 本条数据上传到服务器hdfs的时间
    "delete_time": "",  // 本条数据被删除的时间
    "sync_start_time": "",  // 本条数据被同步开始的时间
    "sync_finish_time": "", // 本条数据被同步完毕的时间
    "size": "",  // 视频大小，单位bytes
    "channel_id": "",  // 视频发布者的频道id
    "owner": "伽耳小丑",  // 视频发布者
    "author": "伽耳小丑",  // 视频发布者
    "avatar_url": "",  // 视频发布者头像url
    "subscribed_num": "",  // 视频发布者被订阅量
    "error_msg": "",  // 视频在服务器被下载过程中的报错信息
    "comments_count": "",  // 视频评论数
    "comments": "",  // 视频评论
    "like_count": "",  // 视频点赞数
    "dislike_count": "",  // 点踩数
    "sync_error": "",  // 同步过程中的报错信息
    "push_into_dq": "1",  // 视频是否默认被下载
    "resolution": "",  // 视频分辨率
    "deleter": "",  // 视频被生产者：1被用户自己删除，2被同步工具删除，3被磁盘清理删除
    "fps": "",  // 帧率
    "frame_counter": "",  // 总帧数
    "width": "",  // 分辨率-宽度
    "height": ""  // 分辨率-高度
  }
}

```
###### 3.2修改数据示例：
```json
{
  "id": "61653",
  "act": "u",
  "act_desc": "改",
  "db": "cs_cp",
  "table": "videoitems",
  "for_test": 1,
  "event_type": 2,
  "row_data": {
    "id": "61653",
    "status": "3",
    "download_time": "2021-02-02 12:01:04",  // 视频被上传到服务器hdfs的时间
    "size": "112264648"
  },
  "related_data": {
    "job_execution_id": 20039,
    "job_instance_id": 1437
  }
}

```


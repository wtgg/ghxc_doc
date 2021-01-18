1. [登录获取token](https://github.com/wtgg/ghxc_doc/blob/main/1.登录获取token.md)
2. [验证社交网络人物账号](https://github.com/wtgg/ghxc_doc/blob/main/2.验证社交网络人物账号.md)
3. [新增任务 GET](https://github.com/wtgg/ghxc_doc/blob/main/3.新增任务 GET.md)
3. [新增任务 POST](https://github.com/wtgg/ghxc_doc/blob/main/3.新增任务 POST.md)
4. 修改任务 task_id
5. 新增执行 je_id
6. 切换任务状态：正在运行/暂停
7. 终止正在运行的爬虫
8. 新增信息源


### kafka
1. 任务信息，topic:`job_instance`

|参数名|必需|类型|说明|
|:----    |:---|:----- |-----   |
|act|  是  |string |数据操作，crud|
|task_id|  是  |string |任务id|
|site_name|  是  |string |网站名|
|enabled|  是  |string |任务状态：0，正在运行；-1，已暂停；1，已完成|

2. 任务执行信息，topic:`job_execution`

|参数名|必需|类型|说明|
|:----    |:---|:----- |-----   |
|act|  是  |string |数据操作，crud|
|unid|  是  |string |国恒信创id|
|id|  是  |string |任务执行id|
|job_instance_id|  是  |string |任务id|
|site_name|  是  |string |网站名|
|succeed|  是  |int |爬虫是否执行成功|
|running_status|  是  |int |爬虫执行状态：0即将运行, 1正在运行，2已完成, 3被中止|
|start_time|  是  |string |爬虫开始时间，形如`2021-01-14 03:00:19`|
|end_time|  否  |string |爬虫结束时间，形如`2021-01-14 03:01:25`|
|finish_reason|  否  |string |爬虫结束原因|


3. 视频信息，topic:`videoitems`

|参数名|必需|类型|说明|
|:----    |:---|:----- |-----   |
|act|  是  |string |数据操作，crud|
|id|  是  |string |视频表id|
|je_id|  是  |string |任务执行表id|
|task_id|  是  |string |任务表id|
|title|  否  |string |视频标题|
|url|  是  |string |视频标题|
|tags|  否  |string |视频标签|
|video_category|  否  |string |视频类型|
|upload_time|  否  |string |发布时间|
|spider_time|  否  |string |采集时间|
|info|  否  |string |简介|
|site_name|  否  |string |来源网站|
|video_time|  否  |float |视频时长|
|status|  是  |int |视频状态：0初始值,已获取,待下载;1正在下载;2下载完成;3上传完成;4前面的过程报错;31正在同步;32同步完成;34同步出错|
|play_count|  否  |string |播放次数|
|lg|  否  |string |语种|
|is_delete|  否  |int |是否被删除|
|download_time|  否  |string |视频上传到hdfs上的时间|
|download_start|  否  |string |视频在服务器开始下载的时间|
|download_finished|  否  |string |视频在服务器下载完成的时间|
|delete_time|  否  |string |视频被删除的时间|
|sync_start_time|  否  |string |视频被同步的开始时间|
|sync_finish_time|  否  |string |视频被同步的结束时间|
|size|  否  |string |视频大小，单位byte|
|author|  否  |string |视频发布者|
|avatar_url|  否  |string |视频发布者头像|
|error_msg|  否  |string |下载和上传过程中的报错|
|comments_count|  否  |string |评论数量|
|comments|  否  |string |评论|
|like_count|  否  |int |点赞数|
|dislike_count|  否  |int |点踩数|
|sync_error|  否  |int |同步过程中的报错|
|deleter|  否  |int |视频被谁删除：1用户自己，2同步工具，3磁盘清理|
|fps|  否  |int |视频帧率|
|frame_counter|  否  |int |总帧数|
|width|  否  |int |分辨率-宽度|
|height|  否  |int |分辨率-高度|


4. 社交网络帖子信息，topic:`social_network_posts`

|参数名|必需|类型|说明|
|:----    |:---|:----- |-----   |
|act|  是  |string |数据操作，crud|
|id|  是  |string |社交网络帖子表id|
|je_id|  是  |string |任务执行表id|
|task_id|  是  |string |任务表id|
|spider_time|  否  |string |采集时间|
|post_id|  否  |string |帖子在来源网站的id|
|site_name|  是  |string |帖子来源网站|
|post_url|  否  |string |帖子在来源网站的url|
|post_datetime|  否  |string |帖子发布时间|
|post_content|  否  |string |帖子内容|
|comments_count|  否  |string |帖子评论数|
|share_count|  否  |string |帖子被分享数|
|is_transmitted|  否  |string |帖子是否是转发别人的|
|like_count|  否  |string |点赞数|
|imgs|  否  |string |图片|
|video_url|  否  |string |包含的视频|


5. 社交网络帖子评论，topic:`social_network_post_comments`

|参数名|必需|类型|说明|
|:----    |:---|:----- |-----   |
|act|  是  |string |数据操作，crud|
|id|  是  |string |社交网络帖子评论表id|
|je_id|  是  |string |任务执行表id|
|task_id|  是  |string |任务表id|
|spider_time|  否  |string |采集时间|
|post_id|  否  |string |帖子在来源网站的id|
|site_name|  是  |string |帖子来源网站|
|at_name|  否  |string |评论者@账号名称|
|user_name|  否  |string |评论者昵称|
|comment_id|  否  |string |评论id|
|comment_time|  否  |string |评论发布的时间|
|content_text|  否  |string |帖子评论内容|

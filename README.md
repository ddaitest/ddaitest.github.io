#Protocol

[TOC]


##Action From Server

####getOffline
获取离线数据

####oneChat
获取私聊数据

####checkUser
监测用户是否合法

####checkOnLine
监测用户是否有其他客户端在线

####==sendMsgCb==
发送消息成功回调

| 参数 | 说明 |备注|
|--------|--------|--------|
|msg_id		|发送方数据id||
|msg_status	|发送状态 1成功,0失败||
|chat_id		|消息ID||
|err_msg		|失败原因，成功为空字符串|||


####==CheckNewMsg==
检查是否有消息数据

| 参数 | 说明 |备注|
|--------|--------|--------|
|flag		|1有新消息0无新消息|||

####==getNewMsg==
获取新消息数据

| 参数 | 说明 |备注|
|--------|--------|--------|
|flag|1:有消息, list数组为消息数据; 0:list为空数组||
|total|符合条件的数据总量||
|list|消息数据列表||
|chat_id|消息ID(可以以此去重)||
|user_id|发送人id||
|target_id|接收人id||
|user_name|发送人姓名||
|user_logo|发送人头像路径||
|send_time|发送消息的时间（服务器时间，时间戳，毫秒）||
|msg_content|消息内容（对应msg_type，文字对应文字内容，声音对应声音url，图片对应图片url）||
|msg_type|消息类型（1文字，2声音，3图片）||
|voice_length|	声音长度（消息类型为声音时对应的声音长度）|||


##Action From Client
####updateUserList
更新用户列表（客户端和服务器端建立连接后，先从API获取用户关系列表，然后调用此事件更新服务器端的用户信息。每次打开APP也需要调用此事件更新用户信息，保证用户信息的同步。）

####login
用户上线

####sendChat
发送私聊信息

####requestOffline
请求离线数据

####logout
用户退出登录

####==sendMsg==
发送私聊信息

| 参数 | 说明 |备注 |
|--------|--------|--------|
|msg_id|客户端消息ID标示，为了实现成功回调(sendMsgCb)中的对应关系||
|user_id|发送人id||
|target_id|接收人id||
|user_name|发送人姓名||
|user_logo|发送人头像路径||
|msg_content|消息内容（对应msg_type，文字对应文字内容，声音对应声音url，图片对应图片url）||
|msg_type|消息类型（1文字，2声音，3图片）||
|voice_length|	声音长度（消息类型为声音时对应的声音长度）|||



####==requestMsg==
请求消息数据

| 参数 | 说明 |备注|
|--------|--------|--------|
|user_id|||
|start_offset|开始时间戳 (为0则为服务器当前时间)||
|end_offset|结束时间戳 (为0则为服务器当前时间)||
|limit||||

_ _ _

##Usage
####Connect

- - -

####Client Send Message
Client 发送 `sendMsg`。
等收到 `sendMsgCb` 后，认为消息发送成功。

- - -

####Client Receive Message
当 Client 收到 `CheckNewMsg` 。
发送 `requestMsg` 。
等待接受 `getNewMsg` 。

- - -

####Disconnect

- - -


Fixed Issues List

|B/C端	|问题描述|
|--------|--------|
|B/C端	|修改图片加载中的“默认图片”|
|B/C端	|优化部分Layout，注意点击响应范围|
|B/C端	|整理Toast, Dialog|
|B/C端	|录制语音结束时机不正确，回放有被截取现象|
|B端		|录音播放过程中退出当前界面，录音还在播放|
|B/C端	|聊天界面发送完图片，聊天区域不自动刷新，需要手动上滑|
|B/C端	|通知栏的icon图标不正确，来消息时的图标|
|C端		|替换图片缓存|
|B/C端	|施工现场查看图片比原图要小，且图片无法缩放操作||

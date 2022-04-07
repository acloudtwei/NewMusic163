# 网易云音乐自动任务(最新cookie版)

# 重点说明❗

目前网易云很多人的音乐人已经被封了，我的音乐人今天也发现安全问题直接封掉音乐人。注意只是封音乐人，意思是你的账号还是能用，兑换的黑胶会员也还在，只是你的
网易音乐人标识取消了，而且申述几率很低。所以建议大家可以用这个脚本刷听歌数以及云贝，音乐人的任务建议不要搞了，不然可能会封掉音乐人！
大家注意下❗❗❗


## 说明

其实这个修改版呢是因为昨天开始网易云音乐在登录的时候加了一个验证，也就是要点击图片要求的字母才可以登录成功。之前都是没有的，
然后今天我就发现我登录失败，无法刷云豆那些。然后我去三楼看了下大家也是不可以，虽然有些人说用cookie可以，但是我用他们的源码搭建
之后发现无法搭建，直接说缺少什么东西，然后我就不管了，直接看我之前用的那个源码，去分析下怎么获取cookie登录的，然后改了改源码，
就可以直接通过将cookie输入登录进去，就无需之前麻烦的登录获取cookie那些。<br/><br/>
目前我发现我电脑上的`cookie有效期`是15天，你们应该也是。也就是说15天之后这个cookie才会失效。也算挺长的吧。
我用的这个源码我也不知道是几百年前的了，和大家用的不太一样，与目前最火的那个源码相比少了一两个任务，但是问题不大，可以保证能运行使用！！！


## 功能

1. 签到领云贝
2. 自动完成云贝任务，并领取云贝
3. 打卡升级
4. 刷指定歌曲的播放量
5. 音乐人自动签到领取云豆
6. 音乐人自动完成任务，并领取云豆
7. 自动领取 vip 成长值
8. 多种推送方式
9. 只支持[腾讯云函数](#一部署到腾讯云函数) 

> 开发不易，如果你觉得本项目对你有用，可以点个 star⭐!

## 注意事项

- 提 issue 之前看看是否有重复的 issue。
- 不要直接在 GitHub 上修改配置文件。已经修改了的，尽快覆盖，并修改密码。
- 转载请注明出处，并保留原作者信息。
- 禁止将代码用于商业用途，包括打包售卖，收费代挂等。
- 为了账号安全考虑，请勿将cookie交给他人代挂。

## 一、部署到腾讯云函数

### 开通服务

首次使用云函数，依次登录 [SCF 云函数控制台](https://console.cloud.tencent.com/scf) 和 [SLS 控制台](https://console.cloud.tencent.com/sls) 开通相关服务，确保账户下已开通服务并创建相应[服务角色](https://console.cloud.tencent.com/cam/role) **SCF_QcsRole、SLS_QcsRole**

### 下载源码

可以通过蓝奏云网盘下载或者直接在github下载

### 创建云函数

1.`点击新建即可`
![Layer](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/1.jpg)


2.选择从头开始，函数名称可以自己决定，运行环境选择`Python3.6`，记住不能选择 `Python3.7`，因为 `Python 3.7` 及之后版本，云函数平台不再额外内置依赖库，提交方法选择本地上传zip文件。
![Function](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/2.jpg)


3.将从蓝奏云下载的源码或从github clone下来的源码直接上传即可，无需修改任何东西！
![Bind](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/3.jpg)


4.继续下拉，点击高级配置，将执行超时时间修改为 900秒。内存默认是 128MB，可以不改，也可改为 64MB！
![Bind](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/4.jpg)


5.在[函数服务](https://console.cloud.tencent.com/scf/list)点进刚刚创建的函数
![Function](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/5.jpg)

6.点击触发管理，再点击创建触发器
![Function](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/6.jpg)


7.`配置如下` 时间和名称那些可以自行配置！

第一个触发器定时任务名称可以使用默认名称，触发周期选择自定义触发周期，Cron表达式填写触发时间，比如 0 30 0 * * * *表示每天 0 点 30 分自动运行！
![Function](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/7.jpg)
![Function](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/8.jpg)


8.在编辑器里点击 `config.json` 这个文件进行配置
![Config](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/9.jpg)


9.可以看到文件中有红色波浪线的错误提示，可以忽略不管，也可以下拉到编辑器的右下角，点击 `JSON` 来更改语言模式，选择 `JSON with Comments`，这样就可以消除错误提示。
![Style](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/10.jpg)
![Style](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/11.jpg)
![Style](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/12.jpg)
![Style](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/13.jpg)


10.在 `config.json` 里填写cookie。运行之后如果发现有些任务没有完成，可能是因为没有开启，将任务对应的 `enable` 字段设置为 `true` 即可开启。
![Style](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/14.jpg)
![Style](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/15.jpg)


11.修改完毕后，点击部署，看到部署成功后点击测试进行测试。
![Test](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/16.jpg)

12.运行成功，可以看到日志是有对应信息输入的，`完美`！
![Success](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/17.jpg)


### 浏览器抓cookie

浏览器抓cookie，我这里演示的是电脑上怎么抓，手机的话需要一些特别的浏览器，比如Alook、X浏览器等等
我会演示`谷歌浏览器`以及`火狐浏览器`怎么抓，挺简单的！

**首先是**使用火狐浏览器抓cookie

需要在网易云音乐输入账号密码登录，然后按一下键盘上的`F12`，选择`存储`，点击`Cookie`，找到域名是`music.163.com`
![Firefox](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/18.jpg)

然后就是直接点击登录，你会发现Cookie这里会有一大堆数据出来，然后我们要找到名称为：`MUSIC_U`的值，这个值就是cookie
![Firefox](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/19.jpg)

**其次是**使用谷歌浏览器抓cookie

这个和火狐其实是一样的道理，也是先按`F12`，然后`登录`，找到`应`用，选择`Cookie`，找到域名是`music.163.com`，然后复制`MUSIC_U`的值即可
![Chrome](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/20.jpg)


<br>
***

经过了上面的步骤，你就可以在腾讯云函数那里部署这个网易云自动任务脚本了！

***

## 二、本地运行

### 下载

拉取代码

```shell
git clone https://github.com/acloudtwei/NewMusic163.git
```

### 安装依赖

切换到项目目录

```shell
cd NewMusic163
```

然后安装依赖

```shell
pip install -r requirements.txt
```

### 修改配置文件

直接修改 `config.json` 文件

### 运行

```shell
python3 index.py
```

### 更新代码

在当前项目目录下打开终端，然后直接输入下面命令

```shell
git pull
```

#### 推送

支持多种推送方式，建议使用企业微信进行推送

1. 企业微信
2. [server 酱](https://sct.ftqq.com/)
3. 酷推
4. [pushPlus](https://www.pushplus.plus)

要使用推送的话将相应的 `enable` 设为 `true`，并填写配置

##### 企业微信

```
/* 企业微信推送 */
"WeCom": {
    /* 是否启用企业微信推送 */
    "enable": true,
    /* 企业ID，登录企业微信后在管理后台“我的企业”－“企业信息”下查看 */
    "corpid": "",
    /* 应用ID，在“应用管理”里，点进相应的应用可查看 */
    "agentid": "",
    /* 应用密钥，在“应用管理”里，点进相应的应用可查看 */
    "secret": "",
    /* 要推送的人的用户ID，每个成员都有唯一的userid，即所谓“帐号”。在管理后台->“通讯录”->点进某个成员的详情页，可以看到。默认为"@all"，向该企业应用的全部成员发送 */
    /* 若该企业应用有多个成员，请将id改为自己的id，如“ZhangSan”，以免其他成员也收到消息 */
    "userid": "@all",
    /* 消息类型：text 文本消息(微信、企业微信里均可查看) | textcard 文本卡片消息(微信、企业微信里均可查看) | markdown markdown消息(只能在企业微信里查看)  */
    "msgtype": "text"
},
```

注册企业微信账号可参考[这里](https://sct.ftqq.com/forward)

`corpid` 为企业 ID，登录企业微信后在管理后台`我的企业`－`企业信息`下查看；`agentid` 为应用 ID，在`应用管理`里，点进相应的应用可查看；`secret` 为应用密钥，在`应用管理`里，点进相应的应用可查看；`userid` 默认为`@all`，会向该企业应用的全部成员发送；`msgtype` 为消息类型，可填写文本消息 `text`、文本卡片消息 `textcard` 或 markdown 消息 `markdown`，markdown 消息不能在微信里查看，只能在企业微信里查看。

##### server 酱

```
/* server酱微信推送 */
"serverChan": {
    /* 是否启用server酱微信推送 */
    "enable": true,
    /* 填写server酱旧版SCKEY或新版SendKey */
    "KEY": ""
},
```

要使用 server 酱的话需要在 `KEY` 里填写旧版的 SCKEY 或新版的 SendKey。

##### 酷推

```
/* Cool Push酷推QQ推送 */
"CoolPush": {
    /* 是否启用酷推推送 */
    "enable": true,
    /* 推送方式，如果想要使用多种方式，请用逗号隔开，如["send","group"] */
    /* send:QQ号私人推送, group:QQ群推送, wx:微信推送, email:邮件推送 */
    "method": [
        "send"
    ],
    /* 酷推Skey */
    "Skey": ""
},
```

要使用酷推的话需要填写 `Skey`。

##### pushPlus 微信推送

```
/* pushPlus微信推送 */
"pushPlus": {
    /* 是否启用pushplus微信推送 */
    "enable": true,
    /* pushplus的token */
    "pushToken": "",
    /* 群组编码，为空时发给自己 */
    "topic": ""
},
```

要使用酷推的话需要填写 `pushToken`。

#### 打卡刷歌

```json5
"daka": {
    /* 是否开启任务 */
    "enable": true,
    /* 满级时自动停止 */
    "full_stop": true,
    /* 歌曲数 */
    "song_number": 500,
    /* 休眠时间 */
    "sleep_time": 10,
    "upload_num": 300
},
}
```
### 测试

修改完代码后，按 ctrl+s 保存代码，然后点击编辑器右上角的`部署`（每次修改完都要重新部署），左下角的`部署`也行。部署完成后点击部署旁边的测试按钮，观察结果，如果失败则检查修改代码。
（借用chen310一张图片）

![Test](https://cdn.jsdelivr.net/gh/chen310/NeteaseCloudMusicTasks/public/img/test.png)

[计费方式](https://cloud.tencent.com/document/product/628/39300)

## 其他

### 邀请码

Acloudtwei的网易云音乐人邀请码，一共10个，具体有啥用懂得都懂！`puuisoQ`
![邀请码](https://cdn.jsdelivr.net/gh/acloudtwei/CDN/NewMusic163/invite.jpg)


### 云函数免费额度及计费方式

在云函数[概览](https://console.cloud.tencent.com/scf/index)界面，可以查看本月剩余免费额度

详见[计费概述](https://cloud.tencent.com/document/product/583/17299)

### 声明

- 本仓库中的脚本仅用于测试和学习目的，请勿用于商业或非法目的，否则后果自负
- 转载请注明出处，并保留原作者信息。
- 如果您认为该项目的脚本可能涉嫌侵犯您的权利，请及时通知，我们将在确认后及时删除

### 感谢star⭐

### 灵感来源

1. [网易云音乐 API](https://github.com/Binaryify/NeteaseCloudMusicApi)
2. [NetEase-MusicBox](https://github.com/darknessomi/musicbox)
3. [NeteaseCloudMusicTasks](https://github.com/chen310/NeteaseCloudMusicTasks)

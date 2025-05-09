# docker-offline-images
从网盘下载各种容器离线镜像

## 为什么有这个仓库
自从国内大型dockerhub代理镜像下线之后，下载Docker镜像非常不方便  
需要经常去寻找代理服务，网站不稳定而且速度非常慢  
因此，我决定将各种镜像下载到本地，然后上传到网盘，方便后续下载。

## 此方案优缺点
缺点很明显
1. 下载镜像繁琐  
需要先登录网盘、转存到自己的网盘、下载到本地、上传到服务器、再导入到docker或者podman 。5个大步骤，很繁琐
2. 镜像大概率不是最新的  
镜像在我下载、上传好之后就不变了，无法使用`latest`

再说一下优点
1. 镜像下载快  
镜像直接从网盘下载，速度非常快，远远超过各种镜像代理网站的下载速度（腾讯云内网速度也很快，不过不是所有人服务器都在腾讯云）
2. 没有频率限制  
dockerhub对免费用户有频率限制，网盘没有

综合而言，如果镜像体积比较大，使用此方案所需时间可能有优势

## 镜像说明
镜像标准名称为： `registry/namespace/repository:tag`

其中
|字段|说明|是否必填|默认值|
| --- | --- | --- | --- |
| registry | 镜像仓库地址，如：`docker.io` | ❌ |`docker.io`|
| namespace | 镜像仓库名称，如：`library` | ❌ |`library`|
| repository | 镜像名称 | ✅ ||
| tag | 镜像标签 | ❌ |`latest`|

最简化场景下，只有一个镜像名称，如：`nginx`
```
docker pull nginx
```

## 目录说明

| 目录 | 说明 |
| --- | --- |
| 0_official | `docker.io`官方镜像,即 `docker.io/library` <br> `0`前缀是为了让文件夹排序到最前面 |
| 0_other_registry | 其它镜像仓库 |
| A | `registry`为`docker.io`，且`repository`首字母大写为A的镜像，如 `alpine` |
| B | `registry`为`docker.io`，且`repository`首字母大写为B的镜像，如 `bi` |
| ... | 规则同上 |

## 文件名-规则

## 网盘
网盘需求为：
1. 支持公开分享（排除阿里云盘）
2. 非会员下载不限速（排除百度云盘、夸克云盘）

目前选择的是 `123云盘`

## 网盘链接(具体列表可进入仓库子文件夹查看)
| 目录 | 说明 |网盘链接|
| --- | --- | --- |
| all | all |https://www.123865.com/s/ueQ8jv-uiyPh|
| 0_official | `docker.io`官方镜像 |https://www.123865.com/s/ueQ8jv-KiyPh|
| 0_other_registry | 其它镜像仓库 ||
| A | `docker.io`上`repository`以a开头的镜像 ||
| B | `docker.io`上`repository`以b开头的镜像 ||
| ... | 规则同上 ||


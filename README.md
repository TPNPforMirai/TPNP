# TPNP for Mirai Embedded

## Install

IMPORTANT: PLEASE UPGRADE YOUR PYTHON TO VERSION 3.8.0+ TO USE THIS BOT.

Change these values:
| File | Name | Value |
| :----: | :----: | :----: |
| Mirai_cqHttp/plugins/setting.yml | ********** | Bot QQ Number |
| TPNP/include/plugins/RSSHub/rss_trans.py | ***************** | BaiduTranslate API appid (optional) |
| TPNP/include/plugins/RSSHub/rss_trans.py | ^^^^^^^^^^^^^^^^^^^^ | BaiduTranslate API SecretKey (optional) |
| TPNP/config.py | ********** | Administrator's QQ Number |

Note: To use BaiduTranslate API, please go to TPNP/include/plugins/RSSHub/rsshub.py , remove the original translate block and replace them with the codes below.

Run `java -jar ./Mirai_cqHttp/cqhttp-mirai-0.2.2.4-embedded-all.jar` first in one screen process, and then go to ./TPNP folder and run `hypercorn run:app -b 0.0.0.0:8080` in another screen process.

Note: You can set properties in Mirai_cqHttp/config.txt to enable autologin.

## Usage from Quan666/ELF_RSS

### 添加订阅
添加订阅所有提到可选参数都只能从后面开始省略，不能设置在代理时省略更新频率的参数，设置第三方时省略更新频率、代理参数

向机器人发送

add mytwitter /twitter/user/Huagequan 123456,23445 -1 5 1 0

```
# 以下为注释

# add是添加订阅命令，若单独发送了add后，根据提示填写订阅信息即可，无需再加add

# mytwitt 为订阅名 因为要根据名字生成文件，所以不能有文件名不允许的特殊字符存在
# 不能命名为rss，会与配置文件冲突！！！

# /twitter/user/Huagequan 为订阅地址，此处为rsshub路由地址，非rsshub订阅源要写完整
# 如 https://myelf.club/index.php/feed/ 同时要设置第三方为1

# 123456,23445为订阅者qq号，逗号分开，-1表示设为空

# -1 为订阅群号，和qq号一样英文逗号分开，-1表示为空。
# qq号，群号两者必须有一个不为空，且有效，否则会出错。

# 5 为检查更新的频率，单位分钟/次，最小一分钟，还受到订阅源缓存影响 可选，默认为5

# 1 是否开启代理，有两种参数0/1 1开启，0关闭，设置此项为一必须设置好代理，此项可选，默认为0不开启

# 0 是否第三方订阅，即非rsshub订阅源时必须设为1  可选，默认为0关闭

# 0 翻译，Google翻译，效果一般  可选，默认为0关闭

# 0 仅输出标题，在正文较长的情况下建议启用  可选，默认为0关闭

# 可选参数建议添加订阅成功后通过change修改
```
机器人回复成功则添加成功。

### 查看订阅
向机器人发送 show_all 或showall、seeall 即可查看所有订阅

向机器人发送 show test 即可查看某一个订阅详细信息 test为订阅名或者订阅链接

### 删除订阅
向机器人发送 deldy test 即可删除某一个订阅 test为订阅名或者订阅链接

### 修改订阅
向机器人发送 change 即可查看修改方法

输入要修改的订阅的 

订阅名 修改项=,属性 

如:

test dyqq=,xx dsf=0

对应参数： 订阅地址-url，订阅QQ-dyqq，订阅群-dyqun，更新频率-uptime，代理-proxy，第三方-dsf，翻译-tl，仅title-ot

注：
代理、第三方、翻译、仅title属性值为1/0

qq、群号前加英文逗号表示追加

test为订阅名 也可直接在change后面加修改参数，也可单独修改某一个参数

### 短链接
发送 短链 https://myelf.club 即可获得短链接


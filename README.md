# CodemaoAutoRegister

**编程猫全自动发码/穷举验证码注册工具**

## 依赖

项目使用Python构建,依赖`requests`和`fake_useragent`库,请在开始使用前执行该命令(已经安装的可以忽略)

```bash
pip3 install requests
pip3 install fake-useragent
```

## 什么是CodemaoAutoRegister?

技术宅迟早毁了BCM,这是Wangs说的

某一天Wangs突发奇想,要不要狠狠地坑一把编程猫? 毕竟现在编程猫半死不活的,坑一把又不能找我来XD

所以Wangs打开了抓包软件,特别巧,包一抓就抓到了,然后Wangs又写了一个简简单单的Python程序重复发包,没想到猫站不仅没有人机验证(特别是发码要花钱的场景),还没有限制!令人忍俊不禁

Wangs知道之后非常开心,再大笑毛毡您连钱都不管了的同时顺便在Nemo小宇宙里大肆谈论,也不知道毛毡那边的看见没有~

互联网精神影响着Wangs,所以他就把自己的发现开源了,快说谢谢Wangs!()

## 在本地使用

1. 克隆并cd到仓库内
2. 执行以下指令

- 开始循环发码

```bash
python3 SendCaptca.py -w <间隔时间(单位秒)> -ru <随机UA(True/False)>
```

- 发一个码

```bash
python3 SendOneCaptca.py -p <手机号码>
```

## API

### 发码API

- API地址:`https://open-service.codemao.cn/captcha/rule/v3`
- 请求方式:POST
- 请求数据(均为必填):

|    键     |  类型  |             备注             |
| :-------: | :----: | :--------------------------: |
| deviceId  | string |         生成UUID即可         |
| identity  |  int   |           手机号码           |
|    pid    | string | 未知，默认填写`65edCTyg`即可 |
|   scene   |   ？   |        未知，默认为空        |
| timestamp | string |          请求时间戳          |

### 验证API

- API地址:`https://api.codemao.cn/tiger/v3/web/accounts/register/phone/with-agreement`
- 请求方式:POST
- 请求数据(均为必填):

|      键       |  类型  |             备注             |
| :-----------: | :----: | :--------------------------: |
| phone_number  |  int   |           手机号码           |
|   password    | string |             密码             |
|    captcha    | string |            验证码            |
| agreement_ids |  list  |        默认`[12,13]`         |
|      pid      | string | 未知，默认填写`65edCTyg`即可 |

## 免责声明

仅供学习交流使用!请在24H内删除,若侵犯了您的权益,请联系我QQ:1480357968

> "花开花落暗示着呼应着我，茫茫荒漠顷刻间春夏秋冬" 来自: 育空河 - 咩栗 https://music.163.com/song?id=2019299993
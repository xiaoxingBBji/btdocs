---
lang: zh-CN
title: 介绍
description: 简单介绍
---

::: tip 参与贡献
~~如果对与此文档有补充、改进意见或者修改，每个页面都可以直接点击末尾的`在 GitHub 上编辑此页`。~~

~~如果喜欢请为 <https://github.com/catlair/BiliOutils> 点个 star，关注才能不迷路。~~
:::

## 致谢

### 开发支持（~~暗杀名单~~）

提供 PR、代码 Issue 或者较为完整的逻辑建议。

- [vtroisWhite](https://github.com/vtroisWhite)
- [wdssfff00](https://github.com/wdssfff00)
- [iiwenwen](https://github.com/iiwenwen)
- [HowerL](https://github.com/HowerL)

### 参考项目

GitHub 上的开源项目：

- [SocialSisterYi/bilibili-API-collect](https://github.com/SocialSisterYi/bilibili-API-collect)
- [catlair/bili-task-puppeteer](https://github.com/catlair/bili-task-puppeteer)
- [lzghzr/TampermonkeyJS](https://github.com/lzghzr/TampermonkeyJS)
- [whyour/qinglong](https://github.com/whyour/qinglong)
- [RayWangQvQ/BiliBiliToolPro](https://github.com/RayWangQvQ/BiliBiliToolPro)
- [dd178/BILI_judgement](https://github.com/dd178/BILI_judgement)

同时感谢所有被依赖的开源项目，详见 package.json。包括没有依赖的 https://github.com/lodash

### 技术支持

- [吾爱破解](https://www.52pojie.cn/)
- [MDN](https://www.52pojie.cn//)

### 捐赠者

- 网友（春风肩上停）
- [JetBrains](https://www.jetbrains.com/zh-cn/community/opensource)
- [vtroisWhite](https://github.com/vtroisWhite)
- [wdssfff00](https://github.com/wdssfff00)

## 支持功能 <Badge v-if="isRefreshed" type="tip" :text="`版本${tagName}`" vertical="top" />

**注意：**

- 表中排列顺序即为功能的调用顺序，内部设置顺序，与配置顺序无关。
- 带删除线的表示已经弃用或其它原因不推荐使用，但是内容没有删除。

| 功能            | 默认值 | 说明                                          | 配置文档                              |
| --------------- | ------ | --------------------------------------------- | ------------------------------------- |
| exchangeCoupon  |        | 兑换漫读券 （暂时~~只能~~通过指定 task 运行） | [点击](../config/func.md#兑换漫读券)  |
| liveSignTask    | `true` | 直播间签到                                    |                                       |
| addCoins        | `true` | 投币                                          | [点击](../config/func.md#投币)        |
| bigPoint        |        | 大会员领取大积分                              | [点击](../config/func.md#大积分)      |
| shareAndWatch   | `true` | 观看和分享视频                                |                                       |
| silver2Coin     | `true` | 银瓜子兑换硬币（配合直播签到用）              |                                       |
| mangaTask       |        | 漫画任务（包含签到，分享，阅读，小游戏）      | [点击](../config/func.md#漫画任务)    |
| supGroupSign    |        | 应援团签到 （目前也无意义了啊）               |                                       |
| useCouponBp     |        | 使用 b 币券（充电/兑换电池）                  | [点击](../config/func.md#使用-b-币券) |
| getVipPrivilege |        | 获取大会员权益                                |                                       |
| matchGame       |        | 赛事竞猜（人人都是硬币慈善家）                | [点击](../config/func.md#竞猜)        |
| giveGift        |        | 赠送过期礼物                                  | [点击](../config/func.md#直播间礼物)  |
| liveIntimacy    |        | 牌子亲密度 （非云函数为异步运行）             | [点击](../config/func.md#粉丝亲密度)  |
| batchUnfollow   |        | 取消关注                                      | [点击](../config/func.md#取关分组)    |
| ~~liveLottery~~ |        | ~~直播天选时刻~~（黑号风险）                  | [点击](../config/func.md#天选时刻)    |
| liveRedPack     |        | 直播天选红包                                  | [点击](../config/func.md#天选红包)    |
| dailyBattery    |        | 每日电池任务（电池+1）                        |                                       |
| activityLottery |        | 转盘抽奖                                      | [点击](../config/func.md#转盘抽奖)    |
| judgement       |        | 风纪委员                                      | [点击](../config/func.md#风纪委员)    |

只有将这些值设置为 `true` 才会生效，如果设置为 `false` ，具体的配置再怎么样也不会去执行，下面是参考写法。

::: details 参考写法

```json5
{
  function: {
    silver2Coin: true,
    addCoins: true,
    liveSignTask: true,
    shareAndWatch: true,
    mangaTask: false,
    batchUnfollow: false,
    supGroupSign: false,
    useCouponBp: false,
    getVipPrivilege: false,
    giveGift: false,
    matchGame: false,
    liveRedPack: false,
    supGroupSign: false,
    bigPoint: false,
    judgement: false,
    activityLottery: false,
  },
}
```

:::

## 重要提示

::: danger
cookie 重要提示（关于频繁失效），除了账号本身可能存在的风险外（例如异地登录，大量的天选等），还可能是以下原因：

请务必查看 Cookie 的获取[点击这里跳转](../config/get_value.md)

~~不管你是否注意到，但是我很高兴的告诉，本项目不再开源，当然下载到的内容能够直接看到代码。开源与不开源无所谓，因为到闭源为止，通过 issue 和 pr 提供代码或文档帮助的一共只有 5 位， star 有 263 个。~~如果你还想再来到这里，记住 `btdocs.vercel.app` 才是一直不变的链接。
:::

::: tip
获取直播间 -412 错误，暂时不知道怎么解决。影响功能：liveLottery、liveRedPack。
:::

## 使用说明

配置方式见顶部导航栏（移动端点左上角，上面部分是导航），点击配置[或者点击这里跳转](../config/)。

## 更新

::: tip 测试内容
漫画基本上获取积分的方法都有了，兑换也有了，使用也有。相当于来了个更高级的等免功能
:::

[历史各版本配置对比](/config/version.md)

- <Badge type="tip" text="新增" vertical="middle" /> 亲密任务发送弹幕可自定义内容。（已发布，现仅更新文档。详见对比配置）

链接跳转：

[更多日志点击访问详情](./update.md)

## QQ 群

~~如果需要反馈，尽量选择 issue，而不是进群。~~

扫码加入群，没事别进去，自己扫码进群以后哔哔谁把你拉进来的是什么意思（群号：759694670）：

![qq群](/images/qq_group.png)

## 支持

<SponsorShip></SponsorShip>

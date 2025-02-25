---
lang: zh-CN
title: 介绍
description: 简单介绍
---

## 安装

```bash
npm install -g bilioutils
```

## 使用

```bash
bilioutils -v
bilioutils -h
```

## 配置

```json5
{
  // 浏览器用户代理
  userAgent: 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:106.0) Gecko/20100101 Firefox/106.0',
  // 云函数随机运行用的时间段
  dailyRunTime: '17:30:00-23:40:00',
  // 通用 api 延迟时间（s）
  apiDelay: [2, 6],
  // b 站 cookie （登录信息）可能需要双引号
  // prettier-ignore
  cookie: "xxxxx",
  // 间隔多少天创建一个新的 cookie（非刷新）
  createCookieDay: -1,
  // 配置运行的功能
  function: {
    // 瓜子兑换硬币
    silver2Coin: true,
    // 投币
    addCoins: true,
    // 直播签到
    liveSignTask: true,
    // 分享和观看
    shareAndWatch: true,
    // 漫画任务
    mangaTask: false,
    // 应援团签到
    supGroupSign: false,
    // 使用 b 币券
    useCouponBp: false,
    // 获取 vip 权益
    getVipPrivilege: true,
    // 直播赠送礼物
    giveGift: false,
    // 赛事竞猜
    matchGame: false,
    // 取消关注
    batchUnfollow: false,
    // 直播天选时刻
    liveLottery: false,
    // 粉丝牌等级
    liveIntimacy: false,
    // 大会员大积分
    bigPoint: false,
    // 风纪委员
    judgement: false,
    // 转盘抽奖
    activityLottery: false,
    // 每日电池
    dailyBattery: false,
    // 直播挂机
    watchLink: true,
  },
  // 消息推送
  message: {
    // 换行
    br: '\n',
    // 仅错误时发送
    onlyError: false,
    // 邮箱
    email: {
      from: '',
      to: '',
      pass: '',
      host: 'smtp.163.com',
      port: 465,
    },
    // push+
    pushplusToken: '',
    // server 酱
    SCKEY: '',
    // ... 更多省略
    // 自定义
    api: '',
  },
  // 投币相关
  coin: {
    // 目标等级
    targetLevel: 6,
    // 保留的硬币数
    stayCoins: 0,
    // 投币的数量（上限5）
    targetCoins: 5,
    // 自定义 up
    customizeUp: [],
    // 获取稿件的来源（排序），留空则来自 首页推荐
    src: ['自定义UP', '特别关注', '关注', '首页推荐', '分区排行'],
    // 合作视频精准匹配上传者
    upperAccMatch: false,
  },
  // 使用b币券
  couponBalance: {
    /** 充电的 up 默认自己 */
    mid: 0,
    /** 预设时间，哪一天？，空数组为每一天 */
    presetTime: [10, 20],
    /** 使用的方式 充电/charge | 电池/battery */
    use: '充电',
  },
  // 赛事竞猜
  match: {
    // 每次竞猜的数量
    coins: 2,
    // 压赔率低的（正压）大于 0 的数，反之等于 0
    selection: 1,
    // 赔率需要达到的差距
    diff: 7.0,
  },
  // 天选时刻
  lottery: {
    // 奖品描述不能包含，比如“自拍一张”将被跳过
    excludeAward: [
      '舰',
      '船',
      '航海',
      '代金券',
      '优惠券',
      '自拍',
      '照',
      '写真',
      '图',
      '提督',
      '车车一局',
      '再来一局',
      '游戏道具',
    ],
    // 奖品描述包含，如果满足则跳过 excludeAward
    includeAward: ['谢'],
    // up 黑名单（up 的 id，不是房间号）
    blackUid: [65566781, 1277481241, 1643654862, 603676925],
    // 关注的用户统一移动到此分组
    moveTag: '天选时刻',
    // 扫描几页直播间
    pageNum: 2,
    /** 关注回复处理方式  */
    actFollowMsg: 'read',
    /** 扫描关注的用户 */
    scanFollow: '',
    /** 跳过需要关注的天选 */
    skipNeedFollow: false,
    // 打印可能中奖的消息
    mayBeWinMsg: true,
  },
  redPack: {
    /**
     * 声明：
     * 表示次数时，小于等于0的数表示不限制次数
     */
    // 直播间来源方式 1 活动（活动链接可能更新不及时），2 扫描。其它值 所有方式依次尝试。
    source: 0,
    // 活动链接
    uri: 'https://api.live.bilibili.com/xlive/fuxi-interface/RedPacketController/redPocketPlaying?_ts_rpc_args_=[101181]',
    // 仅使用活动时有效，每轮抢红包的间隔时间（秒）
    intervalActive: 60,
    // 中场休息时间，当每参加了几个直播间的时候，休息一下 [参加个数，休息时间（分，小于1为直接结束）]
    restTime: [-1, -1],
    // 疑似触发风控时休眠时间，[连续出现次数，休眠时间（分，小于1为直接结束）]
    riskTime: [-1, -1], // 与 riskNum 不同，该参数会与 restTime 互相影响重置次数
    // 同时参与的直播间数量
    linkRoomNum: 1,
    // 总参与次数，达到后不管结果如何，直接结束
    totalNum: -1,
    // 参与直播时发送的弹幕数量（与内置数量比，min(10，剩余时间/5，配置)）
    // [固定值]，[最少,最多]
    dmNum: [10],
    // 是否在等待时处理关注用户（读取消息，移动）
    moveUpInWait: true,
    /** 天选时刻关注 UP 移动到分组 */
    moveTag: 'rp关注',
    /** 关注回复处理方式  */
    actFollowMsg: 'read',
    // 连续超过多少次没有中，直接结束，小于1为不限制
    noWinNum: 10, // 避免一直运行
    // 连续疑似触发风控多少次，直接结束，小于1为不限制
    riskNum: 5, // 避免一直运行
  },
  unFollow: {
    // 单个取消的时间间隔（秒）
    delay: 3,
    // 中场休息，[取消数量, 休息时间（分）] 取消数量和休息时间都应该为正数（非0），否则无效
    restTime: [20, -1],
    // 总数 -1 无限制
    totalNum: -1,
    // 取消关注的 tag
    tags: ['天选时刻', 'rp关注'],
  },
  // 直播间礼物
  gift: {
    // 自定义投喂礼物 UP， 在所填中随机选取
    mids: [],
    // 投喂礼物 id
    // 辣条 小心心 能量石头 PK票 小海浪
    id: [1, 30607, 30426, 31531, 31674],
    // 投喂礼物 name
    name: ['辣条', '能量石头'],
    // 无视其它礼物配置，投喂所有即将过期礼物
    all: false,
  },
  // 亲密度
  intimacy: {
    // 直播弹幕
    liveSendMessage: true,
    // 点赞直播间
    liveLike: true,
    // 每日亲密度上限 （系统 1500）
    limitFeed: 1500,
    // 耗时很长的直播心跳（默认关闭）
    liveHeart: false,
    // 白名单
    whiteList: [],
    // 黑名单
    blackList: [],
    // 同时有多少个直播间已获取亲密度超过200时，强制跳过弹幕和点赞。小于 0 不跳过
    skipNum: 10,
    // 完成直播心跳后是否再检查一次，可能因为数据延迟而重复操作，不建议云函数开启
    isRetryHeart: false,
    // 专属弹幕
    dm: {
      // id 为 up 主 mid，非直播间 id。用于某些直播间可能有机器人玩法
      // '11111': '打卡',
      // '22222': ['打卡', '签到']
    },
  },
  // 漫画
  manga: {
    // 签到
    sign: true,
    // 购买漫画
    buy: false,
    // 每日阅读
    read: false,
    // 购买漫画 id（优先级高）
    mc: [],
    // 购买漫画名称（优先级中）
    name: [],
    // 购买追漫（优先级低）
    love: true,
    // 猜拳
    guess: false,
  },
  // 风纪委员
  jury: {
    // 默认投票 0-3 好-无法判断，从中随机
    vote: [0, 0, 1],
    // 是否采用参考投票，不采用就使用默认投票
    opinion: true,
    // 排除投票 0-3 好-无法判断，用于配合参考投票，不影响【默认投票】配置
    notOpinion: [3],
    // 是否观看视频 0 不观看，1 观看，从中随机
    insiders: [0, 1],
    // 是否匿名 0 不匿名，1 匿名，从中随机
    anonymous: [0, 1],
    // 没有案件不退出，运行一次直到完成
    once: true,
    // 参考人数最少满足
    opinionMin: 3,
    // 没有案件后等待时间（分）
    waitTime: 20,
    // 云函数下使用新的触发器进行休眠
    newTrigger: true,
    // 计算 opinionMin 值时，目标用户投没有观看的权重，观看了是 1
    insiderWeight: 0.8,
    // 异步，非云函数下使用。不支持推送结果
    async: false,
  },
  // 大积分
  bigPoint: {
    // 是否间隔 20s 再重试一次，或者直接填写等待时间（秒）
    isRetry: 20,
    // 是否完成观看视频的任务
    isWatch: true,
    // 领取任务后的观看延时（秒）
    watchDelay: 40,
  },
  // 转盘抽奖
  activityLottery: {
    // 活动列表
    list: [],
    // 是否从网络请求活动列表
    isRequest: true,
    // 抽奖延时（秒）
    delay: [1.8, 3.2],
    // 与 isRequest 配合，是否通过追番增加次数（追番然后取消，不一定有用），云函数不建议开
    bangumi: false,
    // 同上，不过是关注，（未完成，配置了也没用）
    follow: false,
    // 请求 GitHub 使用的代理前缀，例如 https://ghproxy.com/
    proxyPrefix: 'https://ghproxy.com/',
    // 自定义活动列表链接
    customUrl: '',
  },
  // 兑换漫读券
  exchangeCoupon: {
    // 兑换漫读券数量，小于 1 为自动
    num: 1,
    // 间隔时间，单位 ms，随机误差 -50 ~ 150
    delay: 2000,
    // 保留积分数
    keepAmount: 0,
  },
  // 直播挂机
  watchLink: {
    // 目标的 uid （非直播间 id）
    uid: [],
    // 挂机时长，分钟
    time: 65
  },
  log: {
    // 推送日志等级，'error' | 'warn' | 'info' | 'verbose' | 'debug'，或者 false 关闭
    pushLevel: 'debug',
    // 打印日志等级，同上
    consoleLevel: 'debug',
    // 文件日志等级，同上
    fileLevel: 'debug',
    // 是否使用 emoji 表示日志等级
    useEmoji: true,
    // 拆分日志文件，单位 'day', 'month'
    fileSplit: 'day',
  },
  limit: {
    // 获取经验限制为 6 级
    level6: true,
    // 投币限制为 5 颗
    coins5: true,
  },
}
```

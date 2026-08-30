# RC1.9.3 TEST REPORT

## Node/规则回归

## qa.js

```text
PASS no old holder 404
PASS no vector old name
PASS WJC present
PASS question holder present
PASS pigeon present
PASS frozen signature state
PASS exit ending
PASS old ending
PASS same ending
PASS final release
PASS normal uid
PASS unknown client
PASS identity edge
```

## qa_reachability.js

```text
PASS route home/default
PASS route candidate
PASS route wjc
PASS route code17
PASS route incident2018
PASS route temp1848
PASS route helper
PASS route audit
PASS route snapshots
PASS route snapconfig
PASS route edges
PASS route releasefinal
PASS route finalforum
PASS phase7 trigger/use (4)
PASS phase8 trigger/use (5)
PASS phase9 trigger/use (6)
PASS phase10 trigger/use (4)
PASS phase11 trigger/use (4)
PASS release trigger/use (4)
PASS normal account trigger/use (6)
PASS forbidden old holder 404
PASS forbidden 矢量
PASS forbidden Parallax
PASS forbidden 亚当
PASS forbidden old 火山 name misuse
PASS ending END《退出》
PASS ending END《旧版》
PASS ending END《照旧》
PASS ending MARK UID1848 CLOSED
```

## player_simulation.js

```text
[
  {
    "name": "A 谨慎玩家 / 不乱点",
    "status": "PASS",
    "notes": "不需要刷无关页面凑 phaseClock。"
  },
  {
    "name": "B 从不改签名",
    "status": "PASS",
    "notes": "签名谜题变成额外证据，不再卡主线。"
  },
  {
    "name": "C 一份证据都不保存",
    "status": "PASS",
    "notes": "会丢部分可变证据，但仍能继续；代价是信息，不是死档。"
  },
  {
    "name": "D 看到退出就走",
    "status": "PASS",
    "notes": "可在不知道全部真相时合理离开。"
  },
  {
    "name": "E 留下继续查",
    "status": "PASS",
    "notes": "Phase7→11 不依赖 phaseClock。"
  },
  {
    "name": "F snapshot_B 三种设置",
    "status": "PASS",
    "notes": "错误配置和正确配置均有落点。"
  },
  {
    "name": "G 1094 不修",
    "status": "PASS",
    "notes": "可只解决自己的1848，不强迫玩家替论坛收拾全部历史。"
  },
  {
    "name": "H 1094 分开",
    "status": "PASS",
    "notes": "有独立证据支撑，不靠道德按钮文字。"
  },
  {
    "name": "I 老存档字段缺失",
    "status": "PASS",
    "notes": "Phase3/5/8类旧state至少不会因后期字段undefined直接崩。"
  },
  {
    "name": "J 乱输 Identity Edge",
    "status": "PASS",
    "notes": "错误不会Game Over，也不会NPC报正确答案。"
  }
]
```

## player_simulation_adversarial.js

```text
[
  {
    "name": "K 证据槽全塞垃圾",
    "status": "PASS",
    "notes": "玩家可以腾出槽位，不会因为早期乱存三份垃圾软锁。"
  },
  {
    "name": "L 完全相信司南",
    "status": "PASS",
    "notes": "司南是否可信仍由玩家判断，不是阵营条。"
  },
  {
    "name": "M 完全不信司南",
    "status": "PASS",
    "notes": "可以把他的工具当证据来源之一，但不用相信他本人。"
  },
  {
    "name": "N 错误 snapshot END 后反悔",
    "status": "PASS",
    "notes": "END仍成立，但测试/玩家可以返回继续，不用清存档。"
  },
  {
    "name": "O 反复刷新",
    "status": "PASS",
    "notes": "刷新只产生背景状态，不决定关键章节。"
  },
  {
    "name": "P 退出后再回来",
    "status": "PASS",
    "notes": "后续可据此避免同一浏览器立刻又被当1848；本阶段先保证状态存在。"
  },
  {
    "name": "Q 乱搜司南",
    "status": "PASS",
    "notes": "没有独立“搜司南即跳主线”的危险入口；现有司南信息依旧嵌在调查链中。"
  },
  {
    "name": "R 手机窄屏",
    "status": "PASS",
    "notes": "补了长日志、按钮、顶部栏、帖子列表的窄屏兜底。"
  },
  {
    "name": "S 乱改签名很多次",
    "status": "PASS",
    "notes": "当前签名可反复改，历史引用只在第一次捕获时固定。"
  },
  {
    "name": "T 不处理1094直接释放",
    "status": "PASS",
    "notes": "玩家只救自己仍是有效主线结果。"
  }
]
```

## blind_reasoning_test.js

```text
{
  "stages": [
    {
      "id": "S1",
      "name": "注册后看到2019同名旧帖",
      "evidence": [
        "2019 archived newcomer uses current username",
        "profile says UID1848",
        "player knows they registered today"
      ],
      "likely": [
        "网站把当前用户名动态套进旧页面",
        "管理员做了恶作剧",
        "自己以前来过但忘了"
      ],
      "mustNotForce": "自己以前来过"
    },
    {
      "id": "S2",
      "name": "静态引用/缓存开始不一致",
      "evidence": [
        "current profile changes",
        "saved/offline comparison differs",
        "some quoted text stays older"
      ],
      "likely": [
        "缓存不同步",
        "页面模板有bug",
        "旧记录被逐步覆盖"
      ],
      "mustNotForce": "超自然改历史"
    },
    {
      "id": "S3",
      "name": "2023？？与2024鸽子",
      "evidence": [
        "two distinct handles in independent sources",
        "different habits/timing",
        "same UID1848"
      ],
      "likely": [
        "1848是共享/回收账号",
        "这些人其实是同一人换名",
        "论坛在把不同人揉进同一UID"
      ],
      "mustNotForce": "同一人换名"
    },
    {
      "id": "S4",
      "name": "Adam / 司南 / 房东",
      "evidence": [
        "Adam coexists with historical1848",
        "0317/1094 both appear",
        "old CSV says1094=房东"
      ],
      "likely": [
        "账号迁移出错",
        "司南有两个号",
        "1094被接管后旧历史也被重写"
      ],
      "mustNotForce": "司南就是幕后黑手"
    },
    {
      "id": "S5",
      "name": "2018 repair / future DB",
      "evidence": [
        "future-dated rows in 2018 export",
        "repair job",
        "force_confirm",
        "group rebuild"
      ],
      "likely": [
        "数据库预生成未来状态",
        "损坏记录被错误重建",
        "有人伪造2018备份"
      ],
      "mustNotForce": "网站会预言"
    },
    {
      "id": "S6",
      "name": "Side Helper / snapshot_B",
      "evidence": [
        "client reports",
        "1094 consensus drift",
        "offline replay clients",
        "current client state uploads"
      ],
      "likely": [
        "很多所谓记忆变化其实是显示/缓存污染",
        "客户端共识在反向喂服务器",
        "仍有少量现象不能靠Helper解释"
      ],
      "mustNotForce": "网站直接修改大脑"
    }
  ],
  "checks": [
    {
      "name": "avoid explicit conclusion: 所以当前名字在往旧记录里倒灌",
      "pass": true
    },
    {
      "name": "avoid explicit conclusion: 那说明数据库会预测未来",
      "pass": true
    },
    {
      "name": "avoid explicit conclusion: 说明1848以前就有人用",
      "pass": true
    },
    {
      "name": "avoid explicit conclusion: 系统是在修复一致性",
      "pass": true
    },
    {
      "name": "independent holders",
      "pass": true
    },
    {
      "name": "Adam independent",
      "pass": true
    },
    {
      "name": "房东 independent evidence",
      "pass": true
    },
    {
      "name": "future evidence remains",
      "pass": true
    },
    {
      "name": "helper explanation exists",
      "pass": true
    },
    {
      "name": "A0 remains",
      "pass": true
    },
    {
      "name": "unknown residue remains",
      "pass": true
    }
  ]
}
```

## 浏览器DOM实测

使用本机Chromium headless，通过DevTools Protocol把完整单文件版注入about:blank并进行真实DOM点击。结果：

```json
{
  "dialogue": {
    "vague_post_gets_clarifying_reply": true,
    "player_can_reply": true,
    "detail_gets_external_verification": true,
    "npc_does_not_skip_player_turn": true,
    "fire_calls_e_after_second_player_reply": true,
    "e_enters_after_another_player_turn": true,
    "ui_has_old_forum_editor": true
  },
  "mundane": {
    "obviously_mundane_post_does_not_start_story": true
  },
  "pass": true
}
```

验证了模糊发帖、玩家补充、火山验证、E延后加入、普通耳机帖不触发主线。

## 静态专项审计

```json
{
  "build_id": true,
  "broad_inquiry_trigger": true,
  "vague_help_supported": true,
  "mundane_filter_exists": true,
  "player_reply_sequence": true,
  "early_back_and_forth": true,
  "thread_carries_2023": true,
  "thread_carries_2024": true,
  "thread_carries_wjc": true,
  "thread_carries_future": true,
  "thread_carries_helper": true,
  "thread_carries_snapshot": true,
  "story_pm_removed": true,
  "old_save_dialogue_migration": true,
  "old_forum_ui": true,
  "mobile_ui": true
}
```

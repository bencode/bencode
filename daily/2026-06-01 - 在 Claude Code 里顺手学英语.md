# 在 Claude Code 里顺手学英语

在 Claude Code 的对话里，消息前面加个 `en:` 就能顺手学英语——不用切出去查，就在手头这个对话里完成。

核心：随手学的摩擦是上下文切换——要停下来把想学的重新组织出来再查，这步就拦住人了。所以让工具直接操作对话里已有的内容。

- `en: 中文` 译成地道英文
- `en:?` 把刚聊的那句拎出来讲
- `en:save` 进个人词典（按词条合并、记遇见次数，不是流水账）

还有个被动模式：学英语的语境里主动指出值得学的表达。自学的难处常常不是学不会，是不知道该学什么，让它主动挑。

## 装一下

开源的 Claude Code skill，在 [bencode/daily-skills](https://github.com/bencode/daily-skills)：

```
/plugin marketplace add bencode/daily-skills
/plugin install daily-skills@daily-skills
```

词典默认写到 `~/.en/dictionary.md`，想换：`export EN_DICT=…`。

## 用起来什么样

打 `en:?`（回溯刚聊的那个），它拆成一张卡：

```
## factor out (sth)
- 义：把共同/底层的部分抽离出来单独定义
- 换法：extract / pull out / abstract away
- 同义：extract, decompose into, modularize
- 反义：inline, fold in, hardcode
- 搭配：factor out the common logic ｜ factor X out into Y
- 语法：可分动词——factor out sth / factor sth out
- 例：We factored the shared semantics out into a set of primitives.
- 遇见：2026-06-01「先定义一些原语」· 1 次
```

`en:save` 一下并进词典：

```
## in a good mood
- 义：心情好、情绪不错
- 换法/语域：in good spirits（书面）｜ feeling good / great（口语）
- 同义：cheerful, upbeat, in high spirits
- 反义：in a bad mood, down, grumpy
- 例：A morning walk always puts me in a good mood.
- 遇见：2026-06-01「我心情不错」· 1 次
```

再遇到同一个词，它不新开一行，而是次数 +1、补一条语境——所以是词典，不是流水账。

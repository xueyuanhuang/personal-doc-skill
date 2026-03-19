# /personal-doc — AI 生成个人使用说明书

用 Claude Code 自动抓取你的全网内容，分析后生成一份入职用的「个人使用说明书」。

核心思路：**让 AI 从你实际写过的东西里认识你，而不是让你从零描述自己。**

## 它能做什么

1. **抓取你的全网数据** — 微信公众号文章、Twitter 推文、小红书笔记，全量拉取
2. **结合简历和测评** — 盖洛普优势识别器、Principles You、MBTI 等
3. **4 个 AI Agent 并行分析** — 分别看性格、工作风格、兴趣价值观、高频金句
4. **生成完整说明书** — 10 个板块，有数据有例子有原话，直接导入飞书

## 生成的说明书长什么样

| 板块 | 内容 |
|------|------|
| 关于我 | 一段自然的自我介绍，不是「性格开朗善于沟通」 |
| 读书和工作经历 | 简历 + 文章里提到的细节补充 |
| 在 RockFlow 的工作 | 岗位 + 个人优势怎么用上 |
| 我的性格 | 从真实内容提炼，含优点也含短板 |
| 兴趣爱好 | 有具体数据（不是「喜欢读书」而是「386 篇探店笔记」） |
| 推荐书单/电影 | 从文章里提过的书，附个人点评 |
| 希望你如何与我协作 | 可操作的协作建议 |
| 理想中的团队 | 团队价值观期望 |
| 一些我常说的话 | AI 从全量内容里选出的代表性金句 |

开头会自动加一行 AI 生成声明：

> 本文由 AI（Claude Code）基于本人公众号 X 篇文章、Twitter X 条推文、小红书 X 条笔记的全量数据自动分析生成，本人仅提供素材和审阅，对 AI 的发挥不承担责任。如有夸大或过度解读，请找 Claude 算账。

## 安装

```bash
# 1. 克隆到 Claude Code skills 目录
git clone https://github.com/xueyuanhuang/personal-doc-skill.git ~/.claude/skills/personal-doc

# 2. 在 ~/.claude/CLAUDE.md 的 Skills 部分加一行
# - `/personal-doc` — AI 生成个人使用说明书：收集简历+测评+全网内容 → 抓取社交媒体数据 → 4 Agent 并行分析 → 生成入职用个人说明书
```

## 使用

在 Claude Code 对话里输入：

```
/personal-doc
```

然后按提示操作：

1. **提供素材** — 简历、测评报告、社交媒体账号
2. **等待抓取** — AI 自动并行抓取各平台数据
3. **等待分析** — 4 个 Agent 并行跑，几分钟出结果
4. **审阅修改** — 看初稿，提修改意见，迭代到满意
5. **导出** — 生成 .md 文件，导入飞书

## 需要准备什么

**必须：**
- 简历
- 入职岗位

**可选（越多越好）：**
- 测评报告（盖洛普、Principles You、MBTI 等）
- 微信公众号文章（本地文件或公众号名称）
- Twitter 用户名（需要配置 [opentwitter MCP](https://github.com/opentwitter/opentwitter-mcp)）
- 小红书 cookie（浏览器登录后从 DevTools 获取 `a1` 和 `web_session`）

## 小红书 cookie 怎么拿

1. 浏览器打开 [xiaohongshu.com](https://www.xiaohongshu.com) 并登录
2. F12 打开 DevTools → Application → Cookies
3. 找到 `a1` 和 `web_session` 的值
4. 在 Claude Code 对话里直接贴给 AI 就行

## 依赖

- [Claude Code](https://claude.ai/claude-code)（需要 Claude Pro/Team/Enterprise）
- [Playwright MCP](https://github.com/anthropics/mcp-playwright)（小红书抓取用）
- [opentwitter MCP](https://github.com/opentwitter/opentwitter-mcp)（Twitter 抓取用，可选）

## 文件说明

```
personal-doc/
├── README.md        # 你在看的这个
├── SKILL.md         # Claude Code skill 定义（核心流程）
└── template.md      # 说明书输出模板（10 个板块）
```

## 背后的故事

这个 skill 诞生于一次真实的入职体验。入职要填个人说明书，与其自己从零写一篇「正确的废话」，不如让 AI 从自己公众号 307 篇文章、Twitter 109 条推文、小红书 386 条笔记里去认识自己。

结果发现：AI 从你的内容里提炼出来的你，比你自以为的你更准确。因为它看的不是你想展示什么，而是你实际写了什么。

详细过程写成了一篇文章：[八百条帖子里的我](https://mp.weixin.qq.com/s/xxx)（链接待更新）

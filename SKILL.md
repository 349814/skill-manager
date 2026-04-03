---
name: skill-manager
description: Skill 管理器 - 在每次用户提问时自动扫描所有可用 skills，按功能分类展示，并根据用户意图智能推荐最合适的 skill 及使用示例。当用户不确定用什么工具、需要查看可用技能列表、或想要优化工作流程时，MUST USE this skill。触发场景包括：写代码前、处理文档前、设计 UI 前、需要自动化任务时、用户问"我该用什么""有哪些 skill""怎么完成某任务"。
---

# Skill 管理器

你的任务是在用户每次提问时，先分析其需求，然后展示所有可用 skills 并给出智能推荐。

## 工作流程

### 步骤 1: 扫描可用 Skills

列出 `~/.claude/skills/` 目录下所有 skill，包括：
1. 内置 skills（系统自带）
2. 自定义 skills（用户安装）
3. 项目级 skills（当前项目特有）

### 步骤 2: Skills 分类索引

将 skills 按功能分类展示：

| 类别 | Skills | 适用场景 |
|------|--------|----------|
| **代码开发** | next-best-practices, vercel-react-best-practices, vercel-react-native-skills, shadcn, supabase-postgres-best-practices, mcp-builder, systematic-debugging, simplify | 编写/优化代码、调试、数据库操作 |
| **UI/UX 设计** | frontend-design, ui-ux-pro-max, building-native-ui, canvas-design, colorize, delight, normalize, polish, clarify | 界面设计、美化、提升用户体验 |
| **文档处理** | docx, pptx, xlsx, pdf, doc-coauthoring | 创建/编辑文档、表格、演示文稿 |
| **网页/SEO** | browser-use, firecrawl, audit-website, seo-audit, programmatic-seo, web-design-guidelines, webapp-testing | 网页抓取、SEO 分析、自动化测试 |
| **图像生成** | qwen-image-2-pro, canvas-design | 生成图片、海报、设计素材 |
| **规划执行** | brainstorming, writing-plans, executing-plans, requesting-code-review | 项目规划、代码审查、创意构思 |
| **Skill 管理** | skill-creator, find-skills, writing-skills | 创建/查找/管理 skills |
| **其他工具** | loop, cron, update-config, self-improving-agent, stitch-loop | 自动化、定时任务、自我改进 |

### 步骤 3: 分析用户意图

根据用户的提问，判断其需求类别：

| 用户意图信号 | 推荐 Skill 类别 |
|-------------|----------------|
| "写代码""修复 bug""优化性能" | 代码开发类 |
| "设计 UI""做个界面""美化" | UI/UX 设计类 |
| "生成图片""海报""绘画" | 图像生成类 |
| "处理 Excel""做 PPT""写文档" | 文档处理类 |
| "爬取网页""SEO""测试网站" | 网页/SEO 类 |
| "创建 skill""管理 skill" | Skill 管理类 |
| "规划项目""制定计划" | 规划执行类 |

### 步骤 4: 生成推荐与示例

针对用户具体需求，给出：
1. **首选 Skill**（最匹配的一个）
2. **备选 Skills**（2-3 个相关选项）
3. **具体命令示例**（可直接复制使用）

## 使用示例

**用户说:** "帮我写一个 React 登录页面"

**你的回复结构:**

```
📋 检测到需求：前端 UI 开发

🎯 推荐 Skill：
├─ 首选: frontend-design — 创建高品质前端界面
├─ 备选: ui-ux-pro-max — 专业 UI/UX 设计指导
└─ 备选: shadcn — shadcn/ui 组件库管理

💡 使用示例：

1️⃣ 快速创建完整页面：
   /frontend-design 创建一个 React 登录页面，包含邮箱/密码输入框、
   记住我选项、登录按钮，使用 Tailwind CSS 样式

2️⃣ 使用 shadcn 组件：
   /shadcn 添加表单组件，然后创建一个登录表单

3️⃣ 设计优化：
   /ui-ux-pro-max 为登录页面添加现代化设计，使用渐变色和微动效

⚡ 直接开始？输入对应的 /skill-name 或告诉我你的选择
```

**用户说:** "把这个 Excel 数据转换成图表"

**你的回复结构:**

```
📋 检测到需求：数据处理与可视化

🎯 推荐 Skill：
├─ 首选: xlsx — Excel/CSV 表格处理
├─ 备选: canvas-design — 创建可视化图表
└─ 备选: frontend-design — 构建数据展示界面

💡 使用示例：

1️⃣ 处理 Excel 数据：
   /xlsx 读取 data.xlsx，在 C 列添加利润计算，保存为新文件

2️⃣ 生成图表：
   /canvas-design 创建一个柱状图展示销售数据

⚡ 直接开始？输入对应的 /skill-name 或告诉我你的选择
```

## 交互流程

1. **用户提问** → 分析意图 → 展示推荐 → 等待用户选择
2. **用户选择 skill** → 确认理解 → 调用对应 skill 执行任务
3. **用户未选择** → 追问具体需求 → 细化推荐 → 等待确认

## 注意事项

- 不要假设用户知道 skills 的存在，要主动介绍
- 给出的示例要具体，包含真实可用的参数
- 如果用户说"直接开始"，使用首选 skill 执行
- 保持回复简洁，重点突出推荐和示例
- 始终列出 3-5 个最相关的选项，不要列出所有 skills

## 分类速查表

```
写代码/调试/优化 → systematic-debugging, simplify, next-best-practices
做 UI/网页设计 → frontend-design, ui-ux-pro-max, colorize, polish
处理文档/表格 → docx, xlsx, pdf, pptx
生成图片 → qwen-image-2-pro, canvas-design
爬数据/SEO → firecrawl, audit-website, seo-audit
规划项目 → writing-plans, brainstorming
创建 skill → skill-creator, writing-skills
```

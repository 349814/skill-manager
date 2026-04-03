# Skill Manager

一个 Claude Code Skill，用于在每次对话开始时自动分析用户需求，扫描并推荐最合适的可用 Skill。

## 功能

- **扫描 Skills**：自动扫描 `~/.claude/skills/` 下的所有可用 skill
- **分类索引**：将 skills 按开发、设计、文档、SEO、图像生成、规划执行等维度归类
- **意图分析**：根据用户的自然语言描述，识别需求类型
- **智能推荐**：给出首选 skill + 备选 skills + 可直接复制的使用示例

## 触发场景

请在以下场景主动使用此 skill：

- 用户不确定该用什么工具时
- 用户问"有哪些 skill""我该用什么""怎么完成某任务"时
- 用户想优化工作流程、寻找更合适的工具时
- 写代码、处理文档、设计 UI、自动化任务之前

## 使用方式

直接调用：

```
/skill-manager
```

或在任何提问时由 Claude 自动触发。

## 输出示例

当用户说"帮我写一个 React 登录页面"时，skill-manager 会输出：

```
📋 检测到需求：前端 UI 开发

🎯 推荐 Skill：
├─ 首选: frontend-design — 创建高品质前端界面
├─ 备选: ui-ux-pro-max — 专业 UI/UX 设计指导
└─ 备选: shadcn — shadcn/ui 组件库管理

💡 使用示例：
1️⃣ /frontend-design 创建一个 React 登录页面...
2️⃣ /shadcn 添加表单组件...
3️⃣ /ui-ux-pro-max 为登录页面添加现代化设计...

⚡ 直接开始？输入对应的 /skill-name 或告诉我你的选择
```

## 文件结构

```
.
├── SKILL.md      # Skill 定义与执行逻辑
├── README.md     # 本说明文件
└── .vscode/
    └── settings.json
```

## 开发

若需修改分类或推荐逻辑，请编辑 [SKILL.md](SKILL.md)。

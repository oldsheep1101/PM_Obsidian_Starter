# Obsidian AI 插件安装与设置指南

> 本指南将帮助你安装和配置最实用的 Obsidian AI 插件，提升你的知识管理效率。

---

## 🤖 必备 AI 插件

### 1. Smart Connections (智能连接)
**简介：** 自动发现和建立笔记间的语义链接，构建知识网络。

#### 安装步骤：
1. 打开 Obsidian
2. 点击 `Settings` (⚙️)
3. 选择 `第三方插件`
4. 关闭安全模式
5. 点击 `社区插件的浏览`
6. 搜索 "Smart Connections"
7. 点击 `Install`，然后点击 `Enable`

#### 基础配置：
```json
{
  "smart connections": {
    "max connections per file": 10,
    "min similarity": 0.7,
    "enabled": true
  }
}
```

**推荐设置：**
- 最大连接数：10 (避免过多连接)
- 相似度阈值：0.7 (平衡相关性和数量)
- 启用自动发现：✅

#### 使用方法：
- **查看链接**：点击笔记右侧的 "Connections" 面板
- **手动连接**：右键点击笔记 → `Smart Connections` → `Add connection`
- **定期更新**：每周运行一次 `Update connections`

### 2. Copilot (AI 助手)
**简介：** 集成多种 AI 服务，在 Obsidian 中获得 AI 帮助。

#### 安装步骤：
1. 在 Community plugins 中搜索 "Copilot"
2. 安装并启用
3. 配置 API 密钥（见下方配置）

#### API 密钥配置
**选项 1：OpenAI (GPT-4)**
1. 访问 [OpenAI Platform](https://platform.openai.com)
2. 创建 API Key
3. 在 Obsidian Settings 中：
   ```
   Copilot > API Key: your_openai_key
   Model: gpt-4
   Temperature: 0.7
   ```

**选项 2：Anthropic Claude**
1. 访问 [Anthropic Console](https://console.anthropic.com)
2. 创建 API Key
3. 在 Obsidian Settings 中：
   ```
   Copilot > Provider: Anthropic
   API Key: your_claude_key
   Model: claude-3-sonnet
   ```

**选项 3：本地模型 (Ollama)**
1. 安装 Ollama：`brew install ollama` (Mac)
2. 下载模型：`ollama pull llama2`
3. 配置：
   ```
   Copilot > Provider: Ollama
   Model: llama2
   URL: http://localhost:11434
   ```

#### 常用命令
在copilot对话框中输入
```markdown
/summarize          # 总结当前笔记
/explain           # 解释选中的内容
/brainstorm        # 头脑风暴
/translate         # 翻译文本
/format            # 格式化文本
```

---

## 🔄 高级 AI 工作流

### 1. 知识库增强
**插件推荐：**
- **Kanban**：AI 帮助整理任务看板
- **Dataview**：AI 分析数据视图
- **Excalidraw**：AI 辅助绘制流程图

**配置示例：**
```markdown
# AI 驱动的 PM 工作流

## 项目概览
```dataview
TABLE WITHOUT ID
  file.link AS 项目,
  status AS 状态,
  priority AS 优先级,
  AI 分析 := "使用 AI 自动生成项目风险评估"
FROM "01_Projects"
```

## AI 生成的内容
```query
AI 自动生成的用户需求分类标签
```
```

### 2. 自动化模板填充
**Text Generator 插件设置：**
1. 安装 "Text Generator" 插件
2. 创建 PM 专属模板
3. 配置 AI 自动填充

**模板示例：**
```markdown
# 用户研究报告
生成日期: {{date}}
AI 分析员: Copilot

## 用户画像
AI 自动生成的用户画像...

## 需求分析
基于用户反馈的 AI 分析...
```

---

## 🧪 实验室练习

### 练习 1：智能链接实验
1. 创建 5 篇关于 PM 工作的笔记
2. 确保 Smart Connections 已启用
3. 查看自动生成的连接
4. 手动添加你认为相关的连接
5. 对比差异，调整配置

**预期结果：**
- 发现笔记间隐藏的联系
- 建立知识网络的雏形
- 提高信息检索效率

### 练习 2：AI 写作助手
1. 打开 Meeting_Notes_Template.md
2. 选中空白部分
3. 使用 `/summarize` 命令
4. 让 AI 总结关键要点

**提示词示例：**
```
请为产品团队会议生成一个简要总结，包括：
- 3个关键决策
- 3个重要行动项
- 1个需要跟进的问题
```

### 练习 3：知识图谱优化
1. 使用 Obsidian 的图谱视图
2. 调整 Smart Connections 的相似度设置
3. 观察连接密度的变化
4. 找到最适合你的平衡点

---

## ⚙️ 性能优化建议

### 1. 减少延迟
```json
{
  "copilot": {
    "cache enabled": true,
    "max tokens": 1000,
    "timeout": 30
  }
}
```

### 2. 节约 API 使用
- 设置合理的请求频率
- 使用缓存功能
- 批量处理相似请求

### 3. 本地模型优化
- 对于简单任务，使用本地模型
- 复杂写作任务使用云端 API
- 定期更新模型版本

---

## 🚀 进阶配置

### 自定义 AI 提示词
在 `settings.json` 中添加：
```json
{
  "custom prompts": {
    "pm_analysis": "作为产品经理，分析以下内容...",
    "user_feedback": "整理用户反馈，找出关键模式...",
    "feature_request": "评估以下功能请求的可行性..."
  }
}
```

### 自动化工作流
1. 创建 `AI_automation` 文件夹
2. 设置触发条件
3. 配置 AI 处理规则

**示例：**
```markdown
# AI 自动化规则
触发：当创建新笔记时
动作：自动生成标签和摘要
频率：每次保存时
```

---

## 📊 效果监控

### 使用数据追踪 AI 效果
```dataview
TABLE WITHOUT ID
  "链接效率" AS 效率,
  "内容生成速度" AS 速度,
  "AI 准确度" AS 准确度
WHERE file.name = "AI 效果报告"
```

### 定期检查
- [ ] 每周：检查 AI 生成内容质量
- [ ] 每月：回顾知识网络增长
- [ ] 每季度：评估整体效率提升

---

## 🆘 常见问题

### Q: AI 生成的内容不准确？
A: 
1. 调整提示词更具体
2. 提供更多上下文
3. 使用更高温度值增加创造性

### Q: 响应太慢？
A:
1. 检查网络连接
2. 使用本地模型
3. 减少同时进行的请求

### Q: 找不到相关连接？
A:
1. 降低相似度阈值
2. 手动添加关键连接
3. 增加笔记内容丰富度

---

## 📝 维护建议
1. 定期更新插件版本
2. 备份重要的 AI 配置
3. 记录有价值的提示词
4. 分享成果给团队

---

*提示：AI 是增强工具，不是替代品。保持批判性思维，验证 AI 生成的内容。*
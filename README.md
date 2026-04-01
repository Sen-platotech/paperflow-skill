# Paperflow Skill

<p align="center">
  <strong>📚 学术期刊聚合 Skill</strong><br>
  <sub>搜索顶刊、获取论文、AI总结、生成报告</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/OpenClaw-Skill-blue.svg" alt="OpenClaw Skill">
  <img src="https://img.shields.io/badge/Claude%20Code-Compatible-green.svg" alt="Claude Code">
  <img src="https://img.shields.io/badge/Python-3.10+-yellow.svg" alt="Python">
</p>

---

## 功能特点

- 🔍 **智能期刊搜索** - 内置15+领域顶刊数据，支持动态搜索
- 📰 **论文获取** - CrossRef API + RSS订阅获取最新论文
- 🌐 **中英双语翻译** - 本地Ollama翻译，无需API费用
- 🤖 **AI智能总结** - 基于摘要生成中文总结
- 📊 **Markdown报告** - 按期刊分组生成报告

## 支持的领域

**计算机科学**
- 人工智能: Nature MI, JMLR, TPAMI, AI Journal, Machine Learning
- 机器学习: JMLR, Nature MI, ML, IEEE TNNLS
- 自然语言处理: Computational Linguistics, TACL, NLE
- 计算机视觉: IJCV, TPAMI, Pattern Recognition
- 机器人: IJRR, IEEE T-RO
- 数据科学: EPJ Data Science, JASSS

**自然科学**
- 生物学: Nature, Science, Cell
- 神经科学: Nature Neuroscience, Neuron
- 化学: Nature Chemistry, JACS, Angewandte Chemie
- 物理学: PRL, Nature Physics, RMP
- 材料科学: Nature Materials, Advanced Materials
- 量子: Quantum, npj Quantum Information

**医学与生命科学**
- 医学: NEJM, Lancet, JAMA, Nature Medicine
- 生物信息: Bioinformatics, BMC Bioinformatics

**社会科学**
- 政治科学: APSR, AJPS, Journal of Politics, World Politics
- 计算社会科学: JCSS, EPJ Data Science, JASSS, Social Networks
- 经济学: AER, QJE, JPE
- 心理学: Annual Review Psych, Psych Bulletin

## 安装

### 依赖

```bash
pip install httpx feedparser beautifulsoup4 sqlalchemy ollama pyyaml

# 可选：PDF支持
pip install pymupdf

# 启动Ollama服务
ollama serve

# 下载模型
ollama pull qwen2.5
```

### 安装Skill

**方法1: 使用SkillHub (推荐)**
```
在OpenClaw中: skillhub install paperflow
```

**方法2: 手动安装**
```bash
git clone https://github.com/Sen-platotech/paperflow-skill.git
cd paperflow-skill
```

## 使用方式

### 1. 搜索期刊

```bash
python3 scripts/search_journals.py "Artificial Intelligence" --top 10
python3 scripts/search_journals.py "Political Science" --top 5
python3 scripts/search_journals.py "Computational Social Science" --top 5

# JSON输出
python3 scripts/search_journals.py "AI" --json
```

### 2. 订阅期刊

```bash
# 订阅
python3 scripts/subscribe.py add 2522-5839  # Nature Machine Intelligence
python3 scripts/subscribe.py add 0003-0554  # American Political Science Review

# 查看订阅
python3 scripts/subscribe.py list

# 取消订阅
python3 scripts/subscribe.py remove 2522-5839
```

### 3. 获取论文

```bash
# 获取最近7天的论文
python3 scripts/fetch_papers.py --days 7

# 获取最近30天
python3 scripts/fetch_papers.py --days 30 --json
```

### 4. AI总结

```bash
# 生成总结
python3 scripts/summarize.py --days 7 --limit 10

# 指定模型
python3 scripts/summarize.py --days 7 --model qwen2.5

# JSON输出
python3 scripts/summarize.py --days 7 --json
```

### 5. 生成报告

```bash
# 生成Markdown报告
python3 scripts/report.py --output report.md --days 7

# 自定义标题
python3 scripts/report.py --output ai_papers.md --title "AI领域最新论文" --days 14
```

## 输出示例

### 搜索期刊

```
Searching journals for: Artificial Intelligence
Found 5 top journals from database
1. Nature Machine Intelligence (2522-5839) - Springer Nature
2. Journal of Machine Learning Research (1532-4435) - JMLR
3. IEEE TPAMI (0162-8828) - IEEE
4. Artificial Intelligence (0004-3702) - Elsevier
5. Machine Learning (0885-6125) - Springer
```

### 报告格式

```markdown
# 学术论文聚合报告

**时间范围:** 2024-01-15 ~ 2024-01-22
**共收录:** 15 篇论文，来自 2 个期刊

## Nature Machine Intelligence

### 1. Machine learning global atomic representations...
**作者:** J. Frank, S. Chmiela

**🤖 AI总结:**
> 本文提出了一种基于欧几里得快速注意力机制的原子表示学习方法，
> 能够高效地学习分子中原子的表示，在分子性质预测中表现优异。

**链接:** [原文] | [PDF] | [DOI]
```

## 数据存储

- 数据库: `~/.paperflow/papers.db`
- 配置: `~/.paperflow/config.yaml`

## 相关项目

- [paperflow](https://github.com/Sen-platotech/paperflow) - Python CLI版本

## License

MIT License

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/Sen-platotech">Sen-platotech</a>
</p>

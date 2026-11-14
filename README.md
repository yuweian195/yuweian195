# 雨维安 · yuweian195

**AI 应用开发 / Agent 工程 / RAG / AIOps**

我关注的问题很具体：把大模型能力做成**可解释、可测试、可部署**的工程系统，而不是只停留在 Prompt 演示。核心判断交给确定性规则、图谱与检索，LLM 只负责语言组织；每个项目都保留执行轨迹、离线降级和自动化测试。

---

## 项目

<table>
  <tr>
    <td width="33%" valign="top">
      <a href="https://github.com/yuweian195/hire-agent">
        <img src="https://raw.githubusercontent.com/yuweian195/hire-agent/main/docs/screenshots/pipeline-board.png" alt="HireAgent" width="100%">
      </a>
      <h3><a href="https://github.com/yuweian195/hire-agent">HireAgent</a></h3>
      <p>智能招聘 Agent：简历解析、六维评分、批量排名、面试评估与候选人流程。</p>
      <p><code>Python</code> <code>Java</code> <code>TypeScript</code></p>
    </td>
    <td width="33%" valign="top">
      <a href="https://github.com/yuweian195/law-agent">
        <img src="https://raw.githubusercontent.com/yuweian195/law-agent/main/docs/screenshots/contract-console.png" alt="LawAgent" width="100%">
      </a>
      <h3><a href="https://github.com/yuweian195/law-agent">LawAgent</a></h3>
      <p>法律 RAG 与合同审查：法条检索、带引用问答、赔偿计算、条款风险。</p>
      <p><code>Python</code> <code>TypeScript</code></p>
    </td>
    <td width="33%" valign="top">
      <a href="https://github.com/yuweian195/telecom-agent">
        <img src="https://raw.githubusercontent.com/yuweian195/telecom-agent/main/docs/screenshots/noc-wallboard.png" alt="TelecomAgent" width="100%">
      </a>
      <h3><a href="https://github.com/yuweian195/telecom-agent">TelecomAgent</a></h3>
      <p>AIOps：告警压缩、拓扑关联、根因定位、派单与人工复核。</p>
      <p><code>Python</code> <code>TypeScript</code></p>
    </td>
  </tr>
</table>

### 1. HireAgent · 智能招聘

- **业务链路**：简历解析 → 六维评分 → JD 匹配 → 合规检查 → 条件路由 → 面试题生成
- **技术结构**：Python LangGraph 工作流；Java Spring Boot ATS 服务（岗位 / 候选人 / 筛选记录）；TypeScript React 招聘看板
- **工程结果**：26 个 Python 测试 + 5 个 Java 测试 + 前端构建；无 API Key 可离线运行
- **可解释性**：固定权重、逐维理由、每个节点的 trace；岗位级权重可配置

### 2. LawAgent · 法律 RAG

- **业务链路**：问题识别 → 法条检索 → 金额计算 → 带引用意见；合同条款拆分 → 规则扫描 → 法条校验 → 风险评分
- **技术结构**：BM25 + 中文同义扩展；LangGraph 问答/审查双工作流；TypeScript React 审查控制台
- **评估结果**：15 个合成问题，纯 BM25 Recall@3 93%，同义扩展后 100%；合同规则 Precision/Recall 100%
- **边界**：结论只引用本地法条库；检索不足时明确说“依据不足”，不硬答

### 3. TelecomAgent · AIOps

- **业务链路**：告警接入 → 时间窗压缩 → 拓扑关联 → 根因定位 → 影响面 → 案例检索 → 派单 / 人工复核
- **技术结构**：Python 拓扑压缩与规则引擎；LangGraph 条件分支；Node.js 实时告警网关（WebSocket / 滑动窗口）；TypeScript React NOC 大屏
- **评估结果**：223 条合成告警压缩为 10 起事件（95.5%）；3/3 根因命中；影响面召回 100%
- **工程细节**：低置信度事件自动转人工；离线分析结果可回放

---

## 技术栈

![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB)
![Java](https://img.shields.io/badge/Java-21-ED8B00)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6)
![LangGraph](https://img.shields.io/badge/Agent-LangGraph-1C3C3C)
![FastAPI](https://img.shields.io/badge/API-FastAPI-009688)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.3-6DB33F)
![React](https://img.shields.io/badge/React-19-61DAFB)
![Streamlit](https://img.shields.io/badge/UI-Streamlit-FF4B4B)
![SQLite](https://img.shields.io/badge/Storage-SQLite-003B57)
![Docker](https://img.shields.io/badge/Deploy-Docker-2496ED)

## 工程方法

- **确定性优先**：规则、拓扑和检索负责核心判断；LLM 只做评语、意见与摘要，避免不可审计的幻觉。
- **评估先行**：每个项目都有合成评估集，区分 baseline 与改进项，不用“100%”掩盖样本规模。
- **可运行**：无 API Key 可离线运行；Docker Compose、CI、pytest / JUnit / TypeScript build 全链路覆盖。
- **边界清晰**：单机 SQLite、同步链路、合成数据；不把生产化能力写成已完成。

## 联系

- GitHub：[@yuweian195](https://github.com/yuweian195)
- 项目问题与建议：欢迎在对应仓库开 Issue

# skill 版协作约定

本仓库是「学习方向规划助手」skill 实现形式的正本。

## 边界
- 只改本仓库内的 `SKILL.md`、`references/`、`agents/`、`README.md`。
- 不读写网站仓库 `D:\learning-direction-planner-web`，不改 Dify 实现 `D:\dify`。
- 产品级通用设计以 `D:\learning-direction-planner-product\` 为准，本仓库不复制那份文档；产品意图变了先改那边，执行手法变了先改这里。
- 不把运行实例（如 `D:\skill-test\planner`）里的会话、记录、凭证复制进来。
- 执行手法在本仓库改完并自查后，各实现再各自跟进；不允许先在某个实现里改规则文本，再倒回来补这里。

## 改动要求
- 每条新规则要写明：不加它，使用者会遇到什么具体问题。
- 改完按 `references/acceptance.md` 的口径自查，不靠「感觉差不多了」。
- 规则里的阶段完成依据只能是实际读取结果、用户原话或已核实来源。

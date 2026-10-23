# 学习方向规划助手 · skill 版

这是「学习方向规划助手」这个产品的 **skill 实现形式**，也是本仓库唯一正本。

- 入口：`SKILL.md`
- 细节规则：`references/` 六个文件（验收、BOSS 路由、行业调研、资料与记录、OpenCLI、推荐与证据）
- 展示信息：`agents/openai.yaml`
- 分发包：`dist/learning-direction-planner.zip`（不纳入版本控制，可随时重打）

## 同一产品的其他实现形式（各自独立，互不覆盖）

| 实现形式 | 位置 | 说明 |
|---|---|---|
| skill（本仓库） | `D:\learning-direction-planner` | 流程与判断规则的正本，改规则只改这里 |
| 网站 | `D:\learning-direction-planner-web` | 独立网页实现与 Node 服务，有自己的 git 和测试 |
| Dify Chatflow | `D:\dify`（V1 等） | Dify 侧实现与草稿，有自己的边界约定 |

三边共享的是**产品规则本身**，不是文件：规则变了，先改本仓库，再各自跟进并在各自仓库验证。本仓库不读也不写另外两处，另外两处也不得直接改本仓库的文件。

## 怎么用

### 装进某个 DSH 实例

把 `SKILL.md`、`agents/`、`references/` 复制到目标实例的用户级 skill 目录：

```powershell
# 全局实例
$dst = "$env:USERPROFILE\.dsh\skills\learning-direction-planner"

# 或隔离实例（例如 D:\skill-test\planner 那套）
# $dst = "D:\skill-test\planner\.dsh\skills\learning-direction-planner"

New-Item -ItemType Directory -Force -Path $dst | Out-Null
Copy-Item SKILL.md,agents,references -Destination $dst -Recurse -Force
```

装好后重开该实例即可在技能列表里看到「学习方向规划助手」。

### 重打分发包

```powershell
$tmp = Join-Path $env:TEMP 'ldp-pack'
Remove-Item $tmp -Recurse -Force -ErrorAction SilentlyContinue
New-Item -ItemType Directory -Force -Path (Join-Path $tmp 'learning-direction-planner') | Out-Null
Copy-Item SKILL.md,agents,references -Destination (Join-Path $tmp 'learning-direction-planner') -Recurse -Force
New-Item -ItemType Directory -Force -Path dist | Out-Null
Compress-Archive -Path (Join-Path $tmp 'learning-direction-planner') -DestinationPath 'dist\learning-direction-planner.zip' -Force
Remove-Item $tmp -Recurse -Force
```

## 边界

- 本仓库只放 skill 自身需要的文件，不放网站代码、不放 Dify 导出、不放运行记录。
- 运行产生的个人数据（会话、记录、凭证）不进入本仓库。
- 改规则前先看 `references/acceptance.md` 的验收口径，改完按它自查。

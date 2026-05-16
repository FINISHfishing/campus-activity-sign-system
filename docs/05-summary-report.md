# 总结报告

> 要求：本文件应由全组成员共同编辑，并在解决冲突后提交到 `main` 分支。

**课程名称**  <u>软件项目管理</u>
**实验项目**  <u>软件项目管理综合实验</u>
**实验仪器**  <u>计算机</u>

## 1. 项目背景与小组分工

### 项目背景
本实验以“校园活动报名与签到管理系统”为统一项目背景。该系统旨在支持活动发布、学生报名、名单审核、二维码签到、签到统计和活动总结导出等基本功能。本次实验聚焦软件项目管理过程，通过 Git 版本管理工具完成项目初始化、三级 WBS 分解、进度计划编制、配置管理、分支协作、冲突解决及总结报告提交，重点训练项目管理成果的形成、版本受控和协作留痕能力，不要求实现完整的业务系统。

### 项目目标
- 建立统一的项目仓库与目录结构
- 完成围绕交付物的三级 WBS 分解
- 制定简化进度计划（含活动、工期、前置关系、责任人）
- 制定配置管理方案（配置项识别、分支策略、提交与合并规则）
- 制造并解决一次 Git 冲突，记录解决过程
- 全体成员共同完成总结报告，并提交至 main 分支

### 小组分工
| 姓名（角色） | 主要职责 | Git 用户名 |
|-------------|----------|------------|
| 成员A（项目经理） | 统筹整体进度，负责最终提交与合并，完善项目启动文档 | qmn182 |
| 成员B（计划负责人） | 负责 WBS 分解与进度计划文档 | zhaojiameizhi |
| 成员C（配置管理员） | 负责配置管理方案、分支策略与版本留痕 | mayila |
| 成员D（协作成员） | 参与文档完善、冲突制造与解决 | ganquan |


## 2. WBS 分解思路
请填写。

## 3. 进度安排依据
请填写。

## 4. 配置管理与协作过程
请填写。

## 5. 冲突解决过程记录
### 冲突基本信息
- **冲突文件**: `docs/conflict.md`
- **涉及成员**: 成员A（zhaojiameizhi）与成员D（ganquan）
- **冲突类型**: 同一行代码修改冲突 + 文件结构冲突（合并时被误删的「建议操作」模块恢复）
- **解决时间**: 2026-05-01

### 冲突制造步骤
1.  成员A在分支 `feature/conflict-edit` 中，将 `conflict.md` 中的“当前结论”行修改为：“本组决定先经过 dev 再合并到 main”。
2.  成员D在分支 `feature/conflict-ganquan` 中，将同一行修改为：“本组决定直接合并到 main”。
3.  两个分支分别提交并推送到远程仓库，等待合并。

### 冲突发现与解决过程
当项目经理尝试将两个分支合并到 `main` 时，Git 检测到同一行内容被不同方式修改，触发了合并冲突。冲突标记如下：

<<<<<<< HEAD
本组决定先经过 dev 再合并到 main
=======
本组决定直接合并到 main
>>>>>>> feature/conflict-ganquan
### 解决方式
1.  团队成员通过线上沟通协商，最终决定采用成员 A 的版本（先合并到 `dev` 再合并到 `main`），因为该方案更符合实验要求的分支策略。
2.  手动编辑 `conflict.md`，删除 Git 冲突标记，保留选定内容，同时恢复被误删的「建议操作」模块，确保文件结构完整。
3.  提交解决后的文件，并完成合并。
4.  合并后发现文件仍存在标点符号和格式错误，成员 D 创建 `hotfix-conflict-typo` 分支，先后两次对文件进行格式修正，并补充冲突解决说明。
5.  为了完整记录本次冲突实践，成员 D 新增 `conflict-resolution-log.md` 文档，记录冲突产生、协商与解决的全过程。

### 最终结果
- 冲突已完全解决，`conflict.md` 内容正确，文件结构完整，格式规范。
- 解决过程详细记录在 `conflict-resolution-log.md` 中，包含冲突双方修改内容、协商过程及最终决议。
- 合并后的 `main` 分支包含正确的冲突解决版本及后续 `hotfix` 修正，所有修改均已提交并推送至远程仓库。
### 成员D操作命令
# 1. 创建冲突分支并制造冲突
git checkout main
git pull origin main
git checkout -b feature/conflict-ganquan
vim docs/conflict.md
# 将“当前结论”行修改为：“本组决定直接合并到 main”
git add docs/conflict.md
git commit -m "conflict: 成员D把“当前结论”改成“本组决定直接合并到 main”"
git push origin feature/conflict-ganquan

# 2. 冲突解决后，新增冲突解决日志文档
git checkout feature/conflict-ganquan
git pull origin main
touch docs/conflict-resolution-log.md
vim docs/conflict-resolution-log.md
git add docs/conflict-resolution-log.md
git commit -m "docs: 增加“冲突解决日志文档（conflict-resolution-log.md）”（成员D）"
git push origin feature/conflict-ganquan

# 3. 创建hotfix分支修正合并后的文件格式
git checkout main
git pull origin main
git checkout -b hotfix-conflict-typo
vim docs/conflict.md
# 第一次修正标点符号错误
git add docs/conflict.md
git commit -m "hotfix: 修改conflict.md 的标点符号"
git push origin hotfix-conflict-typo

# 第二次修正标点符号并补充冲突解决说明
vim docs/conflict.md
git add docs/conflict.md
git commit -m "hotfix: 第二次修改conflict.md 的标点符号"
git push origin hotfix-conflict-typo

# 补充冲突解决说明并修正文本错误
vim docs/conflict.md
git add docs/conflict.md
git commit -m "hotfix: 修正conflict.md在进行“冲突合并”之后产生的文本错误，并添加一些说明语句。"
git push origin hotfix-conflict-typo

# 4. 将hotfix分支合并回main分支
git checkout main
git merge hotfix-conflict-typo
git push origin main

# 5. 拉取summary分支，添加个人总结
git checkout feature/summary-report
git pull origin feature/summary-report
vim docs/05-summary-report.md
# 添加第5节冲突解决记录及第6节个人收获
git add docs/05-summary-report.md
git commit -m "docs: 补充冲突解决过程记录及个人收获（成员D）"
git push origin feature/summary-report

## 6. 经验与问题
### 成员D（ganquan）的收获与问题
- **收获**: 
  此次，我亲身体验了 Git 冲突的完整产生、协商、解决与后续修正流程，不仅掌握了如何识别冲突标记、使用VS Code手动编辑解决冲突，还学会了通过hotfix分支对合并后的文件进行格式修正。同时，我理解了冲突解决日志的重要性，在本次实验中主动创建了`conflict-resolution-log.md`，完整记录了冲突的产生、协商与解决过程，确保团队协作过程可追溯。此外，通过本次实验，我对Git的分支策略、push/pull/fetch的区别有了更清晰的认识，尤其是在多人协作中，如何通过分支隔离避免不必要的冲突。

- **问题与反思**: 
  1.  在制造冲突时，两个分支基于不同的基础版本，导致除了目标行外还产生了文件结构的冲突，增加了解决复杂度。今后在并行开发前，应确保分支从最新的 `main` 派生，并定期同步远程更新，减少结构性冲突的产生。
  2.  合并完成后发现文件存在标点符号和格式错误，虽通过hotfix分支及时修正，但也意识到在提交前应仔细检查文件格式，避免后续额外的修正操作。

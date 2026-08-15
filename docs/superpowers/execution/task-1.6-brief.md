### Task 1.6: 处置工作台（人工复核与执法台账）

**Files:**
- Create: `apps/dispatch_console/`（处置工作台前端与后端）
- Create: `docs/engineering/处置工作台用户手册.md`

**Interfaces:**
- Consumes: Task 1.5 的 `dispatch[]`、`evidence_package[]`
- Produces: 处置记录 `action{action_id, dispatch_id, action_type(监管侧|平台协同侧), action_content, reviewer1, reviewer2, status, closed_at}`；供 Task 1.8 试点评估统计

- [ ] **Step 1: 复核流程实现**

实现红级双人复核（两人独立确认/驳回）、黄级初筛（确认违规则升级）、绿级归档；复核操作全部留痕。

- [ ] **Step 2: 处置建议书生成**

复核确认后自动生成处置建议书（关联线索、固证包、规则条款、建议的监管侧/平台协同侧动作），由执法人员编辑后走法定程序。

- [ ] **Step 3: 执法台账**

记录预警、责令改正、约谈、立案、信用公示等监管侧动作及平台协同侧动作的发起与反馈跟踪。

- [ ] **Step 4: 验收**

核对：红级线索 100% 走双人复核；处置动作均由人工发起，系统无自动对外处置出口；台账与日志完整。


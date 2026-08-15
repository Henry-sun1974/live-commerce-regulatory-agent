### Task 1.5: 线索库与自动分派

**Files:**
- Create: `services/dispatch/`（线索库与分派服务）
- Create: `docs/engineering/分派规则说明.md`

**Interfaces:**
- Consumes: Task 1.4 的 `evidence_package[]`；Task 1.1 的属地配置
- Produces: 分派单 `dispatch{dispatch_id, clue_id, org_code, status(待复核|复核中|已处置|已结案), assigned_at}`，供 Task 1.6 工作台消费

- [ ] **Step 1: 线索库实现**

实现线索/固证包/分派单的数据模型与查询接口，记录全量决策日志（识别→固证→分派各环节时间戳与操作者）。

- [ ] **Step 2: 属地分派规则**

按试点区县属地规则自动分派至基层执法账号；红级线索强制进入"待复核"状态并通知 2 名执法人员。

- [ ] **Step 3: 时效监控**

统计"线索生成 → 分派"时长，超过 10 分钟自动告警。

- [ ] **Step 4: 验收**

核对：线索生成→分派 ≤10 分钟（连续 7 日统计达标）；红级线索全部进入双人复核流程；分派日志完整可审计。


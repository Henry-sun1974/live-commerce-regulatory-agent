### Task 1.7: 监管大屏与合规服务

**Files:**
- Create: `apps/monitor_dashboard/`（监管大屏）
- Create: `services/compliance_guide/`（合规提示服务）

**Interfaces:**
- Consumes: Task 1.5 线索库统计数据；Task 1.6 处置记录
- Produces: 大屏指标（覆盖率、线索分布、处置进度，口径见 Global Constraints）；合规提示书 `compliance_guide{guide_id, merchant_id, content, sent_at}`

- [ ] **Step 1: 大屏指标**

按方案 v2 第十二章指标口径实现大屏统计（覆盖率、红黄绿线索分布、处置进度、复核率）。

- [ ] **Step 2: 合规提示**

对轻微/首次问题生成合规提示或行政指导书草稿，经执法人员确认后发送。

- [ ] **Step 3: 验收**

核对：大屏指标与口径定义一致（抽样比对 10 项数值）；合规提示发送须经人工确认。


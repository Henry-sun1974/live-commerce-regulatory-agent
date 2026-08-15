### Task 0.3: 搭建金标准评测集框架

**Files:**
- Create: `docs/regulatory/评测集标注规范.md`
- Create: `data/golden_set/golden_v0.jsonl`（首批人工标注样本，≥100 条）

**Interfaces:**
- Consumes: Task 0.2 规则清单（作为标注时的判定依据）
- Produces: 标注样本格式 `{sample_id, text, is_violation, violation_type, rule_ids[], labeler, agreed}`，供 Task 1.3 评测

- [ ] **Step 1: 编写标注规范**

定义：样本来源（试点品类的真实直播话术/商品描述，脱敏后使用）、判定标准（对照规则清单）、标注字段、争议处理（第三人仲裁）。

- [ ] **Step 2: 首批标注**

由 2 名业务人员独立标注 ≥100 条样本（正负例比例约 1:2）；标注结果写入 `golden_v0.jsonl`，每条约含 `sample_id / text / is_violation / violation_type / rule_ids / labeler`。

- [ ] **Step 3: 一致性校验**

比对双人标注，计算一致率；不一致样本由第三人仲裁并标记 `agreed: true`。

- [ ] **Step 4: 验收**

核对：标注样本 ≥100 条；双人标注一致率 ≥90%（否则补充仲裁后重测）；`golden_v0.jsonl` 结构完整。验收通过后进入 Task 1.3 依赖就绪。

---

## 阶段1 · 试点闭环（3 个月，单平台×单品类×试点区县）


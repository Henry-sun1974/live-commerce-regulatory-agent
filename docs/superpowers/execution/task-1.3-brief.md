### Task 1.3: 规则引擎 + 双模型识别

**Files:**
- Create: `services/rule_engine/`（规则引擎服务，加载 `rules_v0.yaml`）
- Create: `services/ai_detect/`（AI 辅助识别服务，输出置信度）
- Create: `docs/engineering/识别服务评测报告.md`

**Interfaces:**
- Consumes: Task 1.2 的 `transcript[]`、`frame_ocr[]`；Task 0.2 的 `rules_v0.yaml`；Task 0.3 的 `golden_v0.jsonl`
- Produces: 线索对象 `clue{clue_id, room_id, level(红|黄|绿), rule_ids[], ai_conf, evidence_refs[]}`，供 Task 1.4 固证、Task 1.5 分派

- [ ] **Step 1: 规则引擎实现**

实现规则加载与匹配：规则命中 → 生成红级线索；规则未命中但 AI 判定违规且置信度 ≥0.8 → 生成黄级线索；其余为绿级归档。

- [ ] **Step 2: AI 识别集成**

部署本地多模态模型对转写文本与 OCR 结果做违规判定，输出 `ai_conf ∈ [0,1]`；置信度低于 0.8 不直接产生黄级线索。

- [ ] **Step 3: 金标准评测**

在 `golden_v0.jsonl` 上评测双通道（规则通道 + AI 通道）联合效果，计算精确率、召回率、F1；输出评测报告。

- [ ] **Step 4: 验收**

核对：试点期目标——精确率 ≥85%、召回率 ≥80%、F1 ≥0.82；红级线索全部由规则命中产生（可回溯 `rule_ids`）；评测报告留存。


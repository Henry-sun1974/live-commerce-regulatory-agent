### Task 0.2: 编制规则条款映射表（规则本体初版）

**Files:**
- Create: `docs/regulatory/规则条款映射表.md`
- Create: `config/rules/rules_v0.yaml`（机器可读规则清单，供规则引擎消费）

**Interfaces:**
- Consumes: Task 0.1 的结构化条款清单
- Produces: 规则记录格式 `{rule_id, rule_type, trigger, article_ref, level}`；其中 `rule_type ∈ {禁令, 阈值, 义务}`，`level ∈ {红, 黄}`；供 Task 1.3 规则引擎加载

- [ ] **Step 1: 逐条映射**

按方案 v2 附录 A 框架，将《直播电商监督管理办法》中可机器化的条款逐条映射为规则记录；每条规则必须包含：`rule_id`（R-001 起编号）、`rule_type`、`trigger`（触发条件，如话术关键词、价格波动阈值表达式）、`article_ref`（对应条号）、`level`（红/黄分级）。

- [ ] **Step 2: 阈值规则定参**

对阈值类规则（价格波动、订单金额等），由业务方提供初值并记录到 `rules_v0.yaml`；未定参的阈值规则标记 `status: pending_params`，禁止直接启用。

- [ ] **Step 3: 输出 YAML 规则清单**

将映射表内容同步为 `config/rules/rules_v0.yaml`，格式示例：

```yaml
rules:
  - rule_id: R-001
    rule_type: 禁令
    trigger: "话术包含绝对化用语（全网最好|全国第一|顶级|最先进）"
    article_ref: "第X条"
    level: 红
    status: active
```

- [ ] **Step 4: 验收**

核对：每条规则均有 `article_ref` 且与 Task 0.1 条款清单一致；无 `status: pending_params` 的规则处于 `active`；映射表覆盖方案 v2 附录 A 的 R-001～R-004 对应条款。验收通过后进入 Task 0.3。


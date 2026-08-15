### Task 1.1: 数据接入（协查数据 + 公开直播列表）

**Files:**
- Create: `docs/regulatory/数据接入与协查接口说明.md`
- Create: `config/sources/pilot_platform.yaml`（试点平台、品类、区县配置）

**Interfaces:**
- Consumes: 试点平台协查数据（依据《网络交易执法协查暂行办法》）；公开直播间列表
- Produces: 直播间清单数据流 `live_rooms[]`（字段：`room_id / platform / category / merchant_id / start_time / status`），供 Task 1.2 拉流；产出文档供 Task 1.5 分派属地规则使用

- [ ] **Step 1: 建立协查通道**

与试点平台属地监管部门/平台方协商数据对接方式（接口/文件传输），明确字段范围与频次，形成《数据接入与协查接口说明.md》。

- [ ] **Step 2: 试点配置**

在 `pilot_platform.yaml` 中写入试点平台、目标品类（食品或美妆）、试点区县范围；配置直播间列表同步任务（按日更新）。

- [ ] **Step 3: 采集与落库**

实现公开直播间列表采集（仅公开展示页），与协查数据合并去重后写入直播间清单库。

- [ ] **Step 4: 验收**

核对：试点范围内可识别直播间列表日更新完整率 ≥95%（连续 7 日统计）；采集行为全部入审计日志；无绕过登录/验证码行为。


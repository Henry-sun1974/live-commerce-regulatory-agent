### Task 1.4: 固证包生成与存证

**Files:**
- Create: `services/evidence/`（固证包生成服务）
- Create: `docs/engineering/固证与存证说明.md`

**Interfaces:**
- Consumes: Task 1.3 的 `clue[]`；Task 1.2 的原始片段、转写、OCR、页面快照
- Produces: 固证包 `evidence_package{package_id, clue_id, video_ref, transcript_ref, snapshot_refs[], meta{capture_time, device_id, source_url, room_id}, sha256, timestamp_token}`，供 Task 1.5 分派、Task 1.6 处置工作台查看

- [ ] **Step 1: 固证包组装**

对每条红/黄线索，自动组装：违规片段（上下文前后各 30 秒）+ 转写文本 + 页面快照 + 取证元数据（NTP 校时采集时间、设备标识、源 URL、直播场次标识）。

- [ ] **Step 2: 哈希与时间戳**

对固证包计算 SHA-256 哈希，接入可信时间戳服务（或区块链存证），生成 `timestamp_token` 并随包存储。

- [ ] **Step 3: 存储隔离**

原始采集数据与固证包分离存储；固证包目录只读，任何修改触发哈希校验告警。

- [ ] **Step 4: 验收**

核对：抽查 10 个固证包，哈希可复算且与记录一致；时间戳可验证；片段含前后 30 秒上下文；固证完整率 100%。


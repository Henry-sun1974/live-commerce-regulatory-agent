### Task 1.2: 流媒体拉流与 ASR 转写流水线

**Files:**
- Create: `pipelines/stream_ingest/`（拉流、转写、抽帧三个模块的工程目录与运行文档）
- Create: `docs/engineering/拉流转写流水线运行手册.md`

**Interfaces:**
- Consumes: Task 1.1 的 `live_rooms[]`；试点平台公开直播流地址
- Produces: 转写文本流 `transcript{room_id, ts_start, ts_end, text, asr_conf}` 与关键帧 OCR 结果 `frame_ocr{room_id, ts, text, image_ref}`，供 Task 1.3 识别；供 Task 1.4 固证包引用

- [ ] **Step 1: 拉流模块**

基于 FFmpeg 实现多路并发拉流（按试点直播间清单动态启停），断流自动重连，单路超时降级为轮询重试；记录拉流日志（起止时间、丢流率）。

- [ ] **Step 2: ASR 转写模块**

部署本地化中文转写引擎，实现音频实时转写（RTF<0.1）与关键帧抽帧 OCR；转写结果带时间戳区间与置信度。

- [ ] **Step 3: 72 小时试运行**

对试点平台目标品类的全部直播间连续运行 72 小时，统计丢流率、转写 RTF、OCR 抽帧完整率。

- [ ] **Step 4: 验收**

核对：丢流率 <1%；单路转写 RTF<0.1；抽查 10 段转写文本，与人工听写比对，字准率 ≥85%；试运行报告写入运行手册。


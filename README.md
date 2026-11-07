# question-bank

Alethic Insight（CUMT）招新 **机试题库** 仓库。

## 定位与限期公开政策

经组织者本次明确授权，本仓库与[会话展示仓](https://github.com/CUMT-Alethic-Insight-Lab/2026autumn-recruitment-sessions-publication)计划于 **2026 年 11 月 8 日公开，展示 7 天，截止 2026 年 11 月 15 日 03:10（北京时间，UTC+8）**。本次授权取代本 README 原先「仅限私有、严禁公开」的政策。

到期由组织者将仓库转为私有、结束公开展示；这是需要组织者执行的安排，**不承诺已设置或会自动完成切换**。公开期间已被下载或复制的材料无法通过转私有收回。限期结束不撤销使用者遵守许可条件时已获得的 CC BY-NC-SA 4.0 授权，详见 [LICENSE.md](LICENSE.md)。

公开的目的是提供公平、可讨论的筛选示范：题目可以被学习，标准可以被研究；我们不以隐藏标准维持区分度，而希望读者学习提出问题、作出取舍、核验 AI 输出与为判断负责。

## 收录范围与阅读边界

- [第五版题库](2026autumn/question_bank_v5.md)除题面外，还保留评分锚点、参考思路、考察点、优秀回答标志、常见翻车模式、评分阶梯，以及历史修订、废弃题与面试归档素材。**不能把库内全部 30 题都称为现行笔试题**；正选、备选、历史版本与面试用途应按原文语境区分。
- 原文中的「评审专用」「不下发」等字样保留当时的使用语境，不代表本次限期展示仍对这些段落保密。参考思路、出题人假设不等于唯一正确答案，历史记录也不等于当前实施承诺。
- **题目配图未纳入本次发布**；个别历史材料已过期或仍有缺件，相关引用、外部链接和事实陈述不保证仍然有效。不补造图片、附件、研究底稿或核验结果，也不将此版本描述为完整可复现的考试包。
- 真实协作过程与评审说明见[会话展示仓](https://github.com/CUMT-Alethic-Insight-Lab/2026autumn-recruitment-sessions-publication)。本题库的许可不自动覆盖该仓的考生表达、项目与第三方材料。

## 许可与署名

组织者有权授权的原创题目、评分锚点与评审标准等内容采用 **CC BY-NC-SA 4.0（署名—非商业性使用—相同方式共享 4.0 国际）**，范围及条件见 [LICENSE.md](LICENSE.md)。署名请保留 **Alethic Insight（CUMT）** 与本题库 URL：<https://github.com/CUMT-Alethic-Insight-Lab/question-bank>，并注明修改、附上许可链接。第三方引用、论文、图像及其他外部材料不因收录而被重新授权，仍依原权利人的许可与适用法律使用。

## 目录约定

按届次组织一级目录，目录名与生产环境的 `campaign_id` 保持一致：

```
2026autumn/          # 2026 年秋季招新（campaign_id = 2026autumn）
  question_bank_v5.md
docs/                # 题库迭代讨论用的 prompt 等辅助材料
  PROMPT_question_bank_iteration.md
```

新一届招新时新建对应届次目录（如 `2027spring/`），不要覆盖往届题库——往届题目与评审 meta 留作对照。

## 迭代流程

1. 在本仓修改对应届次的题库 md；
2. 用平台仓的导入脚本写入数据库（`bank_id` 幂等 upsert，重复导入不产生重复题目）：

   ```bash
   # 先 dry-run 校验解析与统计，不写库
   python server/scripts/import_question_bank.py --md <题库md路径> --db <SQLite路径> --dry-run
   # 确认无误后正式导入
   python server/scripts/import_question_bank.py --md <题库md路径> --db <SQLite路径>
   ```

3. 导入脚本位于平台仓 `server/scripts/import_question_bank.py`，本仓不存放导入代码。

## 迭代讨论

题目打磨与版本迭代的讨论 prompt 见 `docs/PROMPT_question_bank_iteration.md`。

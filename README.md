# question-bank

Alethic Insight（CUMT）招新 **机试题库** 仓库。

## 定位与保密级别

**本仓库为私有仓库，严禁转为公开、严禁将内容复制到任何公开仓库 / Issue / 页面。**

库内除题面外还包含**评审专用 meta**：考察点、优秀回答标志、常见翻车模式、评分阶梯、面试追问素材。这些内容一旦泄露，机试对「考生使用 AI 的模式」的区分度即告失效。访问权限仅限出题与评审成员。

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

# 空姓名仍输出问候语的协作材料

## Issue

- 环境：Ubuntu，Python 3.12；其余依赖待确认。
- 复现命令：`sdt-greet --name " "`
- 期望结果：拒绝空白姓名，返回非零退出码。
- 实际结果：输出 `Hello, !`，退出码为 0。
- 待确认：是否影响 Windows 等其他平台。

## 提交信息

标题：Validate blank name in greetlab CLI

正文：空白姓名仍会输出问候语并以 0 退出；增加 strip 检查，调用 argparse.error，使空白输入以状态码 2 退出。

## 评审意见

- 行为：`--name` 只含空白时未被拦截，仍输出 `Hello, !` 并以 0 退出。
- 风险：参数校验不完整，空白输入绕过预期错误处理。
- 建议：解析参数后检查 `name.strip()` 是否为空，为空时调用 `p.error()`。
- 级别：Blocking
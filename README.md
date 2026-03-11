# 助教工具箱 · 筑真学塾

直播助教日常工具集合，打开网址即用。

## 工具列表

| 工具 | 说明 | 状态 |
|------|------|------|
| [面试助教每日引导](guide.html) | 课前/课堂/课后三阶段步骤引导，进度自动保存 | 可用 |
| [推荐上麦工具](speak.html) | 根据学员上麦历史自动排序推荐名单，一键生成群通知 | 可用 |
| [申论试卷排版](https://zhuzhen-typeset.pages.dev/) | 上传试卷内容，自动排版生成 DOCX + PDF | 可用（外链） |
| 出勤录入工具 | 拖入腾讯会议 Excel，自动匹配学员、生成出勤报告 | 开发中 |
| 上麦记录表 | 选择题目和学员，生成格式化的上麦记录文本 | 开发中 |

## 数据更新

`data/students.json` 由 [zhuzhen-edu-desk](https://github.com/XiaoMai-cool/zhuzhen-edu-desk) 的导出脚本生成：

```bash
# 在 edu-desk 仓库下执行
bash .claude/scripts/deploy_to_tools.sh
```

## 部署

通过 Cloudflare Pages 部署，推送到 `main` 分支后自动更新。

# 助教工具箱 · 筑真学塾

直播助教日常工具集合，打开网址即用。

## 工具列表

| 工具 | 说明 | 状态 |
|------|------|------|
| [助教每日引导](guide.html) | 面试 / 申论双课型，课前→课中→课后→临时交接四阶段引导，进度自动保存 | 可用 |
| [推荐上麦工具](speak.html) | 根据学员上麦历史自动排序推荐名单，一键生成群通知 | 可用 |
| [申论试卷排版](https://zhuzhen-typeset.pages.dev/) | 上传试卷内容，自动排版生成 DOCX + PDF | 可用（外链） |
| 学员学情跟进 | 查看学员画像与跟进历史，记录学情动态，标记风险学员 | 开发中 |
| 出勤录入工具 | 拖入腾讯会议 Excel，自动匹配学员、生成出勤报告 | 开发中 |
| 上麦记录表 | 选择题目和学员，生成格式化的上麦记录文本 | 开发中 |

## 负责人配置

助教每日引导页面中的「负责人」默认为"小麦"。如需切换，在网址后加参数即可：

```
guide.html?coord=新负责人姓名
```

设置后会自动记住，下次打开无需重复设置。页面底部可查看当前负责人。

## 数据更新

`data/students.json` 由 [zhuzhen-edu-desk](https://github.com/XiaoMai-cool/zhuzhen-edu-desk) 的导出脚本生成：

```bash
# 在 edu-desk 仓库下执行
bash .claude/scripts/deploy_to_tools.sh
```

## 部署

通过 Cloudflare Pages 部署，推送到 `main` 分支后自动更新。

## 后续更新计划

### 访问权限控制（Cloudflare Access + GitHub 身份验证）

对敏感页面（如推荐上麦、学员学情跟进）添加访问控制，仅允许指定 GitHub 账号访问。

**方案**：GitHub 仓库 Private + Cloudflare Access

- 仓库保持 Private，源码不公开
- 通过 Cloudflare Zero Trust 配置 GitHub 作为身份验证提供方
- 对指定路径设置 Access Policy，未授权用户无法访问页面内容
- 免费版支持 50 个用户

**配置步骤**：
1. 进入 [Cloudflare Zero Trust](https://one.dash.cloudflare.com/) 后台
2. Settings → Authentication → Add identity provider → GitHub（需在 GitHub 创建 OAuth App）
3. Access → Applications → Add application → Self-hosted，填入域名和需保护的路径
4. 创建 Policy：Allow 规则，条件为 Login Methods = GitHub + 指定邮箱

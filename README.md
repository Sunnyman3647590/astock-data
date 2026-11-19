# A 股数据参考

把公开行情、分红、财务与卖方目标价算成几张表的**只读**页面。

**在线地址**：https://sunnyman3647590.github.io/astock-data/

- 数据来源：akshare（东方财富 / 同花顺 / 财联社 / 中证）
- 页面内容：数据底座、红利收息榜、机会雷达、淘汰去向、组合回测、口径边界
- 单文件静态页，无脚本、无外链、无跟踪，手机可直接看

## 这个仓库里有什么

只有 `index.html`（和让 GitHub Pages 原样发文件的 `.nojekyll`）。

页面由本地一套投研工作台按规则算出后导出，**不含任何人的持仓、成本价、自选池与备注**——
导出时是拿一份清空了个人字段的数据库副本渲染的，不是靠模板选择性显示。

## 更新方式

在本地工作台的目录下：

```bat
set GITHUB_TOKEN=ghp_xxxx
.venv\Scripts\python.exe -m app share_page --site D:\astock-share-site --push
```

它会重新生成页面、体检、写入本目录，然后**通过 GitHub Contents API 直接更新
`index.html`**（不经过 git push）。Pages 30~60 秒后自动发布，不用点按钮。

仓库参数在 `pages.json`（repo / branch / path），不写死在代码里。

> 为什么不用 `git push`：本机 git 配了 `http.proxy=127.0.0.1:7890`，代理一关就报
> `CONNECT tunnel failed` 或 `unexpected eof`，而 `api.github.com` 另有一条通路。
> 少依赖一个会坏的环节。代价是本地不再保留 git 历史——历史在远端，每次发布一条提交。

## 声明

这是个人研究用的数据整理工具输出，不是投资建议。页面上每条结论都标了口径与已知偏差
（幸存者偏差、基准不含分红、风格依赖），请连同这些限制一起看。

# ysh-prototypes

**粤省事需求 · HTML 原型库**

存放产品原型（HTML/CSS/JS 静态页面）的仓库，每个原型一个独立目录，可直接通过 GitHub Pages 在线查看和分享。

---

## 目录结构

```
ysh-prototypes/
├── index.html                  # 原型总览页（列表 + 入口）
├── manifest.json               # 原型清单，新增原型要在这里登记
├── .nojekyll                   # 关闭 Jekyll 构建，让文件原样发布
└── prototypes/
    └── <原型名>/               # 每个原型一个目录（英文小写 + 连字符）
        └── index.html          # 该原型的入口页
```

## 在线访问

启用 GitHub Pages 后（Settings → Pages → Source 选 `main` / `root`）：

- 总览页：`https://wujl-0208.github.io/ysh-prototypes/`
- 单个原型：`https://wujl-0208.github.io/ysh-prototypes/prototypes/<原型名>/`

> 分享单条链接时用第二条，收件人不用再从总览页里找。

## 新增一个原型

已经做好的 HTML 直接放进来就行，不需要套模板：

1. 在 `prototypes/` 下新建一个目录，命名用**英文小写 + 连字符**（如 `skin-config-trial`）
2. 把做好的 HTML 放进去，**入口文件命名为 `index.html`**；如果页面带图片/字体等素材，一并放在同一目录（原型自包含，不跨目录引用）
3. 在 `manifest.json` 的 `prototypes` 数组里加一条：

```json
{
  "dir": "prototypes/skin-config-trial",
  "title": "运营后台 · 新建皮肤",
  "desc": "一句话说明这个原型要解决什么",
  "tags": ["运营后台", "表单"],
  "date": "2026-09-21",
  "status": "review"
}
```

4. 提交推送，Pages 大约几十秒后自动更新

## 字段说明

| 字段 | 说明 |
|---|---|
| `dir` | 原型目录路径，相对仓库根目录 |
| `title` | 卡片标题，用中文 |
| `desc` | 一句话说明这个原型要解决什么 |
| `tags` | 标签，用于快速识别类型的原型 |
| `date` | 更新日期，`YYYY-MM-DD` |
| `status` | `draft` 草稿 / `review` 待评审 / `final` 定稿 / `archived` 归档 |

顶层还有一个 `updated` 字段，记最后一次更新的日期。

## 约定

- **入口文件必须叫 `index.html`**：这样访问 `prototypes/<原型名>/` 就能直接打开，链接干净
- 原型**自包含**：每个目录里放全自己的 HTML/CSS/JS/图片，不跨目录引用，单独打开也能跑
- **不引外网依赖**：不用 CDN、不连外部接口，保证离线可看、Pages 也不会挂
- 目录名和文件名不用中文，避免链接编码问题；**页面内容是中文没问题**
- 定稿后不要把原型删掉，把 `status` 改成 `archived`，历史版本留着有用

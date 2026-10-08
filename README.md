# Niño3.4 指数监测 · ENSO Monitor

Niño3.4 海表温度距平指数的自动监测与可视化单页网站（零构建、纯静态、单文件）。

## 在线访问

- GitHub Pages：<https://dejavu-1280.github.io/nino3.4-monitor/>
- Cloudflare Pages（备用）：<https://nino34.pages.dev/>

## 功能

- **自动获取数据**：页面加载后自动从 NOAA CPC（ERSSTv5 月度序列，1950 至今）抓取最新数据，每 30 分钟自动刷新，支持手动刷新；跨域通过多个公共代理通道容错
- **内置快照兜底**：实时获取失败时自动回退到构建时内嵌的数据快照（1950-01 至 2026-06，共 918 个月）
- **指数图表**：距平 > +0.5°C 涂红（厄尔尼诺位相）、< −0.5°C 涂蓝（拉尼娜位相），附 ±0.5°C 阈值线、3 个月滑动平均（ONI 口径）、时间缩放与区间快捷切换
- **监测卡片**：最新指数、当前位相与连续超阈值月数、数据跨度、历史极值
- **课堂问答**：物理海洋学思考题参考答案（混合层、温盐结构、温跃层、海表热收支 Qs/Qb/Qe/Qh）

## 数据来源

NOAA Climate Prediction Center — [ERSSTv5 Niño3.4 月度序列](https://www.cpc.ncep.noaa.gov/data/indices/)，气候基准期 1991–2020。

## 更新数据快照

```bash
curl -o nino34_raw.txt "https://www.cpc.ncep.noaa.gov/data/indices/ersst5.nino.mth.91-20.ascii"
# 将新数据解析为 [yyyymm, anom] 数组，替换 index.html 中 const SNAPSHOT = [...] 后提交即可
```

仅供科研与教育参考。

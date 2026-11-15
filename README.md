# 影之刃零逆天者难度 AI 行为演示

人工智能概论第二次作业：MLP 参数学习的实现与可视化。

本作业由我与 Codex 联合完成。灵感来自《影之刃零》的适应性敌人设计；本作独立使用 MLP 实现课程模拟，不声称复现原作内部算法。

## 体验

[进入演示](./index.html)

首页介绍作品缘起；点击「进入行为演示」，再选择「观看演示」，即可观看约 56 秒的自动对局。也可选择格挡或闪避，与对手进行简单交手。概率条、网络图与损失曲线常驻展示。

## 学习过程

模型读取距离、最近防守习惯、上次防守和候选招式，预测各招命中概率。招式在当前防守选择前锁定；结算后仅用实际施展招式的结果作为标签，经反向传播和 Adam 更新参数。

- 战斗网络：6→8（tanh）→1（sigmoid），共 65 个参数。
- 学习目标：二元交叉熵；学习率 0.025；保留最近 12 条样本。
- 开局轮换探索，后续仍保留 22% 随机探索。
- 支持暂停、冻结学习、逐次拆解预测与参数更新、模型及记录导出。
- 课程 XOR 示例：2→2→1 网络；可逐步观察前向传播、梯度与训练。
- 对照实验：固定轮换、命中率统计、MLP，使用 12 个固定种子进行比较。

18 次演示用于说明学习过程，不代表充分训练。模型有探索和适应期，损失不保证单调下降。实验采用简化合成环境，不代表商业游戏或所有真人玩家。

## 文件

- `index.html`：内嵌 HTML、CSS、JavaScript 与图片的完整离线网页。MLP、反向传播、Adam 和界面源码均在此文件中。
- `README.md`：作品说明。
- `VALIDATION.md`：实际测试结果与完成边界；其中脚本路径指开发源码目录，测试脚本不包含在此精简上传目录内。

无需安装依赖、API Key 或后端。网页运行时不向远程服务发送对局、模型或个人数据；点击参考来源链接才会打开外部网站。

## GitHub Pages

把整个 `mlp-demo` 文件夹放到已有网站的发布目录下，保留原网站首页。若网站发布源是仓库根目录，则放在根目录下；若发布源是 `docs`，则放在 `docs` 下。访问现有网站地址后加 `/mlp-demo/`。

不要只上传 ZIP：GitHub Pages 发布网页文件，不会把仓库中的 ZIP 自动解压成网站。未开通 Pages 时，在仓库 Settings → Pages 中按官方文档配置发布源。

## 素材与来源

首页使用 S-GAME 官方宣传图裁切并进行淡化；角色与庭院使用 AI 辅助生成。原游戏名称、角色与官方素材权利归其权利人所有。

- [游戏官方网站](https://pbz.s-game.com/zh-CN/)
- [首页官方原图](https://pbz.s-game.com/assets/preorder/preorder-base-gallery-01-zh.png)
- [制作人采访](https://automaton-china.com/all/article/interview/20261009-30770-ying-zhi-ren-ling-zhi-zuo-ren-cai-fang/)
- [GitHub Pages 发布源配置](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

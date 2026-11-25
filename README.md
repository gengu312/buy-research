# 买前调研 · buy-research

给支持 Agent Skills 的助手装上这个中文技能，可以从“家里的东西用着不顺手”一路讨论到“这个规格、这个价，现在值得买吗”。也可以带着商品链接、购物车价格或两个现成候选，从中间开始。

比如，买一个能推到桌下的收纳车时，助手会查装上轮子和盖子后的总高。你后来决定必须保留轮子，它会更新候选。等你挑好具体款式，再算哪家便宜、值不值得为一张券凑单。

## 在 Codex 中使用

在 macOS 或 Linux 上，首次安装可以运行以下命令。仓库目录需要保留，个人技能目录里的链接指向这里。

```sh
git clone https://github.com/gengu312/buy-research.git
mkdir -p "$HOME/.agents/skills"
ln -s "$(pwd)/buy-research/skills/buy-research" "$HOME/.agents/skills/buy-research"
```

在新会话中输入：

```text
$buy-research 我家桌下净高 70 厘米，想买个带盖的收纳车。帮我找装上轮子也放得进去的，预算 120 元。
```

选好型号后可以接着问：

```text
这款我选好规格后显示 98 元包邮，明天有满减，但要再买一件。只想买收纳车的话，值得等吗？
```

更新时在克隆的仓库目录里运行 `git pull --ff-only`。其他支持 Agent Skills 的工具，可将 [skills/buy-research](skills/buy-research) 放进其技能目录，保持内部文件结构。直接阅读也可以从 [SKILL.md](skills/buy-research/SKILL.md) 开始。

## 能查到什么

实时查价需要宿主提供联网搜索或网页读取。助手会标出查到的渠道、具体款式、查询日期和可购买条件。遇到地区库存或个人会员券，提供实选规格和结算明细就够了。仅有商品资料时，仍可以比较尺寸、找规格冲突和计算优惠。这个技能本身不需要 API 密钥。

## 来源与许可

选购流程参考了 [ai_shopping_assistant_skill 的这个版本](https://github.com/jade888jgj/ai_shopping_assistant_skill/tree/9b28b987646846dafb19cc2d899b892d3bf61923)。本项目将多轮改需求、同型号混发、规格证据和同篮比价写成可单独使用的步骤。代码与文档按 [MIT 许可证](LICENSE) 分发，重新分发技能目录时请附上许可证。

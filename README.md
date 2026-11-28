# buy-research · 买前调研

<p>
  <a href="./README.md"><img src="https://img.shields.io/badge/Docs-English-2563EB?style=flat-square" alt="English" /></a>
  <a href="./README.zh-CN.md"><img src="https://img.shields.io/badge/%E6%96%87%E6%A1%A3-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87-64748B?style=flat-square" alt="简体中文" /></a>
</p>

Install this Chinese shopping-research Agent Skill into any assistant that supports Agent Skills (`SKILL.md`) to work all the way from *"something at home feels awkward to use"* to *"at this exact spec and price, is it worth buying right now?"* You can also jump in mid-way with product links, cart totals, or two shortlisted candidates.

For example, when shopping for a rolling storage cart that slides under a desk, the assistant checks the total assembled height **with both casters and lid installed**. If you later decide keeping the casters is non-negotiable, it updates the candidate list accordingly. Once you settle on an exact variant, it calculates which store is cheaper and whether padding an order just to hit a coupon threshold is actually worth it.

> **Language Note**: `buy-research` is a Simplified Chinese skill designed around Chinese e-commerce realities (multi-variant SKU traps, mixed-spec shipping, platform coupons, and order-padding math). Prompt examples below keep the original Chinese invocations alongside English explanations.

## Use in Codex

On macOS or Linux, run the commands below for first-time installation. Keep the cloned repository directory in place, since the symlink inside your personal skills directory points to it.

```sh
git clone https://github.com/gengu312/buy-research.git
mkdir -p "$HOME/.agents/skills"
ln -s "$(pwd)/buy-research/skills/buy-research" "$HOME/.agents/skills/buy-research"
```

In a new session, enter:

```text
$buy-research 我家桌下净高 70 厘米，想买个带盖的收纳车。帮我找装上轮子也放得进去的，预算 120 元。
```

*English meaning: `"$buy-research Under-desk clearance at home is 70 cm, and I want a lidded storage cart. Help me find options that still fit with the wheels installed, budget 120 RMB."`*

After choosing a model/variant, follow up with:

```text
这款我选好规格后显示 98 元包邮，明天有满减，但要再买一件。只想买收纳车的话，值得等吗？
```

*English meaning: `"After selecting my exact spec, this one shows 98 RMB with free shipping. Tomorrow there's a spend-threshold discount, but it requires buying one more item. If I only want the storage cart, is it worth waiting?"`*

To update later, run `git pull --ff-only` inside the cloned repository directory. For other tools that support Agent Skills, place [skills/buy-research](skills/buy-research) into their skills directory while keeping its internal file structure intact. To read the skill directly, start from [SKILL.md](skills/buy-research/SKILL.md).

## What It Can Check

Live price lookups require the host assistant to provide web search or web page fetching. The assistant notes the queried channel, exact SKU/variant, lookup date, and purchase eligibility conditions. When encountering regional stock limits or personal membership coupons, providing your selected spec and checkout breakdown is enough. Even with pasted product details alone, it can still compare dimensions, catch spec conflicts, and calculate net discounts. This skill itself requires no API keys.

## Credits & License

The shopping workflow references [this revision of `ai_shopping_assistant_skill`](https://github.com/jade888jgj/ai_shopping_assistant_skill/tree/9b28b987646846dafb19cc2d899b892d3bf61923). This project distills multi-turn requirement changes, mixed-variant SKU shipping ("同型号混发"), spec-evidence checks, and same-basket price comparison into standalone steps. Code and documentation are distributed under the [MIT License](LICENSE); please include the license when redistributing the skill directory.

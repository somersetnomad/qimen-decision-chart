# 奇門 Qimen Decision Chart

A nine-palace Qimen Dun Jia chart for thinking through a decision. Type your question, cast the board, and read how your position relates to the matter through the five elements.

It's a single HTML file with no build step and no dependencies beyond two Google Fonts.

![Qimen decision chart](screenshot.png)

## Using it

Open `qimen-oracle.html` in any modern browser, or publish it with GitHub Pages:

1. Rename the file to `index.html` (or link to it directly).
2. In the repository settings, open **Pages** and set the source to the main branch.
3. Your chart will be live at `https://<your-username>.github.io/<repo-name>/`.

Type a question, press **Cast chart** (or Enter), and read the result.

## Reading the chart

**The board** follows the Luo Shu layout with south at the top, as in traditional charts. Each of the eight outer palaces shows:

| Part | What it is |
| --- | --- |
| Trigram | The palace (巽 Xun, 離 Li, 坤 Kun and so on), with its direction and element |
| Door | The large character: 開 open, 休 rest, 生 life, 傷 harm, 杜 du, 景 scenery, 死 death, 驚 fear |
| Star | One of the nine stars, such as 天心 Xin or 天蓬 Peng |
| Deity | One of the eight spirits, such as 值符 Leader or 九天 Nine Heaven |
| Stems | Heaven stem over earth stem |

The center palace (中) is shown but not read.

**The seals** mark the two palaces that matter. The red 我 seal is you, standing for the day stem. The blue 事 seal is the matter, standing for the hour stem.

**The verdict** comes from the element relationship between your palace and the matter's palace:

| Relationship | Verdict |
| --- | --- |
| The matter feeds you (生) | Strong advantage: go ahead |
| Same element (比) | Stable, peer alignment |
| You feed the matter (生) | Resource drain: proceed with discipline |
| You restrain the matter (剋) | Uphill effort: hold the reins yourself |
| The matter restrains you (剋) | High obstacle: pause or change course |

**The door** in the matter's palace adds a final note. Harm, death and fear doors are shown in red and flag something to check before committing.

## How a cast works

The chart is seeded from your question plus the current five-minute window (UTC). Asking the same question within the same five minutes gives the same chart. A new question, or the same one later, gives a new chart.

This is a simplified, symbolic version of Qimen Dun Jia. A traditional chart is calculated from the solar term, the Yin or Yang escapement and the stems of the hour, and this tool doesn't do that calculation. It places the doors, stars, deities and stems by seeded shuffle instead. Treat it as a prompt for reflection, not as a professional reading or as advice.

## Customising

Everything lives in `qimen-oracle.html`:

- **Colors and fonts** are CSS variables at the top of the `<style>` block (`--paper`, `--ink`, `--cinnabar`, `--indigo` and so on).
- **Verdict wording** is in `evaluateRelationship()`.
- **Character labels** for doors, stars, deities, stems and elements are in the `HAN` object.
- **Which doors count as obstacles** is set in `ADVERSE_DOORS`.

## Accessibility

Each palace has a full text description for screen readers. Keyboard focus is visible, the seal animation is turned off when reduced motion is requested, and the layout adapts down to phone width.

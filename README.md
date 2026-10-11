# 奇門 Qimen Decision Chart

A Qimen Dun Jia hour chart for thinking through a decision. Type your question, cast the board for the moment, and read how your position relates to the matter. The chart is calculated from the solar calendar, not drawn at random.

It's a single HTML file with no build step and no dependencies beyond two Google Fonts.

![Qimen decision chart](screenshot.png)

## Using it

Open `qimen-oracle.html` in any modern browser, or publish it with GitHub Pages:

1. Rename the file to `index.html` (or link to it directly).
2. In the repository settings, open **Pages** and set the source to the main branch.
3. Your chart will be live at `https://<your-username>.github.io/<repo-name>/`.

Type a question and press **Cast chart** (or Enter). The chart is cast for the current time unless you set **Chart time** yourself, which lets you look back at a past moment or plan ahead. The question is recorded with the reading, but only the time decides the chart, as in traditional practice.

## Calculation settings

Open **Calculation settings** under the time field. Your choices are remembered in the browser and saved with each journal entry.

| Setting | Options |
| --- | --- |
| Choosing the ju | **Chai bu (拆補)**, the default: the solar term in force at the moment, with the yuan taken from the day's Jia or Ji head. **Zhi run (置閏)**: upper-yuan heads take the solar terms in turn; when a head runs more than nine days ahead of Summer or Winter Solstice, Grain in Ear or Major Snow is repeated (marked 閏). |
| Time for the pillars | **Device clock**, or **true solar time** at a longitude you enter (east positive). True solar time applies the longitude offset from UTC and the equation of time. |
| Travelling Horse from | The **hour** branch (default) or the **day** branch. |

## How the chart is calculated

The engine follows the rotating-plate (轉盤) hour method:

- **Four pillars.** The year turns at Start of Spring, months turn at each major solar term, and the day turns at 23:00, the start of the Zi hour.
- **Solar terms.** The sun's apparent longitude is computed with Jean Meeus's low-precision formula, accurate to about 0.01°, which places term boundaries within roughly fifteen minutes.
- **Escapement and ju.** Yang escapement runs from Winter Solstice to Grain in Ear, yin from Summer Solstice to Major Snow, and the ju (1 to 9) comes from the term and yuan by the method you choose.
- **Plates.** The earth plate lays out 戊己庚辛壬癸丁丙乙 from the ju palace. The duty star (值符) moves to the palace of the hour stem and carries the other stars and their stems around with it, with Tian Qin travelling alongside Tian Rui. The duty door (值使) moves one palace per hour from the start of the hour's decade. The eight deities follow the duty star, clockwise in yang escapement and counter-clockwise in yin.
- **You and the matter.** Your palace is where the day stem sits on the heaven plate (marked 我), and the matter's palace is where the hour stem sits (marked 事). A Jia stem is read through the stem that hides it.

## Reading the chart

**The strip above the board** shows the four pillars, the solar term and yuan, the escapement and ju, the method and time basis, the duty star and door, and the hour's void branches.

**Each palace** shows its trigram, its door in large type, then the star, the deity, and the heaven-plate stem over the earth-plate stem. Harm, death and fear doors appear in red. Select any palace to open its full reading: what the door, star and deity mean, how they work together, whether the palace strengthens or presses the door, its stem formation, any clashes, and an overall lean.

**Marks** in the corner of a palace:

| Mark | Meaning |
| --- | --- |
| 空 Void | The void (Kong Wang) branches of the hour's decade fall here. What sits here may be hollow or fail to deliver. |
| 馬 Horse | The Travelling Horse (Yi Ma). Sudden acceleration, travel or an urgent catalyst. |
| 沖 Clash | The palace opposite the hour branch, or a heaven stem clashing the earth stem beneath it (Jia–Geng, Yi–Xin, Bing–Ren, Ding–Gui). |
| 刑 Strike | A ceremonial stem is struck and punished here (六儀擊刑). |
| 迫 Pressed | The door's element overcomes the palace (門迫), weakening it. |
| 格 Formation | A favorable heaven-over-earth formation. Every palace has a formation from the table of 81, but only the favorable ones are marked on the board. |

The reading also notes when the day and hour clash or punish each other (Zi–Mao, Yin–Si–Shen, Chou–Xu–Wei and the self-punishing branches), and flags fu yin (伏吟) and fan yin (反吟).

**The verdict** comes from the element relationship between your palace and the matter's palace:

| Relationship | Verdict |
| --- | --- |
| The matter feeds you (生) | Strong advantage: go ahead |
| Same element (比) | Stable, peer alignment |
| You feed the matter (生) | Resource drain: proceed with discipline |
| You restrain the matter (剋) | Uphill effort: hold the reins yourself |
| The matter restrains you (剋) | High obstacle: pause or change course |

Notes underneath add anything that changes the picture, such as the matter's palace being void, carrying the Horse, or holding an adverse formation.

## Print or PDF brief

**Print or save as PDF** under a reading produces a monochrome one-page A4 brief. It includes the question and time, the four pillars and ju, the verdict, the full nine-palace grid, the reading notes and any journal outcome. Choose "Save as PDF" in the print dialog to archive it.

## Journal

**Save to journal** keeps a reading with its time, question, verdict, your palace, the matter's palace and door, and the calculation settings. Later, record whether it turned out as read, partly or not, and add notes. The journal summary tallies outcomes so you can see how readings hold up over time. **Open chart** brings back the exact chart with the settings it was cast with.

The journal is stored in your browser on this device only. Use **Export journal** to save it as JSON and **Import journal** to restore it or move it to another browser.

## Accuracy and limits

This is one standard school of hour-chart Qimen. Schools differ on the ju method, the time basis, the day boundary, deity names and the wording of the formations, so a chart here may not match every almanac or app. The zhi run method in particular varies between teachers in how it starts the count and when it repeats a term. For a chart cast within a few minutes of a solar term boundary, check it against a full almanac.

The formation names follow the common 十干克應 lists. The meanings and verdicts are short summaries of traditional associations. Treat the chart as a prompt for reflection, not as professional advice.

## Customising

Everything lives in `qimen-oracle.html`:

- **Colors and fonts** are CSS variables at the top of the `<style>` block (`--paper`, `--ink`, `--cinnabar`, `--indigo` and so on).
- **The engine** is in the `<script id="engine">` block and has no dependency on the page, so you can load it in Node or reuse it elsewhere. `castChart(date, { method, basis, longitude, horseFrom })` returns the full chart.
- **Meanings** for doors, stars, deities and formations are in `DOORS`, `STARS`, `DEITIES` and `PATTERN_LIST`.
- **Verdict wording** is in `evaluateRelationship()`.

## Accessibility

Each palace is a keyboard-operable button with a full text description for screen readers. Focus is visible, animations are turned off when reduced motion is requested, and the layout adapts down to phone width.

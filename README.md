# Hi Combo print cost calculator

A single-file, offline-friendly calculator for working out what a 3D print on
a Creality Hi Combo actually costs — electricity, filament and machine wear —
and turning that into a selling price for a batch of parts.

No build step, no dependencies. Open `index.html` in a browser and it runs.

## Usage

Open `index.html` directly, or serve it locally:

```sh
python3 -m http.server 8080
```

then visit `http://localhost:8080`.

Your inputs are saved to `localStorage`, so the page remembers your last job
between visits. Use **Reset to Hi Combo defaults** to start over.

## What it calculates

- **Print job** — duration and filament used for one piece (copy these
  straight from the slice estimate in Creality Print), currency, and a
  material preset (PLA, Hyper PLA, PETG, ABS, ASA, PLA-CF) that fills in
  typical spool cost, power draw and wear rate.
- **Running costs** — your electricity tariff, the printer's average power
  draw, spool cost/weight, and an optional wear-and-tear rate per print hour
  (nozzles, plates, belts, fans, PTFE tubes).
- **Batch & pricing** — number of pieces required for the quotation, and the
  profit margin to sell at.

## Output

- **Cost breakdown** — electricity, material and maintenance cost for a
  single piece, shown as a pie chart with a per-item breakdown.
- **Pricing & spools** — totals for the whole batch: how many filament spools
  the job needs (with a fill chart), a cost-vs-profit bar for the per-piece
  sell price, and the batch's total cost, profit and selling price.

## Notes

- The Hi Combo's 1150 W rating is the AC bed at full power during warm-up;
  once at temperature the average draw is far lower. Defaults assume ~140 W
  for PLA. For an accurate figure, measure a print with a plug-in energy
  meter and enter its average wattage.
- Material preset prices are in Indian rupees and converted to other
  currencies at approximate fixed rates — only used when you apply a preset.

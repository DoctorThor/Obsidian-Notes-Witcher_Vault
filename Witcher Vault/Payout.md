<%*
/*
Witcher Contract Payout Calculator
Uses:
- Base Tier Value (in Crowns)
- Party Size
- Average Party Level
- Difficulty
- Region
- Haggling (%)

Formula:
Final Payout = Base × PartyMod × LevelMod × DiffMod × RegionMod × (1 + Haggling%)
*/

// 1. Get base tier value
const baseInput = await tp.system.prompt("Base tier value in Crowns (e.g. 150)");
const base = parseFloat(baseInput || "0");

// 2. Party size → Party Mod
const partySizeInput = await tp.system.prompt("Party size (number of PCs)");
const partySize = parseInt(partySizeInput || "1");

let partyMod = 1.0;
if (partySize <= 1) partyMod = 1.0;
else if (partySize === 2) partyMod = 1.2;
else if (partySize === 3) partyMod = 1.5;
else if (partySize === 4) partyMod = 1.8;
else partyMod = 2.0;

// 3. Level → Level Mod
const levelInput = await tp.system.prompt("Average party level");
const level = parseInt(levelInput || "1");

let levelMod = 1.0;
if (level <= 3) levelMod = 0.8;
else if (level <= 6) levelMod = 1.0;
else if (level <= 10) levelMod = 1.2;
else if (level <= 14) levelMod = 1.4;
else levelMod = 1.6;

// 4. Difficulty → Diff Mod (use suggester)
const diffOptions = [
  "Slightly Harder (×1.1)",
  "Hard (×1.25)",
  "Deadly (×1.5)",
  "Extremely Deadly (×2.0)",
  "Normal (×1.0)"
];
const diffChoice = await tp.system.suggester(diffOptions, diffOptions, false, "Choose difficulty");
let diffMod = 1.0;
if (diffChoice.startsWith("Slightly")) diffMod = 1.1;
else if (diffChoice.startsWith("Hard (×1.25)")) diffMod = 1.25;
else if (diffChoice.startsWith("Deadly")) diffMod = 1.5;
else if (diffChoice.startsWith("Extremely")) diffMod = 2.0;
else diffMod = 1.0;

// 5. Region → Region Mod
const regionOptions = [
  "Velen (×0.8)",
  "Novigrad / Oxenfurt (×1.0)",
  "Redania (×1.1)",
  "Skellige (×1.3)",
  "Nilfgaard (×1.2)",
  "Toussaint (×1.4)",
  "Custom (manual multiplier)"
];
const regionChoice = await tp.system.suggester(regionOptions, regionOptions, false, "Choose region");

let regionMod = 1.0;
let regionLabel = regionChoice;

if (regionChoice.startsWith("Velen")) regionMod = 0.8;
else if (regionChoice.startsWith("Novigrad")) regionMod = 1.0;
else if (regionChoice.startsWith("Redania")) regionMod = 1.1;
else if (regionChoice.startsWith("Skellige")) regionMod = 1.3;
else if (regionChoice.startsWith("Nilfgaard")) regionMod = 1.2;
else if (regionChoice.startsWith("Toussaint")) regionMod = 1.4;
else {
  const regInput = await tp.system.prompt("Custom region multiplier (e.g. 1.15)");
  regionMod = parseFloat(regInput || "1.0");
  regionLabel = `Custom (×${regionMod})`;
}

// 6. Haggling (%)
const haggleInput = await tp.system.prompt("Haggling (% modifier, e.g. 0, 10, -10)");
const hagglePercent = parseFloat(haggleInput || "0");
const haggleMod = 1 + (hagglePercent / 100);

// 7. Compute payout
let payout = base * partyMod * levelMod * diffMod * regionMod * haggleMod;
let rounded = Math.round(payout);

// 8. Output nicely
-%>

### 🧾 Contract Payout (Calculated)

- **Base Tier Value:** `<%= base %>₡`
- **Party Size:** `<%= partySize %>` → **Party Mod:** `×<%= partyMod %>`
- **Average Level:** `<%= level %>` → **Level Mod:** `×<%= levelMod %>`
- **Difficulty:** `<%= diffChoice %>` → **Diff Mod:** `×<%= diffMod %>`
- **Region:** `<%= regionLabel %>` → **Region Mod:** `×<%= regionMod %>`
- **Haggling:** `<%= hagglePercent %>%` → **Haggling Mod:** `×<%= haggleMod.toFixed(2) %>`

**Final Payout:** `≈ <%= rounded %>₡`

> Formula: `Final = Base × Party × Level × Difficulty × Region × Haggling`
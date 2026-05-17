---
type: weapon            # optional, just for your reference
base: 250               # base price in Crowns before modifiers
region: Skellige        # Velen / Novigrad / Redania / Skellige / Nilfgaard / Toussaint
quality: fine       # crude / standard / fine / mastercrafted / relic
rarity: rare          # common / uncommon / rare / very_rare
for: sell               # "sell" = NPC selling to PCs (shop price)
                        # "buy"  = NPC buying from PCs (loot sale)
vendor_rate: 0.4        # optional: how much vendors pay when buying from PCs
---
```dataviewjs
// ===============================
// Witcher Item Price Calculator
// ===============================
//
// Uses fields in the current note:
// base        -> base Crowns price (number)
// region      -> Velen / Novigrad / Redania / Skellige / Nilfgaard / Toussaint
// quality     -> crude / standard / fine / mastercrafted / relic
// rarity      -> common / uncommon / rare / very_rare
// for         -> "sell" (shop price to PCs) or "buy" (vendor buys from PCs)
// vendor_rate -> multiplier for vendor buying from PCs (default 0.4)
//
// Final price = base * regionMod * qualityMod * rarityMod
// If for == "buy": final = that * vendor_rate
//

const page = dv.current();

const base = Number(page.base ?? 0);

// ------------- Region Mods (from our economy) -------------
const regionMods = {
    "velen": 0.9,              // slightly cheaper goods (poor region)
    "novigrad": 1.0,
    "novigrad/oxenfurt": 1.0,
    "oxenfurt": 1.0,
    "redania": 1.0,
    "skellige": 1.2,
    "nilfgaard": 1.1,
    "toussaint": 1.3
};

let rawRegion = String(page.region ?? "Novigrad").toLowerCase();
let regionKey = rawRegion.replace(/\s+/g, ""); // handle "Novigrad / Oxenfurt" variants
if (regionKey === "novigrad/oxenfurt") regionKey = "novigrad/oxenfurt";

const regionMod = regionMods[regionKey] ?? 1.0;

// ------------- Quality Mods -------------
const qualityMods = {
    "crude": 0.75,         // rusted / junk
    "standard": 1.0,       // normal town-smith
    "fine": 1.25,          // good craft
    "mastercrafted": 1.5,  // witcher / dwarven / top tier
    "relic": 2.0           // legendary
};

const qualityKey = String(page.quality ?? "standard").toLowerCase();
const qualityMod = qualityMods[qualityKey] ?? 1.0;

// ------------- Rarity Mods -------------
const rarityMods = {
    "common": 1.0,
    "uncommon": 1.25,
    "rare": 1.5,
    "very_rare": 2.0,
    "very rare": 2.0
};

const rarityKey = String(page.rarity ?? "common").toLowerCase();
const rarityMod = rarityMods[rarityKey] ?? 1.0;

// ------------- Vendor rate (when selling to vendor) -------------
const vendorRate = page.vendor_rate !== undefined ? Number(page.vendor_rate) : 0.4;

// ------------- Calculation -------------
const mode = String(page.for ?? "sell").toLowerCase(); // "sell" => shop selling to PCs, "buy" => vendor buying from PCs

// Raw market value (what an item is "worth" in your economy)
let marketValue = base * regionMod * qualityMod * rarityMod;

// Price shown to PCs:
let priceToPCs;
let note;

if (mode === "buy") {
    // NPC buying from PCs – vendorRate cuts it down
    priceToPCs = marketValue * vendorRate;
    note = "Vendor buying this item from PCs (loot sale).";
} else {
    // Default: selling to PCs (shop price)
    priceToPCs = marketValue;
    note = "NPC shop selling this item to PCs.";
}

// Round for nice numbers
marketValue = Math.round(marketValue);
priceToPCs = Math.round(priceToPCs);

// ------------- Output -------------
dv.table(
    ["Field", "Value"],
    [
        ["Base Price", base + " ₡"],
        ["Region", `${page.region ?? "Novigrad"} (×${regionMod})`],
        ["Quality", `${page.quality ?? "standard"} (×${qualityMod})`],
        ["Rarity", `${page.rarity ?? "common"} (×${rarityMod})`],
        ["Market Value", marketValue + " ₡"],
        ["Mode", mode === "buy" ? "Vendor buys from PCs" : "Shop sells to PCs"],
        ["Vendor Rate", mode === "buy" ? vendorRate.toString() : "—"],
        ["Final Price to PCs", priceToPCs + " ₡"],
    ]
);

dv.paragraph("> " + note);
```


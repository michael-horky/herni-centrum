# Prompty pro generování PNG vrstev — Oblékání panenky

## Technické specifikace (platí pro VŠECHNY obrázky)

- **Rozměry:** 300 × 620 px
- **Pozadí:** průhledné (PNG s alfa kanálem)
- **Styl:** flat cartoon illustration, Barbie-like proporce, čisté okraje pro compositing
- **Panenka má hlavu v horní části** (střed hlavy ≈ y=90), ramena ≈ y=165, boky ≈ y=290, kolena ≈ y=430, chodidla ≈ y=565
- Hlava: elipsa cca 150×144 px, střed (150, 90)

---

## VLASY — BACK LAYER (`layers/hair-back/`)

> **Grayscale, průhledné pozadí.**
>
> ⚠️ **KRITICKÉ — nejčastější chyba:** Negeneruj siluetu celého těla ani šedou výplň těla/trupu.
> Nakresli **POUZE samotné vlasové prameny** (jako tenké pásy/stuhy), které se zobrazují za hlavou.
> Vše ostatní (obličej, krk, tělo, trup, ruce, nohy) musí být **100% průhledné**.
> Představ si to jako „jen vlasy na průhledném skle" — žádné pozadí, žádná výplň.
>
> Středně šedá = prostřední tón (hex #808080). Bez jakékoli barvy — čistě šedá škála.
> Okraje hladké (anti-aliased), ideální pro CSS filter tinting.

### Společný base prompt (přidat za každý):
```
300x620px PNG, FULLY transparent background, grayscale only (no color tones), flat cartoon illustration.
Draw ONLY the hair strands — thin ribbons/strips of hair. NO body silhouette, NO torso fill, NO gray fill anywhere except the actual hair.
The oval face area (centered at x=150 y=90, ~150px wide 144px tall) must be completely transparent — do not fill it.
Everything below the shoulders (below y=180) that is not actual hair strands must be transparent.
Hair is rendered as if it falls BEHIND the head. Smooth anti-aliased edges for compositing.
```

| Soubor | Popis vlasů (back layer) |
|--------|--------------------------|
| `01-long-loose.png` | Long straight hair hanging behind back, reaching to waist (~y=340), hair-back layer only (behind head and body) |
| `02-braid-shoulder.png` | Single braid starting at back of head, coming over right shoulder, hanging to chest level (~y=260) — show braid continuing behind right shoulder |
| `03-pigtails.png` | Two pigtails hanging behind shoulders, reaching chest (~y=230), symmetrical |
| `04-braids.png` | Two braids (copy/Zöpfe) hanging behind shoulders, reaching waist (~y=320), symmetrical |
| `05-medium.png` | Medium-length hair behind head, reaching shoulder blades (~y=210), slightly wavy |
| `06-bob.png` | Short bob behind head, hanging to chin level from back (~y=140), clean straight ends |
| `07-pixie.png` | Very short pixie cut — minimal back layer, just short hair at nape of neck (~y=120) |
| `08-bald.png` | Completely bald — empty image (no hair at all), transparent PNG |
| `09-bun.png` | Hair pulled up into bun on top of head — back layer shows hair gathered upward, bun visible above head (~y=20), small flyaways |
| `10-double-bun.png` | Two space buns on top of head — back layer shows hair parted and pulled to two buns at sides of crown |
| `11-afro.png` | Large afro puff — back layer shows the round afro silhouette behind head, very voluminous, extends ~40px past head on all sides |
| `12-curly-long.png` | Long curly/wavy hair behind back, reaching waist (~y=340), loose curls, lots of volume |
| `13-mohawk.png` | Shaved sides mohawk — back layer minimal (shaved sides), just a thin strip of hair at nape |
| `14-princess.png` | Princess updo — back layer shows hair swept up from sides toward crown, elaborate curls/waves behind head |
| `15-headband.png` | Simple hair worn down with headband — back layer same as 01-long-loose but with a hair accessory band visible at top (~y=70) |
| `16-fairy-braid.png` | Long fairy-tale braid down the back, decorated with small flower details, reaching to lower back (~y=380) |
| `17-punk.png` | Punk/edgy style — short spiky back, shaved nape, possibly asymmetrical |

---

## VLASY — FRONT LAYER (`layers/hair-front/`)

> **Grayscale, průhledné pozadí.**
>
> ⚠️ **KRITICKÉ — nejčastější chyba:** Prostor uvnitř vlasů (obličej, čelo, tváře) musí být **100% průhledný**.
> Negeneruj tmavou/černou výplň uvnitř vlasové siluety — to by zakrylo SVG obličej.
> Nakresli **POUZE vlasové prameny** (ofina, prameny po stranách obličeje). Prázdný prostor = průhledný.
>
> Stejná šedá škála jako back layer.

### Společný base prompt:
```
300x620px PNG, FULLY transparent background, grayscale only (no color), flat cartoon illustration.
Draw ONLY the hair strands/bangs that hang IN FRONT of the face — just thin ribbons/strips of hair.
The face interior (the space inside the hair frame) must be 100% TRANSPARENT — do NOT fill it with any color.
No silhouette mask. No background fill. Think of it as individual hair strands floating on transparent canvas.
Only the hair strands themselves are opaque gray; everything else is transparent.
Smooth anti-aliased edges for compositing.
```

| Soubor | Popis vlasů (front layer) |
|--------|---------------------------|
| `01-long-loose.png` | Front face-framing strands of long straight hair, middle part, strands draping over front of shoulders |
| `02-braid-shoulder.png` | Single braid coming over right shoulder in front, visible from collar to chest; wispy side strands framing face |
| `03-pigtails.png` | Two front hair sections parted in middle, leading to pigtails; short flyaways around face |
| `04-braids.png` | Two front sections parted in middle leading to braids; clean part visible on top of head |
| `05-medium.png` | Front face-framing waves/strands, medium-length hair curling around jaw line |
| `06-bob.png` | Bob front layer — smooth sections framing face, clean chin-length bob sides visible |
| `07-pixie.png` | Short wispy fringe/bangs, pixie front pieces framing forehead, very short |
| `08-bald.png` | Empty transparent PNG |
| `09-bun.png` | Hair bun front layer — smooth forehead, possibly wispy baby hairs framing face, bun detail on top |
| `10-double-bun.png` | Two space buns clearly visible in front/top of head (spherical bun shapes ~30px diameter each), baby hairs |
| `11-afro.png` | Afro front — the afro puff extends in front above forehead, rounded silhouette sides visible |
| `12-curly-long.png` | Curly front strands framing face, ringlets pulling forward over shoulders |
| `13-mohawk.png` | Mohawk front — dramatic spiky strip running from forehead to crown, tall (~40px above head), the characteristic mohawk fan shape |
| `14-princess.png` | Elaborate front updo — barrel curls, decorative waves framing face, swept-back sides |
| `15-headband.png` | Bangs/fringe in front, headband visible across forehead (y≈70), two thin band strips going over head |
| `16-fairy-braid.png` | Fairy braid front — braided crown section across forehead, small flower/star decorations, front tendrils |
| `17-punk.png` | Punk front — dramatic spiky fringe or asymmetrical side sweep, bold shape above forehead |

---

## OBLEČENÍ — OUTFIT LAYER (`layers/outfit/`)

> **Plná barva, průhledné pozadí.** Outfit zakrývá tělo od krku (≈y=155) po chodidla (nebo krátší).
> Musí mít průhlednou oblast pro hlavu, krk, ruce a (většinou) nohy.
> Styl: flat cartoon, čisté barvy, cartoon shading.

### Společný base prompt:
```
300x620px PNG, transparent background, flat cartoon illustration style, Barbie-like doll outfit,
female figure proportions: shoulders at y≈165, waist at y≈255, hips at y≈290, knees at y≈430, feet at y≈565.
Head area (oval centered at 150,90) is transparent. Arms extend outward from shoulders.
Clean edges, cartoon shading, vibrant colors.
```

| Soubor | Outfit |
|--------|--------|
| `01-elsa.png` | Elsa (Frozen) ice queen dress — light blue/cyan sparkly floor-length gown with cape, snowflake details, off-shoulder |
| `02-anna.png` | Anna (Frozen) dress — teal/magenta folk-inspired bodice with black corset, teal skirt with floral embroidery |
| `03-snowwhite.png` | Snow White dress — yellow skirt, blue bodice with white collar, red bow at neck, short puffy sleeves |
| `04-cinderella.png` | Cinderella ball gown — light blue/silver voluminous floor-length ball gown with puff sleeves, glitter |
| `05-aurora.png` | Sleeping Beauty Aurora dress — pink floor-length gown with pointed fairy sleeves, jewel neckline |
| `06-shirt-skirt.png` | Casual: white short-sleeve fitted T-shirt tucked into pastel floral A-line mini skirt (reaches ~y=370) |
| `07-shirt-jeans.png` | Casual: colorful graphic fitted T-shirt with light blue skinny jeans reaching to ankles (~y=555) |
| `08-shirt-shorts.png` | Summer casual: crop tank top, high-waisted denim shorts reaching mid-thigh (~y=350) |
| `09-summer-dress.png` | Flowy spaghetti-strap summer dress, floral print, midi length (~y=450), light and breezy |
| `10-hoodie.png` | Cozy: pastel oversized hoodie with kangaroo pocket, matching jogger sweatpants, cuffed at ankles |
| `11-bikini.png` | Swimwear: colorful bikini top (triangles) and bikini bottoms, summery pattern (polka dots/tropical) |
| `12-swimsuit.png` | One-piece swimsuit — vibrant color with fun print (stars/stripes), sporty or cute style |
| `13-ski.png` | Ski suit — one-piece or two-piece neon ski jacket + ski pants, boots integrated, winter sporty |
| `14-pyjamas.png` | Pajamas — cute printed PJ set: long-sleeve top with stars/moon/animals print + matching pants |
| `15-tutu.png` | Ballet tutu — fitted ballet leotard (pink/lavender) with multi-layer tutu skirt sticking out (~40px), ballet tights |
| `16-witch.png` | Witch costume — black/purple witch dress with jagged hem, striped tights, collar detail (hat added by SVG acc layer) |
| `17-pirate.png` | Pirate costume — white puffy shirt, dark vest, striped capri pants, belt with buckle (hat added by SVG acc layer) |
| `18-astronaut.png` | Astronaut suit — white spacesuit with NASA-style patches, helmet ring at neck, gloves, suit details |
| `19-doctor.png` | Doctor/nurse outfit — white lab coat over blue scrubs, stethoscope around neck, coat pockets |
| `20-queen.png` | Royal queen gown — deep red/purple velvet floor-length gown, gold trim, ermine collar (crown added by SVG acc layer) |
| `21-clown.png` | Clown costume — oversized colorful polka-dot jumpsuit, ruffled collar, rainbow buttons (red nose added by SVG acc layer) |
| `22-tank-leggings.png` | Athleisure: fitted colorful tank top + high-waisted patterned leggings reaching ankles |

---

## BOTY — SHOES LAYER (`layers/shoes/`)

> **Plná barva, průhledné pozadí.** Boty jsou umístěné ve spodní části obrázku.
> Chodidla panenky ≈ y=555–575. Boty by měly být viditelné jen ve spodní části plátna.
> Styl: flat cartoon, odpovídá stylu outfitů.

### Společný base prompt:
```
300x620px PNG, transparent background, flat cartoon illustration style, shoes/footwear only,
positioned at the very bottom of the canvas — two feet side by side centered at approximately 
x=122 (left foot) and x=178 (right foot), top of shoes at approximately y=545, soles at y=580.
Legs/ankles visible just above. Clean edges, cartoon shading.
```

| Soubor | Boty |
|--------|------|
| `00-barefoot.png` | Bare feet — no shoes, just cartoon bare feet with toenails, skin-neutral (will match SVG skin via leg layer) — actually transparent/empty, the SVG legs already show feet |
| `01-sneakers.png` | White/colorful sneakers/trainers with colored laces and sole stripe, sporty style |
| `02-heels.png` | Classic pointy-toe high heels (stilettos), neutral nude or black, elegant |
| `03-ballet-flat.png` | Flat ballet flats/ballerinas, pink or nude, small bow on toe |
| `04-pointe.png` | Ballet pointe shoes — satin pink pointe shoes with ribbons lacing up ankles (~y=510) |
| `05-cowboy.png` | Cowboy boots — leather cowboy boots reaching to mid-calf (~y=490), decorative stitching |
| `06-wellies.png` | Rubber rain boots/wellies — shiny colorful rubber boots reaching to knee (~y=440), fun print |
| `07-sandals.png` | Summer flat sandals with ankle straps, colorful with small flower/gem decoration |
| `08-bunny-slipper.png` | Bunny slippers — fluffy white/pink slippers with bunny ears and face on toes, cozy |
| `09-clown-shoes.png` | Clown shoes — exaggeratedly long oversized red/yellow pointy clown shoes, very wide |
| `10-rollerskates.png` | Roller skates — high-top boot rollerskates with 4 wheels, colorful with toe stop |
| `11-ski-boots.png` | Ski boots + skis — rigid plastic ski boots with skis extending out below (skis reach beyond canvas edge) |
| `12-flippers.png` | Swim flippers — large rubber dive flippers, neon green/yellow, extending forward |
| `13-snowshoes.png` | Snowshoes — wide oval snowshoe frames attached to winter boots, wooden/metal frame style |
| `14-cleats.png` | Soccer/football cleats — sporty athletic cleats with colored laces, grip studs on sole |
| `15-pink-boots.png` | Pink knee-high fashion boots — shiny pink boots reaching to knee (~y=440), fashionable |
| `16-paw-slippers.png` | Animal paw slippers — fluffy slippers shaped like animal paws (bear/cat/dog), with claw details |

---

## Poznámky pro generování

1. **Vrstva hair-back** musí mít průhlednou oblast TAM, kde bude obličej/tělo — generuj jen vlasovou část za hlavou
2. **Vrstva hair-front** zobrazuje jen ofinu a prameny PŘED obličejem — obličej sám musí zůstat průhledný
3. **Barefoot (`00-barefoot.png`)** — může být prázdné průhledné PNG, chodidla jsou součástí SVG těla
4. **Příslušenství** (čarodějnický klobouk, pirátský klobouk, koruna, klaun nos) jsou přidány dynamicky přes SVG acc vrstvu — v PNG outfitu je nekreslíme
5. **Konzistence stylu** — všechny obrázky musí vypadat jako součást jedné sady (stejný cartoon styl, similar line weight)
6. **Testování filtrů vlasů** — po vygenerování prvních hair PNG spusť hru a zkontroluj, jestli CSS filtry sedí. Filtry jsou v `HAIRS[]` v `index.html` a možná bude třeba je doladit.

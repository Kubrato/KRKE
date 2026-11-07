# Turkish tales: source notes (Step 1)

Detailed notes behind the 🇹🇷 column of [tales-list.md](tales-list.md).
Researched by Kübra, November 2026.

## The main source

**Wolfram Eberhard & Pertev Naili Boratav, *Typen türkischer Volksmärchen*** ("Types of Turkish Folktales").
Wiesbaden: Franz Steiner, 1953. German, XI + 506 pages.

- It is a **catalogue**, not a story book. The authors grouped many Turkish folktales into **types** with their own numbers (**TTV** numbers).
- For each type the book gives: **I. Motivreihe** (main story, step by step), **II. Belege** (list of recorded versions, with the place), **III. Varianten** (differences), **IV. Erweiterungen** (extensions), **V. Bemerkungen** (remarks).
- **Free digital copy (PDF, 734 MB):** https://opendata.uni-halle.de/handle/1981185920/36665 (DOI: 10.25673/36433). Open it in a normal browser; the site blocks automatic tools.
- The PDF is a scan, so **text search does not work**. Use the "Typ …" at the top corner of the pages.

### How to read a source reference ("Beleg")

Page 423 lists the handwritten collections in Boratav's folklore archive in Ankara.
Example: *Ankara 32,3 (Ankara)* = collection "Ankara 32", tale no. 3, recorded in Ankara.
Names in capitals (KÚNOS, TEZEL, MAHIR …) are printed books.

### The Aarne → TTV table (pp. 421–422)

The book ends with a table that matches the international numbers (old Aarne system, 1928) to TTV numbers. The authors list a match "only where a real correspondence seems to exist".

| Aarne (≈ ATU) | TTV | Our tale type | Checked? |
|---|---|---|---|
| 310 | Anl. C 12 | Rapunzel | ✅ fits |
| 408 | 89 | Three Oranges | not yet read |
| 425 | 98 | Lost Husband | not yet read |
| 480 | – | Kind & Unkind Girls | no match in table → **our** match: TTV 59 |
| 503 | 118 | Hunchback | ✅ fits |
| 510 | 60 | Cinderella | ✅ fits |
| 545B | 34 | Puss in Boots | ✅ fits |
| 700 | 288 | Tom Thumb | ✅ fits |
| 707 | 239 | Three Golden Children | not yet read |
| 709 | 167, Anl. A b | Snow White | ✅ fits |
| 1640 | 330 | Brave Little Tailor | ❌ **does not fit** (see below) |
| 410 | – | Sleeping Beauty | no Turkish version |

### Page photos

Photos of all pages we used are in `docs/sources/eberhard-boratav-1953/` (file names start with the page number, e.g. `p067_TTV60_cinderella.png`).
⚠️ The book is still **in copyright**, so these photos are **not uploaded to GitHub** (they are in `.gitignore`). Ask Kübra if you need them, or open the free PDF at the page number.

---

## 1. Cinderella (ATU 510A) → TTV 60 *Aschenbrödel* / *Kül kedisi*

- **Pages:** 67–69 · photos `p067_…`, `p068-069_…`
- **Story:** A stepmother treats her stepdaughter badly. A **cow** helps the girl. While the others are at a wedding, the girl gets beautiful clothes from the cow and goes too, but leaves before the others. She **loses a shoe**; the prince searches for its owner and finds her at the stepmother's house. They marry.
- **Versions:** 22 (İstanbul, Ankara, Adana, Erzurum, Erzincan, İzmit, Iğdır, İzmir …). Example: N. Tezel, *İstanbul*, pp. 51–57.
- **Variants:** the cow is killed and its **buried bones** help her; a fish she saved helps her; the dead mother gives advice; she must **sort mixed grains**; the party is a **circumcision feast**; the prince throws a golden ball to choose a bride; a **rooster** tells the prince where she is hidden.
- **Remark (p. 69):** "The Turkish name is *kül kedisi* (ash-cat). Despite the similarity to the European tale, direct influence through translated literature seems excluded."
- **Extra (≈):** TTV 189 *Tülüce* (pp. 218–220, 21 versions), a "Donkeyskin" tale (ATU 510B). In 2 versions the test object is a shoe.

## 2. Kind and Unkind Girls (ATU 480) → TTV 59 *Das Katzenhaus* (The Cats' House)

- **Pages:** 65–67 · photos `p065_…`, `p066-067_…`
- **Story:** A poor girl comes to a house of cats, treats them well and gets a gift. An evil woman copies her, treats the animals badly and dies.
- **Versions:** 31 (İstanbul, Ankara, İzmir, Bursa, Konya, Niğde, Mersin, Nevşehir, Erzurum, Kars …). Example: Kúnos, pp. 69–74 (Adakale).
- **Variants:** she follows a rolling cake or a ball of yarn; the magic being is an old woman, a giantess, a fairy or three riders; she **combs the old woman's hair**; she spits gold; washing in a magic stream makes her beautiful; the bad girl gets a **sack of snakes and scorpions**. On p. 137 the helper is the *Çarşamba cadısı* (Wednesday witch).
- **Remark:** often joined to the start of TTV 60 (Cinderella).
- ⚠️ The catalogue's table does **not** list 480 → 59. **We** made this match, because the plot is the ATU 480 pattern.

## 3. Gifts of the Little People (ATU 503) → TTV 118 *Die Buckligen* (The Hunchbacks)

- **Pages:** 136–137 · photo `p136-137_…`
- **Story:** A hunchbacked woman is locked in the **hamam** by mistake and sees dwarfs dancing at night. She sings with them "Wednesday, Wednesday…" and they take away her hump. Another hunchbacked woman "corrects" the song with "Thursday…" and gets the first one's hump too.
- **Versions:** 3 (Kastamonu, İstanbul ×2). Example: *Ankara 17,4*, collected by Muazzez Görkey.
- **Remark:** Wednesday is an unlucky day in Turkish belief.

## 4. Tom Thumb (ATU 700) → TTV 288 *Däumling*

- **Pages:** 332–333 · photo `p332-333_…`
- **Story:** A childless woman gets many children **as small as peas** and throws them into the fire; one escapes. He sits in the **donkey's ear** and brings food to his father. He is buried in cow dung and burnt when the dung is used as fuel.
- **Versions:** 11 (Develi, Edirne, İstanbul, Kastamonu, Gümüşhane, Afyon …). Example: *Afyon 1,14* (Yazılıkaya).
- **Variants:** names *Bizdan*, *Cücan*; **swallowed by a cow** or a hen; robbers use him; **a wolf eats him** and starves because he shouts.
- **Remark:** a Kalmyk parallel exists.
- **Related:** *Nohut Oğlan* (Boratav, pp. 272–276 of a 2016 edition), probably the same type.

## 7. Brave Little Tailor (ATU 1640) → *Kara Mustafa the Hero* (no TTV)

- **Source:** Ignác Kúnos, *Forty-four Turkish Fairy Tales* (1913). Text: https://sacred-texts.com/asia/ftft/ftft09.htm
- ❌ The table says 1640 → TTV 330, but **TTV 330 (pp. 364–365) is a different story** (a fool kills the Ağa's cattle, 1 version from Bayburt). Probably a mistake in the table.
- **To do:** read Kara Mustafa and check the "flies / many at one blow" motif.

## 9. Puss in Boots (ATU 545B) → TTV 34 *Der Müller und der Fuchs* (The Miller and the Fox)

- **Pages:** 49–51 · photo `p049_…`
- **Story:** A fox helps a poor miller, calls him the "Dust Padishah", wins him a princess and takes a palace from giants. At the end the fox **plays dead**; the miller throws the body away, so the fox shows his ingratitude.
- **Versions:** 15 (Hasanoğlan, İstanbul, Çankırı, Ankara, Mersin, Artvin, Manisa, Zonguldak …).
- **Best example:** variant j, V. Mahir, pp. 71–73: the youngest of three sons gets **only a cat**, like the European tale.

## 10. Rapunzel (ATU 310) → *Gülümser* (appendix C 12)

- **Page:** 418 · photo `p418-419_…`
- **Source:** Mehmet Tuğrul (Boratav's student), village Mahmut-Gazi (Çal, Denizli). Only summarised in the appendix.
- **Story:** A peri kidnaps Gülümser and keeps her in a house with no door and no stairs in the sea. The peri **climbs up her hair**. The Ant-Padishah climbs up the same way; Gülümser drives the peri away with *özerlik* (rue) water and marries him.
- **Versions:** 1, so the type seems rare in Turkey.

## 11. Sleeping Beauty (ATU 410) → not found

No match in the table, no type in the book. Probably a mostly European tale.

## 12. Snow White (ATU 709) → TTV 167 *Nar tanesi* (Pomegranate Seed)

- **Pages:** 185–187 · photos `p185_…`, `p186-187_…`
- **Story:** The stepmother asks **the Moon** who is the most beautiful. She makes the girl swallow snakes so she looks pregnant, and the father sends her away. The girl lives with **forty robbers**. The stepmother brings **poisoned cherries**, then another poisoned thing; the robbers put her in a coffin; a prince takes the coffin, the poison is removed, and they marry.
- **Versions:** 15 (İstanbul, Konya, Sivas, Nevşehir, Kars, Erzincan, Kastamonu, Rize, Malatya). Example: *Ankara 1325,2* (Konya).
- **Variants:** a **mirror** (*ayna*) instead of the Moon (*ay*); **seven brothers or dwarfs**; a **poisoned apple**; she wakes when the coffin is shaken. Names: *Nardaniye*, *Dürdane*.
- **Remark (p. 187):** very similar to Snow White, but a recent borrowing from Europe is unlikely.
- **Appendix A (p. 411):** a separate *Schneewittchen und die sieben Zwerge* came from European books. The authors did not count it as a folk tale.

## Rows 5, 6, 8 (found earlier, from other sources)

| Tale type | Turkish tale | Source | TTV |
|---|---|---|---|
| 5 Three Oranges (408) | *The Three Orange-Peris* | Kúnos 1887 | 89 (pages not read yet) |
| 6 Golden Children (707) | *The Golden-Haired Children* | Kúnos 1899 | 239 (pages not read yet) |
| 8 Lost Husband (425A) | *Sabırtaşı* | Eflatun Cem Güney 1947 | 98 (pages not read yet) |

## Other sources used

- Wikipedia: [The Princess in the Suit of Leather](https://en.wikipedia.org/wiki/The_Princess_in_the_Suit_of_Leather) (TTV 189), [Puss in Boots](https://en.wikipedia.org/wiki/Puss_in_Boots) (TTV 34), [The Stone of Patience](https://en.wikipedia.org/wiki/The_Stone_of_Patience_(Turkish_folktale)) (TTV 98)
- Nohut Oğlan: [REF/JEF 2025 article](https://academiaromana.ro/ief/rev/REF2025/DOI/06.pdf)
- Kara Mustafa: [Sixty at a Blow (1968)](https://www.biblioguides.com/pub/book/sixty-at-a-blow-a-tall-tale-from-turkey-1968)

## Still to do

- [ ] Read TTV 89, 98, 239 (rows 5, 6, 8) for the number of versions and places
- [ ] Read *Kara Mustafa* (row 7)
- [ ] Choose 2–3 unique Turkish tales (ideas: Keloğlan and the Hoca's Daughter, appendix C 13; *Ayı kulak*, appendix C 3)

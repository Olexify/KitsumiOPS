# Kitsumi word packs (Advanced scanning)

Downloaded by the Kitsumi browser extension only when a user installs one in
the Dict tab (Advanced scanning). Each file is a gzip'd list, one word form per
line, `form<TAB>flags` - no definitions.

| File | Built from | Source version | Licence |
| :--- | :--- | :--- | :--- |
| scan-ja-1.tsv.gz | JMdict, by the Electronic Dictionary Research and Development Group (EDRDG) - https://www.edrdg.org/ | JMdict of 2026-09-26 | CC BY-SA 4.0 |
| scan-zh-1.tsv.gz | CC-CEDICT, published by MDBG - https://cc-cedict.org/ | CC-CEDICT of 2026-09-26 | CC BY-SA 4.0 |

These packs use the EDRDG dictionary files in conformance with the Group's
licence (https://www.edrdg.org/edrdg/licence.html) and CC-CEDICT under its
licence. Being derived from CC BY-SA works, the packs are shared under
**CC BY-SA 4.0** (https://creativecommons.org/licenses/by-sa/4.0/). No
copyright is claimed over the data itself.

`index.json` names the current version of each pack with its SHA-256; the
extension reads it to install the newest version and to offer updates (at most
weekly, only while a pack is installed).

## Flags (Japanese)

`1` ichidan verb, `5` godan verb, `k` 来る, `s` する verb, `z` ずる verb,
`i` i-adjective, `S` noun that takes する, `p` particle, `c` common form
(JMdict priority news1 / ichi1 / spec1 / spec2 / gai1).

## Updating (monthly)

The JMdict licence asks software that uses the data to keep it current. Once a
month:

1. Download the latest sources:
   - http://ftp.edrdg.org/pub/Nihongo/JMdict_e.gz
   - https://www.mdbg.net/chinese/export/cedict/cedict_1_0_ts_utf-8_mdbg.txt.gz
2. `node tools/packs/build-ja.js JMdict_e.gz` and
   `node tools/packs/build-zh.js cedict_1_0_ts_utf-8_mdbg.txt.gz`
   (in the Kitsumi development folder). A changed pack gets the next version
   number and a new file (`scan-ja-2.tsv.gz` ...); an unchanged one is left
   alone.
3. Upload the new `.tsv.gz` file(s) and `index.json` here, and update the
   "Source version" dates above. Keep the older files - older Kitsumi builds
   still know them.

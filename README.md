# sources-tn

Original county election result documents from Tennessee, kept exactly as the counties published them, with original filenames preserved.

Tennessee's Secretary of State publishes statewide and federal results. County commission, school board, sheriff, trustee and the other county offices are published only by the ninety five county election commissions, in whatever form each county chose. This repository is those documents.

## What is here

**382 documents from 78 of Tennessee's 95 counties, plus 4 feed captures from 4 more.** `manifest.csv` lists every one with its
source URL, the date it was retrieved, and a SHA-256 you can check against the file.

Files are organised by **election**, because that is what people come here looking for:

```
<year>/<election-date>/<county>/<the county's own filename>
feed-captures/<election-date>/<county>/    not a published file, see below
```

So Tennessee's August 2026 election is one place, `2026/2026-08-06/`, holding 23 counties and
73 files, rather than scattered across 23 county folders. Nine documents carry no readable
election date and sit under `date-unknown/`.

Filenames are the county's own, never renamed, with one exception described under feed captures below. Where a county's URL carries no usable name,
the county's own label for the document is used instead: Cumberland publishes through Google
Drive, so all 24 of its files would otherwise be called `uc.pdf`, and they are named for the
precincts the county itself named them after.

**Looking for one county rather than one election?** `manifest.csv` has a `county` column, and
a `repo_path` column pointing at every file.

## Feed captures, which are not documents

**Three things here are not files any county published, and they are kept apart from the ones that
are.** Some counties post no results file at all. They run a results page backed by a live endpoint,
and what we can keep is our own dated capture of what that endpoint answered when we asked.

**Davidson County (Nashville), Shelby County (Memphis) and Montgomery County are all of this kind.**

They are hashed and citable exactly like everything else, and they are marked three ways so nothing
can mistake one for a document the county published:

- they live under `feed-captures/`, never in the dated document tree
- `manifest.csv` carries an **`artefact_kind`** column, which reads `feed-capture` rather than
  `document`
- the `flags` column says so in words on every one of them

**One thing genuinely differs, and it is the reason for the separation.** A published file is a thing
a county made and posted, and it is the same object tomorrow. An endpoint answers differently on
Tuesday than it did on Monday, and it can stop answering without anyone deciding to withdraw
anything. **So a feed capture is evidence about an instant, and `retrieval_date` carries far more
weight in those rows than it does in a document's.**

**A filename in these rows is ours, not the county's.** Everywhere else the original filename is
preserved, because how a county named its file tells you something about how it was produced. Our
Davidson capture is called `election-returns.xml` after a segment of the endpoint we queried.
**Nashville did not name it, and nothing should be read from it.**

**This is not a criticism of those counties.** Publishing results through a live page is a normal
and reasonable thing for a county to do, and in some ways it serves the public better than a scan.
It simply means "what the county published" has no fixed answer, and we would rather say so than
pretend otherwise.

### What the `status` column means, all five values

**No document here is `certified`.** Certified would mean we hold the certification document
itself. We hold none, so that value appears zero times.

| value | count | meaning |
|---|---:|---|
| `unknown` | 111 | the document says nothing about its status, or nothing readable |
| `election_night` | 15 | the document says it is unofficial |
| `official_claimed` | 12 | **the document** calls itself official. That is the county's claim, not our verification |
| `certified_claimed` | 1 | the document says it is certified. Again its claim, and we have not seen the certificate |
| `n/a` | 3 | not a results document |

**A claim is only ever read from the document's own first page, never from its filename.**
Four documents were downgraded to `unknown` for precisely this reason: their filenames say
official or certified while the page itself yields no text at all. One is literally named
`Certified Results (County Election) August 6, 2026`. By the standard above, a certification
claim read off a filename is the weakest possible version of the thing that standard exists to
prevent. The `flags` column records what each filename said.

### How much of this is scanned, stated plainly

This repository's value is that you can check it, so you should know what we could not read.

**109 of the 382 documents are scans with no embedded text layer.** Of those, most were read by
OCR. **11 of the 382 yield no text by any means**, native or OCR, and every one of those carries
`unknown` status by construction.

Of the 28 documents that do carry a status claim, **12 are scans whose text came from OCR**, and
**none rests on a page nobody could read**.

**Three of the 382 are not results** and are marked `not-results` in `document_kind`: a
redistricting notice, a daily ballots-cast tally sheet, and an early-voting totals sheet. They
are here because the county published them. Turnout and correspondence are not results.

**78 of 95 is what we have retrieved, not what Tennessee publishes.** A county absent from this
repository is almost always one whose page we have not yet fetched.

Built by [Out of Many. Us](https://outofmany.us).

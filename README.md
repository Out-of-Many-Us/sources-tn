# sources-tn

Original county election result documents from Tennessee, kept exactly as the counties published them, with original filenames preserved.

Tennessee's Secretary of State publishes statewide and federal results. County commission, school board, sheriff, trustee and the other county offices are published only by the ninety five county election commissions, in whatever form each county chose. This repository is those documents.

## What is here

**124 documents from 29 of Tennessee's 95 counties.** `manifest.csv` lists every one with its
source URL, the date it was retrieved, and a SHA-256 you can check against the file.

Files are organised as `counties/<county>/<election-date>/source/`, keeping the county's own
filename. Nine documents carry no readable election date and sit under `date-unknown`.

**No document here is labelled certified.** Certified means we hold the certification document,
not that the report has the word OFFICIAL printed on it. Where we have not seen the
certification, the manifest says `unknown` and the `flags` column says why.

**Three of the 124 are not results** and are marked `not-results` in `document_kind`: a
redistricting notice, a daily ballots-cast tally sheet, and an early-voting totals sheet. They
are here because the county published them. Turnout and correspondence are not results.

**29 of 95 is what we have retrieved, not what Tennessee publishes.** A county absent from this
repository is almost always one whose page we have not yet fetched.

Built by [Out of Many. Us](https://outofmany.us).

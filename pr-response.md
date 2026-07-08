# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->

## Comment 1 — Rename

**What I did:** in `watchlist_service.py`, I found `save_to_watchlist` and right
click → "Go to References" to find all references, and I renamed the function
name and all its references to `add_to_watchlist`.

**How I verified:** a project-wide search of `save_to_watchlist` returns no
result.

## Comment 2 — Deduplication

**What I did:** in `collection_service.py`, I found the logic that handled
duplication and copied that block of code along with the Exception it raised to
`add_to_watchlist` in `watchlist_service.py`, then I rewrote the names and
strings so they describe watchlists instead of collections.

**How I verified:** a search of "collection" in `watchlist_service.py` returns
no results that needed to be renamed. the model for `WatchlistEntry` has the
same `user_id` and `film_id` fields as `CollectionEntry`, so the arguments
passed into `filter_by` can remain the same. functionality check is implemented
in the next commit.

## Comment 3 — Missing test

**What I did:** I copied all tests from `test_collection.py` to
`test_watchlist.py` and rewrote all the collection references to watchlist.

**How I verified:** all testcases for both collection and watchlist passes,
except the one that tests watchlist order, which will be handled in a later fix.

## Comment 4 — Default visibility
**My position:**
**Reasoning:**
**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**
**Reasoning:**
**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->
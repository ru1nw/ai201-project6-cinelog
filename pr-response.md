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

**My position:** `public=True` is an intentional choice that aligns with the
purpose of the program.

**Reasoning:** `public=True` default allows the user and anyone who wants to
learn more about the user a chance to view their watchlist. this system is
designed to be a community, and defaulting to public is important to facilitate
conversation.

**Tradeoff acknowledged:** some users might want some or all entries on their
watchlist be private, and that requires an extra step.

## Comment 5 — Sort order

**My position:** alphabetical order is easier to find a specific entry

**Reasoning:** as the list of entries grows, it will quickly become unmanagable
to skim through the list and quickly find an entry. alphabetical order makes
searching an entry for a specific movie easier, as not everyone remember when
they watched it.

**Engagement with reviewer's point:** ordering by recency is easier when looking
for a recently watched movie, which might be useful in some cases, but
alphabetical order is a more convenient choice for users in the long run.

## Comment 6 — Rebase

**What conflicted:**

-   the .gitignore in the main branch conflicted with the newly added one in
    feature branch from milestone 1
-   `WatchlistEntry` in `models.py` was removed after rebase

**How I resolved it:**

-   I chose the .gitignore from the main branch as it also ignored
    `.pytest_cache/`
-   added `WatchlistEntry` back

**How I verified no conflict remains:** no conflict markers remain, and all
testcases pass

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->
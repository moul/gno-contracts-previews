# gno-contracts-previews

Static [gnoweb](https://gno.land) snapshots of [moul/gno-contracts](https://github.com/moul/gno-contracts),
served from the `gh-pages` branch at <https://moul.github.io/gno-contracts-previews/>.

| Path | What |
|---|---|
| `main/` | every package on `gno-contracts@main`, rebuilt on every push there |
| `pr-<N>/` | what pull request N changed, plus every package that imports it |

**Nothing here is hand-written and nothing here should be edited.** The branch is rewritten as a
single orphan commit on every publish, so the repository only ever holds the site as it is now
rather than every version it has ever had. A commit you add by hand is gone at the next push.

Both are produced by `gnocontracts preview` in the contracts repository
(`tools/gnocontracts/preview.go`), which boots `gnodev` on the workspace and crawls the result.
The snapshots are `noindex, nofollow`: every page is a near-duplicate of a real gno.land page.

Each snapshot is a fresh local chain that has only ever run `init()`. Transactions, the faucet
and search do not work, and a link that leaves the snapshot goes to the live site.

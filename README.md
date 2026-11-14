# gno-contracts-previews

Static [gnoweb](https://gno.land) snapshots of [moul/gno-contracts](https://github.com/moul/gno-contracts),
served from the `gh-pages` branch at <https://moul.github.io/gno-contracts-previews/>.

| Path | What | Rebuilt |
|---|---|---|
| `main/` | every package on `gno-contracts@main` | every push there |
| `pr-<N>/` | what pull request N changed, plus every package that imports it | every push to the PR |

## Retention

A pull request keeps its preview for **21 days after it closes**. Its bot comment embeds the
before/after screenshots by URL, so deleting on the close event would leave every merged pull
request with a comment full of broken images.

An hourly job is the only thing that removes anything. It drops previews past that grace period,
and if the site is still over its size budget it gives up the closed ones early, oldest first.
**A preview of an open pull request is never removed**, whatever the budget says.

## Nothing here is hand-written

The branch is rewritten as a single orphan commit on every publish, so the repository only ever
holds the site as it is now rather than every version it has ever had. A commit you add by hand
is gone at the next push.

Both snapshots come from `gnocontracts preview` in the contracts repository
(`tools/gnocontracts/preview*.go`), which boots `gnodev` on the workspace and crawls the
result. Every page is `noindex, nofollow`: each is a near-duplicate of a real gno.land page.

Each snapshot is a fresh local chain that has only ever run `init()`. Transactions, the faucet
and search do not work, and a link that leaves the snapshot goes to the live site.

# License Management For xmidt-org

Generally there are two things we need to do to maintain the licenses used by
the software provided by the xmidt-org:

1. Add licenses that the [licensed](https://github.com/github/licensed) tool
   misses/can't understand to the list of identified & already approved licenses.
2. Add new licenses to the list of approved licenses.

## Updating an unidentified license

Generally the build breaks due to a new license like [this.](https://github.com/xmidt-org/scytale/runs/8076991426?check_suite_focus=true#step:9:12)

```
Checking cached dependency records for scytale
...............................................................................
.......................................................F.......................
...............................................................................
...............................................................................
.............
Errors:
 * scytale.go.github.com/miekg/dns
  filename: /home/runner/work/scytale/scytale/.licenses/go/github.com/miekg/dns.dep.yml, version: v1.1.50, license: other, allowed: false
false
    - license needs review: other


329 dependencies checked, 1 errors found.

Licensed found errors during source enumeration.  Please see https://github.com/github/licensed/tree/master/docs/commands/status.md#status-errors-and-resolutions for possible resolutions.
```

In this case the `github.com/miekg/dns` code license wasn't understood.  So the
next thing to do is to go examine the license(s) in that [project](https://github.com/miekg/dns).

In this case, the [LICENSE](https://github.com/miekg/dns/blob/master/LICENSE) is
a `3-clause-bsd` license.

So the next step is to open a PR against the [org-approved.yml](https://github.com/xmidt-org/.github/blob/main/licensing/org-approved.yml) file.

Add this repository (following the instructions in the file).  **NOTE:** you should only be
approving and referencing licenses found under the `allowed` section.  Other licenses
need to be reviewed more thoroughly.

[Here is the PR from our example.](https://github.com/xmidt-org/.github/compare/add-license?expand=1)

## Adding a new license type

The process is much the same as above, except the license is added to the `allowed`
list.  These need review from the org administrator as we need to ensure our
software meets the licensing guidelines we have.

## Repro

Repro for: https://github.com/foundry-rs/foundry/issues/7225

- Run `forge install uniswap/v3-core@0.8`

No [Github tag](https://github.com/Uniswap/v3-core/tags) of 0.8 exists, this should refer to the `0.8` branch.

Yields:

```
Installing v3-core in /home/zerosnacks/Projects/counter/lib/v3-core (url: Some("https://github.com/uniswap/v3-core"), tag: Some("0.8"))
Cloning into '/home/zerosnacks/Projects/counter/lib/v3-core'...
remote: Enumerating objects: 8244, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 8244 (delta 0), reused 2 (delta 0), pack-reused 8240
Receiving objects: 100% (8244/8244), 6.37 MiB | 7.58 MiB/s, done.
Resolving deltas: 100% (6277/6277), done.
    Installed v3-core 0.8
```

`.gitmodules` contains (no `path` specified):

```
[submodule "lib/v3-core"]
	path = lib/v3-core
	url = https://github.com/uniswap/v3-core
```

Note that it correctly installs the `0.8` branch at this point but does not specify the path in `.gitmodules`.

This causes issues when a user now runs `forge update` where it resets to `master`, making it incompatible with a `0.8` codebase.
I remember running into this, resolving it by manually adding the branch in the `.gitmodules` file.

To retry this yourself from the start:

- Run `forge install uniswap/v3-periphery@0.8`

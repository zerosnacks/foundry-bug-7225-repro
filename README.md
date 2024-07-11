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

`.gitmodules` contains:

```
[submodule "lib/v3-core"]
	path = lib/v3-core
	url = https://github.com/uniswap/v3-core
```

Without a path specified.

This causes issues when a user now runs `forge update`.

To retry this yourself from the start:

- Run `forge install uniswap/v3-periphery@0.8`

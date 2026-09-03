# tl_openthread_libs

Prebuilt OpenThread libraries for Telink platforms, consumed as a Zephyr module.

> [!WARNING]
> ## Renamed repository — do NOT recreate the old name
>
> This repository was renamed from **`telink-semi/openthread_telink_lib`** to **`telink-semi/tl_openthread_libs`**.
>
> **Do NOT create a new repository named `openthread_telink_lib` under the `telink-semi` account.**
>
> GitHub serves automatic 301 redirects from the old URL to this repository **only while the old name remains unclaimed**. Claiming the old name with any new repository would permanently break:
>
> - every historical link in documentation and release notes still pointing at the old URL,
> - `git fetch` / `west update` in existing workspaces whose west manifest is pinned to the old URL,
> - the `origin` remotes of all existing clones and forks.
>
> If you need a repository under the old name for any reason, use a different account or a different name — never `telink-semi/openthread_telink_lib`.

> [!IMPORTANT]
> 中文提示：本仓库由 `openthread_telink_lib` 改名而来。请**不要**在 `telink-semi` 账号下新建名为 `openthread_telink_lib` 的仓库——否则 GitHub 的旧地址 301 重定向将失效，历史文档链接、已发布的 west manifest 及所有已存在克隆的 `origin` 远端都会断链。

## About this repository

- **Provenance:** an original Telink-maintained repository — not a fork of any upstream repository, and not a rebuilt copy. During the rename window it was first published under the new name as a mirror snapshot placeholder; after confirmation from the Thread Group, the original repository with its full commit history, branches and tags was renamed onto the name `tl_openthread_libs`. What you see here is that original repository under its new name.
- **Purpose:** hosts the prebuilt OpenThread libraries (`.a` archives under `lib/`) for Telink platforms, together with the `Kconfig` options and CMake glue needed to link them into Zephyr applications.
- **Produced by:** the `lib_builder` job of the Telink Zephyr SDK (`samples/net/openthread/lib_builder` in [`telink-semi/tl_zephyr`](https://github.com/telink-semi/tl_zephyr)); the job builds OpenThread for the supported Telink configurations and publishes its artifacts here.

## Using the module (west)

The module is pulled in through the Telink west submanifest. The west project **name** and the local checkout **path** are unchanged — only the repository **URL** changed:

```yaml
# submanifests/telink.yaml (telink-semi/tl_zephyr)
projects:
  - name: openthread_telink_lib                          # west project name (unchanged)
    url: https://github.com/telink-semi/tl_openthread_libs   # NEW URL after the rename
    revision: tags/v4.1.2
    path: modules/lib/openthread_telink_lib              # local path (unchanged)
```

After `west update`, the module registers as the Zephyr module `openthread_telink_lib` (see `zephyr/module.yml`) and links the prebuilt libraries selected through Kconfig (for example `libopenthread-ftd-extended.a`, `libopenthread-ftd-reduced.a`).

## Related repositories

| Repository | Role |
|---|---|
| [`telink-semi/tl_zephyr`](https://github.com/telink-semi/tl_zephyr) | Telink Zephyr SDK — west top-level manifest and the `lib_builder` job |
| [`telink-semi/tl_openthread`](https://github.com/telink-semi/tl_openthread) | OpenThread sources from which these libraries are built |
| [`telink-semi/tl_matter`](https://github.com/telink-semi/tl_matter) | Telink Matter SDK (formerly `connectedhomeip`) |
| [`telink-semi/tl_mcuboot`](https://github.com/telink-semi/tl_mcuboot), [`telink-semi/tl_xz`](https://github.com/telink-semi/tl_xz) | Other renamed Telink dependencies |

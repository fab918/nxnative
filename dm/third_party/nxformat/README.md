# nxformat reader

From https://github.com/fab918/nxformat, revision
`d40e62d978ee2cd1a1261415f59b5aa5302ccfe6` (1.0.2), `dist/`.
MIT; see LICENSE and the reader header's notice.

Only the C++17 archive reader and its pinned, positional disk source are
included. There is no writer, converter, Rust runtime or C API dependency.
`dm/tools/nx_reader.cpp` links the reader to Zstandard and supplies a bounded
read-only pipe protocol for `scripts/pack_nx.py` and the existing native NCA
reader. Blocks retain the upstream integrity checks and cache policy.

Local change: `Snapshot::icon_index` retains the already validated application
or metadata-history icon index, alongside the upstream `nacp_index`. This lets
an explicitly selected older version keep its own icon. There is no wire-format
or validation change.

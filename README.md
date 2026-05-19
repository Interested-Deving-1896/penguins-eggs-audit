# penguins-eggs-audit

Integration framework extending [Penguins-Eggs](https://gitlab.com/openos-project/penguins-eggs_deving/penguins-eggs)
with 39 git-based projects across 8 feature domains, with a focus on security auditing,
supply chain transparency, and OS hardening.

## Feature Domains

| Domain | Purpose | Key Projects |
|---|---|---|
| Distribution | ISO hosting & versioning | git-lfs, giftless, gogs |
| Decentralized | P2P ISO distribution via IPFS | brig, git-lfs-ipfs, ipgit |
| Config Management | Versioned wardrobe editing | presslabs/gitfs, dsxack/gitfs |
| Build Infrastructure | Reproducible, verified builds | system-transparency, BtrFsGit |
| Dev Workflow | CI/CD, security, automation | gitstream, frogbot, workflow-ts |
| Packaging | Installation & app distribution | gitpack, github-paser |
| Security & Audit | OS hardening, attestation, vulnerability scanning | vouch, OSs-security, ultimate-linux-suite |
| SBOM & Supply Chain | Software bill of materials generation and license compliance | syft, grant, SBOM-Generation |

## Documents

- [ARCHITECTURE.md](ARCHITECTURE.md) — System design and project mapping
- [INTEGRATION-SPEC.md](INTEGRATION-SPEC.md) — Per-integration specifications with CLI, config, and acceptance criteria
- [PROJECT-CATALOG.md](PROJECT-CATALOG.md) — All 39 projects with descriptions and links

## Implementation Phases

1. **Foundation** — git-lfs, gitpack, release downloader, selective wardrobe download
2. **Decentralized** — brig, git-lfs-ipfs, ipgit, git-ipfs-rehost
3. **Config Management** — gitfs variants, wardrobe merge tools
4. **Build Infrastructure** — system-transparency, BtrFsGit snapshots
5. **Dev Workflow** — gitstream, frogbot, TypeScript CI, developer tools
6. **Self-Hosted** — gogs registry, opengist sharing, giftless server
7. **Security & Audit** — vouch attestation, OS hardening, vulnerability scanning
8. **SBOM & Supply Chain** — syft SBOM generation, grant license compliance, SBOM-Generation reference implementations

## File Inventory

54 files total: 30 TypeScript modules, 8 shell scripts, 6 YAML configs, 4 docs, 6 other.

## Structure

```
penguins-eggs-audit/
├── README.md
├── ARCHITECTURE.md
├── INTEGRATION-SPEC.md
├── PROJECT-CATALOG.md
└── plugins/
    ├── distribution/
    │   ├── lfs-tracker/          # git-lfs ISO tracking + produce hook
    │   ├── gogs-registry/        # Docker Compose self-hosted registry
    │   └── opengist-sharing/     # wardrobe share/import via gists
    ├── decentralized/
    │   ├── brig-publish/         # IPFS distribution via brig
    │   ├── lfs-ipfs/             # git-lfs-ipfs transfer agent setup
    │   ├── ipfs-mirror/          # CI-driven IPFS repo mirroring
    │   └── ipgit-remote/         # git remote backed by IPFS
    ├── config-management/
    │   ├── wardrobe-mount/       # FUSE mount with auto-commit (gitfs)
    │   ├── wardrobe-browse/      # read-only revision browser
    │   ├── wardrobe-merge/       # merge multiple wardrobe repos
    │   └── wardrobe-read/        # programmatic API for wardrobe access
    ├── build-infra/
    │   ├── st-output/            # System Transparency boot artifacts
    │   └── btrfs-snapshot/       # BTRFS snapshots around produce
    ├── dev-workflow/
    │   ├── pr-automation/        # gitStream rules (.cm)
    │   ├── security-scan/        # Frogbot GitHub Action
    │   ├── ts-ci/                # TypeScript-defined CI workflows
    │   └── dev-tools/            # developer costume (lazygit, etc.)
    ├── packaging/
    │   ├── gitpack-install/      # .install/ for gitpack support
    │   ├── release-downloader/   # shell + oclif release downloader
    │   └── dir-downloader/       # selective wardrobe directory download
    ├── security-audit/
    │   ├── vouch-attest/         # cryptographic attestation via vouch
    │   ├── os-hardening/         # OS hardening scripts (OSs-security)
    │   └── linux-suite/          # unified Linux tooling (ultimate-linux-suite)
    └── sbom/
        ├── syft-generate/        # SBOM generation for ISO artifacts
        ├── grant-license/        # license compliance scanning
        └── sbom-reference/       # CISA SBOM generation reference workflows
```

## Origins

penguins-eggs-audit integrates 39 git-based projects. Key upstreams by domain:

**Distribution & Decentralized**
- [git-lfs/git-lfs](https://github.com/git-lfs/git-lfs) — ISO tracking via Git LFS
- [nicowillis/giftless](https://github.com/nicowillis/giftless) — self-hosted Git LFS server
- [gogs/gogs](https://github.com/gogs/gogs) — self-hosted Git registry
- [brig-ipfs/brig](https://github.com/sahib/brig) — IPFS-based distribution via brig
- [ipfs/go-ipfs](https://github.com/ipfs/go-ipfs) — IPFS node

**Config Management & Build**
- [presslabs/gitfs](https://github.com/presslabs/gitfs) — FUSE-mounted git repo for wardrobe editing
- [system-transparency/system-transparency](https://github.com/system-transparency/system-transparency) — reproducible verified builds

**Dev Workflow & Security**
- [linear-b/gitstream](https://github.com/linear-b/gitstream) — PR automation rules
- [jfrog/frogbot](https://github.com/jfrog/frogbot) — security scanning GitHub Action
- [anchore/syft](https://github.com/anchore/syft) — SBOM generation
- [anchore/grant](https://github.com/anchore/grant) — license compliance scanning

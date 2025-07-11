# Orbit

**Decentralized registry and Galaxy publisher for [Cosmos](https://github.com/yourname/cosmos)**

> Orbit is a tool for maintainers. It takes a Galaxy built by [Stellar](https://github.com/yourname/stellar) and publishes it as a signed, portable, decentralized registry — ready to be consumed by Cosmos.

---

## 🚀 What It Does

Orbit manages:

* ✅ Galaxy signing and registry index generation
* ✅ Decentralized publishing (USB, IPFS, Git, HTTP)
* ✅ Secure syncing and verification model
* ✅ Offline and airgapped compatibility

Orbit does **not** build Stars or handle package creation — that's Stellar's job.

---

## 🧩 Relationship to Cosmos and Stellar

| Tool    | Role      | Actions                           |
| ------- | --------- | --------------------------------- |
| Stellar | Builder   | Creates Stars and Galaxies        |
| Orbit   | Publisher | Signs, indexes, and publishes     |
| Cosmos  | Consumer  | Syncs Galaxies, installs packages |

* **Galaxies** are the format: directories of `star.toml`s and tarballs
* **Registries** are signed Galaxies managed by Orbit

---

## 📦 Install

```bash
cargo install --locked --git https://github.com/yourname/orbit
```

Or download a static binary from [Releases](https://github.com/yourname/orbit/releases)

---

## 📁 Example Workflow

### 1. Build your Galaxy with Stellar

```bash
stellar galaxy-init core/
stellar build-star hello
```

### 2. Initialize Orbit in your Galaxy

```bash
orbit init core/
```

### 3. Add packages to the registry

```bash
orbit add ./core/packages/hello-1.0.0.tar.gz
```

### 4. Publish to a destination

```bash
orbit publish ./core/ --to /mnt/usb
orbit publish ./core/ --to git@github.com:user/core-galaxy.git
```

---

## 🔐 Trust Model

* All registries are signed (GPG or minisign)
* Clients (Cosmos) verify signatures before using any metadata or tarballs
* You can configure pre-trusted keys or use trust-on-first-use

---

## 🌍 Syncing

Orbit registries can be consumed by Cosmos from:

* File paths (USB, NFS, etc.)
* HTTP(S)
* Git repositories
* IPFS (planned)

---

## 🧱 Orbit Registry Layout

```txt
core/
├── packages/
│   └── hello-1.0.0.tar.gz
├── stars/
│   └── hello.toml
├── meta.toml
├── registry.toml          <- Registry index
├── signatures/
│   └── index.sig       <- Signed by maintainer
```

---

## 🧪 Roadmap

* [ ] Initial Release
* [ ] Web UI browser for offline registries
* [ ] Registry merge (`orbit combine`)
* [ ] Built-in diff / changelog viewer
* [ ] TUF-style threshold signatures
* [ ] LAN discovery via Avahi/Bonjour

---

## 📜 License

MIT. Built by and for people who believe static binaries, cryptographic trust, and minimalism aren’t mutually exclusive.

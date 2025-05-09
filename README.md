# qretina

**Install with your eyes.**

`qretina` is an offline-first bootloader that reconstructs full binary applications from a stream of QR codes. Designed for air-gapped systems, rescue utilities, and viral app distribution, `qretina` makes it possible to transfer complete executables without a network, just by pointing a camera at a QR stream.

---

## 🚀 Features

* **QR stream decoding** — Reads sequences of QR codes in real time
* **Binary reassembly** — Reconstructs original payloads (e.g. `.apk`, `.exe`, `.zip`, `.wasm`, etc.)
* **Offline operation** — Requires no internet, Bluetooth, or Wi-Fi
* **Tiny loader** — Minimal bootloader footprint, fast startup
* **Progressive loading** — Supports chunked QR sequences for large files
* **Integrity check** — Ensures correctness before execution or export

---

## 📦 Use Cases

* Bootstrapping devices in isolated or air-gapped environments
* Emergency delivery of critical software (e.g. firmware, antivirus, recovery tools)
* Viral, peer-to-peer software sharing without infrastructure
* Educational tools for decentralized app distribution
* QR-based NFT or digital collectible installation

---

## 🔧 How It Works

1. A source device encodes a binary file into a series of QR codes.
2. The target device runs `qretina`, which scans and tracks the stream.
3. Once all segments are received and verified, the binary is reassembled.
4. The app is saved or optionally executed (configurable).

---

## 📐 Payload Schema (JSON)

Each QR code must contain a JSON object with the following structure:

```json
{
  "id": "<unique-transfer-id>",
  "total": <number-of-chunks>,
  "index": <chunk-index>,
  "data": "<base64-encoded-chunk>",
  "hash": "<sha256-of-chunk>"
}
```

### Field descriptions:

* `id`: A UUID or unique identifier for the full payload.
* `total`: Total number of QR segments in the transfer.
* `index`: Zero-based index of this QR chunk.
* `data`: Base64-encoded binary fragment.
* `hash`: SHA-256 hash of the decoded chunk to ensure integrity.

> All QR codes in a transfer must share the same `id` and include all chunks from `index = 0` to `total - 1`.

---

## 🧪 Status

> `qretina` is currently in **alpha**. We're testing performance on Android and Linux platforms, with planned support for WebAssembly and low-end microcontrollers.

---

## 📜 License

MIT License (see `LICENSE` file).

---

## 🧠 Credits

Brought to life by minds obsessed with alternative computation, air-gap hacks, and turning cameras into data ports.

---

## ✨ Tagline ideas

* "Software, seen. Not downloaded."
* "From QR to code. No wires, no web."
* "Air-gap bootstrapping through vision."
* "qretina: a retinal stream for digital payloads."

---

## 📸 Demo (Coming Soon)

> Watch a full binary executable reconstructed from a QR stream — no network, no pairing, no problem.

---

## 🤝 Contributions

Open to issues, ideas, and pull requests. Help shape the future of visual software delivery!

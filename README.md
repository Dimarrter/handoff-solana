# HandOff

A receipt for the version you sent. Solana devnet MVP for student project handovers.

HandOff computes a file's SHA-256 fingerprint in the browser, creates a portable JSON receipt and lets a reviewer check whether a received file has the same contents. File bytes never leave the device.

## Try the core workflow

Open the app, choose **Use a sample file**, and download the receipt. In **Verify a handover**, load the receipt with the original file and compare. The matching and changed-file examples also work without a wallet. Local receipts never claim a blockchain timestamp.

## Materials

- [Pitch deck, eight slides](HandOff-pitch.pdf)
- [Pitch video draft](HandOff-pitch.mp4)
- [Demo video draft](HandOff-demo.mp4)
- [Complete source project](HandOff-project.zip)
- [Pitch subtitles](HandOff-pitch.srt) and [demo subtitles](HandOff-demo.srt)

The videos use synthetic English narration and actual prototype screens. They do not imitate the participant's voice or simulate a successful blockchain transaction.

## Solana integration

An injected compatible wallet can sign a transaction containing `handoff:v1:sha256:<digest>` in the existing SPL Memo program on **devnet**. Only after confirmation does the app export an anchored receipt. The verifier independently checks the successful transaction, exact memo and signing wallet. Filename and local date remain untrusted convenience metadata.

Devnet only. No tokens, transfers, escrow or mainnet transactions. Test SOL has no monetary value. A receipt does not prove authorship, originality, ownership, teacher acceptance or permanent storage.

## Validation

Four automated test groups pass: the SHA-256 `abc` vector, changed content, malformed receipts and transaction inspection failures. Browser checks cover sample creation and a complete export/import comparison with both original and edited files. A real wallet transaction remains untested. The optional devnet smoke test stopped when the faucet returned an internal error.

The competition requires Noah AI. The authenticated Noah account currently has zero generation credits and blocks the build. Noah integration remains pending. This repository must not be represented as a completed Noah-built competition entry yet.

## Source and local use

This repository's root contains the deployable static app. `HandOff-project.zip` contains the maintainable source, lockfile, tests, build script and local server.

Extract the archive, open its `project/` directory and run:

```sh
node server.mjs
```

Open http://127.0.0.1:4173. To change the app, use Node.js 20 or newer:

```sh
npm ci
npm test
npm run build
```

## References

[Official SPL Memo documentation](https://www.solana-program.com/docs/memo)

[IFK UNI Vibeathon requirements](https://superteam.fun/earn/listing/develop-solana-web3-project-mvp-and-pitch-for-ifk-uni-vibeathon)

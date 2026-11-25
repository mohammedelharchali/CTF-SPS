# 🔐 Symbolic Vault

**Category:** Reverse Engineering / Symbolic Execution  
**Difficulty:** Medium–Hard  
**Flag format:** `SIS{...}`

> The vault takes one passphrase. It hides it behind a small virtual machine of its own,
> and its guards don't take kindly to tools that try every path.
> Find the passphrase that opens it. **The passphrase is the flag.**

## Files

| File | Description |
|------|-------------|
| `vault` | Linux x86-64 ELF, stripped |

SHA-256: `77c121291b91c09d7a76c6695cdb06797b523ebb0fc97ae844b8b34d6819e194`

## Running it

```bash
chmod +x vault
./vault
```

```
=== SYMBOLIC VAULT ===
Enter the passphrase: hunter2
ACCESS DENIED.
```

## Rules

- Everything you need is in the binary. There is no server.
- Brute force won't work (the passphrase is 32 characters).
- Please don't post the flag in the group chat. Send it to the authors privately.

## Hints (open only if stuck)

<details>
<summary>Hint 1</summary>

Look at what `main` checks, in order. Some checks give a lot of information away for free.
</details>

<details>
<summary>Hint 2</summary>

You *could* reverse the VM by hand… or you could let a tool reason about it for you.
`angr` and `z3` are both fair game.
</details>

<details>
<summary>Hint 3</summary>

If your angr script never ends, look at its active states. Which function is making them multiply,
and do you really need angr to explore every path through it?
</details>

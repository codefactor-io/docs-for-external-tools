Pattern: Crypto Miner Detected

Issue: -

## Description

A file matches a cryptomining signature from the bundled YARA rules: the stratum mining protocol, known mining pool domains, two or more miner names (xmrig, ethminer, ...), or browser cryptojacking scripts (CoinHive, CryptoLoot, WebAssembly miners). The message names the matching YARA rule.


Example of **insecure** code:

```text
./xmrig -o stratum+tcp://pool.minexmr.com:4444 -u WALLET
```

## Further Reading

* [YARA documentation](https://yara.readthedocs.io/)
* [Neo23x0 signature-base](https://github.com/Neo23x0/signature-base)

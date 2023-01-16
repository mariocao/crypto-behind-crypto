# crypto-behind-crypto

This table is based on research at SEDA Protocol for assessing which cryptographic primitives are most widely used by blockchain protocols.

The following table includes the chains with the most-wide adoption or  significant TVL (Total Value Locked). Items are displayed in alphabetical order (market cap or TVL metrics change abruptly with time).

The main conclusions are:
- Most platforms use the same cryptographic primitives as Ethereum and Bitcoin.
- The most widely-used signing algorithm is ECDSA with the curve `secp256k1`.
- Relatively newer protocols use EdDSA with `curve25519`. 
- Hashing algorithms vary depending the desired chain interoperability.
- Most widely-used hashing algorithm is `keccak256`.
- Aggregate signature schemes are only supported by EVM-compatible chains with the curve `bn256` (aka `alt-bn128`).
- Support to aggregate signature schemes based on newer curves such as `bls12-381` are almost non-existent.


## Data

| Name      	| Symbol 	| Type    	| Signing Algorithm     	| Signing Default Curve                 	| Signing Supported Curves 	| Hash Default Alg.        	| Supported Hash Alg.                	| Aggregate Signatures 	| Address Encoding          	| Address Hash                                                  	|
|-----------	|--------	|---------	|-----------------------	|---------------------------------------	|--------------------------	|--------------------------	|------------------------------------	|----------------------	|---------------------------	|---------------------------------------------------------------	|
| Acala     	| ACA    	| account 	| ECDSA, Schnorr, EdDSA 	| curve25519, ristretto25519, secp256k1 	|                          	| blake2b                  	| sha2-256, ripemd-160               	| bn256                	| SS58 (~base58)            	| none                                                          	|
| Algorand  	| ALGO   	| account 	| EdDSA                 	| curve25519                            	| secp256k1                	| sha-256                  	| sha3-256, keccak-256*, sha-512/256 	|                      	| base32                    	| none                                                          	|
| Avalanche 	| AVAX   	| utxo    	| ECDSA                 	| secp256k1                             	|                          	|                          	| keccak-256*                        	| bn256                	| bech32 +  none (just hex) 	| sha-256, ripemd-160 +  last 20 bytes of Keccak-256* (C-CHAIN) 	|
| Bitcoin   	| BTC    	| utxo    	| ECDSA                 	| secp256k1                             	|                          	| sha-256, ripemd-160      	|                                    	| n/a                  	| base58, bech32            	| sha-256, ripemd-160                                           	|
| Cardano   	| ADA    	| utxo    	| EdDSA                 	| curve25519                            	|                          	| blake2b                  	|                                    	|                      	| base58, bech32            	| none                                                          	|
| Cosmos    	| ATOM   	| account 	| ECDSA                 	| secp256k1                             	| (ed25519 consensus)      	| keccak-256*              	|                                    	| n/a                  	| bech32 (or hex)           	| last 20 bytes of Keccak-256*                                  	|
| EOS       	| EOS    	| account 	| ECDSA                 	| secp256k1                             	|                          	| sha-256                  	|                                    	|                      	| none                      	| none                                                          	|
| Ethereum  	| ETH    	| account 	| ECDSA                 	| secp256k1                             	|                          	| keccak-256*              	| sha2-256, ripemd-160, blake2b      	| bn256                	| none (just hex)           	| last 20 bytes of Keccak-256*                                  	|
| Mixin     	| XIN    	| utxo    	| EdDSA                 	| curve25519                            	|                          	| sha-512                  	|                                    	| n/a                  	| n/a                       	| n/a                                                           	|
| Monero    	| XMR    	| utxo    	| EdDSA, Bulletproofs   	| curve25519                            	|                          	| keccak-256*              	|                                    	|                      	| base58                    	| keccak-256*                                                   	|
| NEO       	| NEO    	| account 	| ECDSA                 	| secp256r1                             	|                          	| sha-256                  	|                                    	|                      	| base58                    	| sha-256, ripemd-160                                           	|
| Ontology  	| ONT    	| account 	| ECDSA                 	| secp256r1                             	|                          	| 3x sha-256               	|                                    	|                      	| base58                    	| sha-256, ripemd-160                                           	|
| Polkadot  	| DOT    	| account 	| ECDSA, Schnorr, EdDSA 	| curve25519, ristretto25519, secp256k1 	|                          	| blake2b                  	|                                    	| n/a                  	| SS58 (~base58)            	| none                                                          	|
| Solana    	| SOL    	| account 	| EdDSA                 	| curve25519                            	| secp256k1                	| sha-256                  	| blake3, keccak-256                 	| bn256                	| none                      	| none                                                          	|
| Stellar   	| XLM    	| account 	| EdDSA                 	| curve25519                            	|                          	| sha-256, sha-512         	|                                    	|                      	| base32                    	| none                                                          	|
| Tezos     	| XTZ    	| account 	| ECDSA, EdDSA          	| ed25519, secp256k1, secp256r1         	|                          	| blake2, sha-512 in EdDSA 	|                                    	|                      	| base58                    	| blake2                                                        	|
| Tron      	| TRON   	| utxo    	| ECDSA                 	| secp256k1                             	|                          	| sha-256                  	| sha2-256, ripemd-160, blake2b      	| bn256                	| base58                    	| last 20 bytes of Keccak-256*                                  	|
| Waves     	| WAVES  	| account 	| EdDSA                 	| curve25519                            	|                          	| blake2b256, keccak256*   	|                                    	| bn256, bls12-381     	| base58                    	| none                                                          	|
| XRP       	| XRP    	| account 	| ECDSA, EdDSA          	| secp256k1, curve25519                 	|                          	| sha-512Half              	|                                    	|                      	| base58                    	| first half of sha512                                          	|
| Zcash     	| ZEC    	| utxo    	| ECDSA, zk-SNARKs      	| secp256k1, Jubjub, bls12-381          	|                          	| sha-256                  	|                                    	|                      	| base58, bech32            	| sha-256, ripemd-160                                           	|

Notes:
- `keccak256*`: Ethereum uses KECCAK-256. It should be noted that it does not follow the FIPS-202 based standard (a.k.a SHA-3), which was finalized in August 2015. Many blockchain protocols use the same modified version as Ethereum.


### Other chains

Other protocols share the same characteristics as the main L1 chains:

| Name             	| Symbol 	| Same algorithms as... 	| Aggregate Signature 	|
|------------------	|--------	|-----------------------	|---------------------	|
| Acala            	| ACA    	| Polkadot              	| bn256               	|
| Arbitrum         	| -      	| Ethereum              	| bn256               	|
| Bitcoin Cash     	| BCH    	| Bitcoin               	| n/a                 	|
| Bitcoin SV       	| BSV    	| Bitcoin               	| n/a                 	|
| Boba Network     	| BOBA   	| Ethereum              	| bn256               	|
| BSC              	| BNB    	| Ethereum              	| bn256               	|
| Celo             	| CELO   	| Ethereum              	| bn256               	|
| Cronos           	| CRO    	| Cosmos                	| ?                   	|
| Dash             	| DASH   	| Bitcoin               	| n/a                 	|
| DefiChain        	| DFI    	| Bitcoin               	| n/a                 	|
| Ethereum Classic 	| ETC    	| Ethereum              	| bn256               	|
| Fantom           	| FTM    	| Ethereum              	| bn256               	|
| Fusion           	| SN     	| Ethereum              	| bn256               	|
| Gnosis           	| GNO    	| Ethereum              	| bn256               	|
| Harmony          	| ONE    	| Ethereum              	| bn256               	|
| Kava             	| KAVA   	| Cosmos                	| ?                   	|
| Klaytn           	| KLAY   	| Ethereum              	| bn256               	|
| Litecoin         	| LTC    	| Bitcoin               	| n/a                 	|
| Metis            	| METIS  	| Ethereum              	| bn256               	|
| Moonbeam         	| GLMR   	| Ethereum              	| bn256               	|
| Optimism         	| OP     	| Ethereum              	| bn256               	|
| Osmosis          	| OSMO   	| Cosmos                	| n/a                 	|
| Parallel         	| PARA   	| Polkadot              	| n/a                 	|
| Polygon          	| MATIC  	| Ethereum              	| bn256               	|


## Acknowledgements & References

 - [Best-of Crypto](https://github.com/LukasMasuch/best-of-crypto)
-  [Cryptography behind top 20 cryptocurrencies by Tomas susanka](https://github.com/tsusanka/coins-cryptography)
-  [Cryptography behind the top 100 cryptocurrencies by Ethan Fast](http://ethanfast.com/top-crypto.html)


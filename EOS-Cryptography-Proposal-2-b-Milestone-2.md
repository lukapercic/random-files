# Milestone Delivery

**The [invoice form](https://forms.gle/wLuAzXKa9qYrZQob9) has been filled out correctly for this milestone and the delivery is according to the official [milestone delivery guidelines](https://github.com/eosnetworkfoundation/grant-framework/blob/master/docs/milestone-deliverables-guidelines.md).**  

* **Application Document:** https://github.com/eosnetworkfoundation/grant-framework/blob/main/applications/EOS-Cryptography-Proposal-2-b.md
* **Milestone Number:** 2
* **Milestone Payment Amount:** $32,000 USD
* **Contact Name:** Luka Percic
* **Contact email:** zeropass@pm.me

## Context
This delivery shows the power of ACK library and accelerated EC-based signature verification algorithms, by implementing the NIST and Brainpool curves. It also includes ECDSA key recovery from the signatures. 

## Deliverables
| Number | Deliverable | Link/Notes |
| -----: | ----------- | ------------- |
| 0a. | License | MIT |
| 0b. | Documentation | Documentation and step-by-step guide in [README.md](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/README.md).  | 
| 0c. | Testing Guide | [Section in the guide](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/README.md#algorithm-testing) |
| 0d. | Running it | We deployed on the [Jungle 4 testnet](https://jungle4.eosq.eosnation.io/account/helloeosiock) the [example contract](https://github.com/ZeroPass/ack/blob/b8d3ea841d32e1be372c36d0fb57785ec944a218/examples/helloack).|
| 1. | Antelope SDK library | Implementation of P-384, P-521 NIST curves |
| 2. | Antelope SDK library | Implementation of brainpoolP256r1, brainpoolP320r1, brainpoolP384r1, brainpoolP512r1 Brainpool curves |
| 3. | Antelope SDK library | Implementing ECDSA key recovery from signature |


#### Benchmark:
**Native**
|curve | recover | verify |
|------|---------|--------|
| brainpoolP256r1 | 1.631ms | 1.550ms|
| brainpoolP320r1 | 2.708ms | 2.460ms|
| brainpoolP384r1 | 4.060ms | 3.830ms|
| brainpoolP512r1 | 8.256ms | 7.697ms|
| secp256k1       | 0.794ms | 0.740ms|
| secp256r1       | 1.050ms | 1.030ms|
| secp384r1       | 2.110ms | 1.940ms|
| secp521r1       | 5.402ms | 4.920ms|


**WASM OC**
|curve | recover | verify |
|------|---------|--------|
| brainpoolP256r1 |  5.552ms - 6.3ms | 5.161ms - 5.5ms|
| brainpoolP320r1 |  8.191ms - 9.1ms | 8.189ms - 8.588ms|
| brainpoolP384r1 | 11.728ms - 17.364ms | 11.401ms - 15.157ms|
| brainpoolP512r1 | 22.604ms - 28.364ms | 18.626ms - 25.198ms|
| secp256k1       | 3.213ms - 3.883ms | 2.893ms - 4.2ms|
| secp256r1       | 3.960ms - 4.670ms | 3.664ms - 4.9ms|
| secp384r1       | 7.225ms - 8.798ms | 6.756ms - 7.743ms|
| secp521r1       | 18.032ms - 20.886ms | 16.012ms - 20.107ms|

*secp521r1 performance is lacking couse


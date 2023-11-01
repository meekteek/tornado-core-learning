## Details about zk proofs/validation/etc.

1. If someone has already withdrawn their eth share from the pool, it is possible to generate a new valid zk proof that passes but fails later at the smart contract layer.
   This occurs because the work from proof where nullifer hash will be generated as valid and merkletree check passes, the proof will be valid but once the smart contact looks at the
   generated nullifer hash, it will see that the proof simply proved that it knew the pre-image of the nullifier hash and there is no reason to allow another withdrawl.
   Because these proofs are not stateful, we turn to ethereum smart contracts to handle checking and ensuring no "replay-attack" withdraws occur

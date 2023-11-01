## Details about zk proofs/validation/etc.

1. If someone has already withdrawn their eth share from the pool, it is possible to generate a new valid zk proof that passes but fails later at the smart contract layer.
   This occurs because the work from proof where nullifer hash will be generated as valid and merkletree check passes, the proof will be valid but once the smart contact looks at the
   generated nullifer hash, it will see that the proof simply proved that it knew the pre-image of the nullifier hash and there is no reason to allow another withdrawl.
   Because these proofs are not stateful, we turn to ethereum smart contracts to handle checking and ensuring no "replay-attack" withdraws occur

2. It is possible to generate a valid zk proof that passes for a random root. The proof will show that you do know the secret to a leaf node for a given root, but because the root is not valid in      the context of the specified merkle tree representing the pool of money then the smart contract verifying will not do anything. the smart contract is stateful and knows that the proof is not        relevant in the context of the pool of money being requested so no funds will be transfered to the prover.


Given the outlined examples, it is clear that creating valid zk proofs is easy but creating valid zk proofs that will pass on the correct specific details that are outlined in the smart contract is only possible given the stringent conditions of who the prover is, whether they are owed funds from the pool, etc.

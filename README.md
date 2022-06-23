# dune-analytics-aztec-connect

A PostgreSQL abstraction to extract data from the `processRollup` operation.
The resulting structures looks like this:

### aztec_v2_proof_bridge_data_struct
```
type aztec_v2_proof_bridge_data_struct as (
  addressId numeric,
  inputAssetIdA numeric,
  outputAssetIdA numeric,
  inputAssetIdB numeric,
  outputAssetIdB numeric,
  auxData numeric,
  secondInputInUse boolean,
  secondOutputInUse boolean
);
```

### aztec_v2_inner_proof_data_struct
```
type aztec_v2_inner_proof_data_struct as (
  proofType text,
  noteCommitment1 bytea,
  noteCommitment2 bytea,
  nullifier1 bytea,
  nullifier2 bytea,
  publicValue numeric,
  publicOwner bytea,
  asset text
);
```

### aztec_v2_proof_data_struct
```
type aztec_v2_proof_data_struct as (
  rollupId numeric,
  rollupSize numeric,
  dataStartIndex numeric,
  oldDataRoot bytea,
  newDataRoot bytea,
  oldNullRoot bytea,
  newNullRoot bytea,
  oldDataRootsRoot bytea,
  newDataRootsRoot bytea,
  oldDefiRoot bytea,
  newDefiRoot bytea,
  bridges dune_user_generated.aztec_v2_proof_bridge_data_struct [],
  defiDepositSums numeric [],
  assetIds numeric [],
  totalTxFees numeric [],
  defiInteractionNotes bytea [],
  prevDefiInteractionHash bytea,
  rollupBeneficiary bytea,
  numRollupTxs numeric,
  innerProofs dune_user_generated.aztec_v2_inner_proof_data_struct []
);
```

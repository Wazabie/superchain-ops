# Validation

This document can be used to validate the state diff resulting from the execution of the upgrade transaction.

For each contract listed in the state diff, please verify that no contracts or state changes shown in the Tenderly diff
are missing from this document. Additionally, please verify that for each contract:

- The following state changes (and none others) are made to that contract. This validates that no unexpected state
  changes occur.
- All addresses (in section headers and storage values) match the provided name, using the Etherscan and Superchain
  Registry links provided. This validates the bytecode deployed at the addresses contains the correct logic.
- All key values match the semantic meaning provided, which can be validated using the storage layout links provided.

## State Changes

Note: The changes listed below do not include safe nonce updates or liveness guard related changes.

### `0x860e626c700AF381133D9f4aF31412A2d1DB3D5d` (`DisputeGameFactoryProxy`)

- **Key**: `0xffdfc1249c027f9191656349feb0761381bb32c9f557e01f419fd08754bf5a1b` <br/>
  **Before**: `0x0000000000000000000000000000000000000000000000000000000000000000` <br/>
  **After**: `0x000000000000000000000000e562e81d08cD5e212661EF961B4069456e426C56` <br/>
  **Meaning**: Updates the implementation for game type 0. Verify that the new implementation is set using
  `cast call 0x860e626c700AF381133D9f4aF31412A2d1DB3D5d "gameImpls(uint32)(address)" 0`.

### `0x89126a987717207d4E990ed2e8880fd170DceA1A` (`AnchorStateRegistryProxy`)

- **Key**: `0xa6eef7e35abe7026729641147f7915573c7e97b47efa546f5f6e3230263bcb49`<br/>
  **Before**: `0x0000000000000000000000000000000000000000000000000000000000000000` (Note this may have changed if games of this type resolved)<br/>
  **After**: `0x7b696e91aa7deb28d8891d32311930a10e3c05ee56a36ed1843def31bd2f8076` <br/>
  **Meaning**: Set the anchor state output root for game type 0 to 0x7b696e91aa7deb28d8891d32311930a10e3c05ee56a36ed1843def31bd2f8076.

- **Key**: `0xa6eef7e35abe7026729641147f7915573c7e97b47efa546f5f6e3230263bcb4a`<br/>
  **Before**: `0x0000000000000000000000000000000000000000000000000000000000000000` (Note this may have changed if games of this type resolved)<br/>
  **After**: `0x95a7f9` <br/>
  **Meaning**: Set the anchor state L2 block number for game type 0 to 9807865.

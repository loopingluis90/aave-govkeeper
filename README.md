# Aave GovKeeper

Aave Governance Keeper, to help on all phases of the Aave Governance proposals (AIPs). Based on OpenZeppelin Defender, this tool automatically performs governance actions so we can ensure proposals are successfully applied and do not get stale.

## Overview

Aave Improvement Proposals (AIPs) are governance proposals run by the Aave DAO. The Aave community vote on the AIPs to implement changes on the protocol. An AIP has multiple stages: Creation, Succeeded, Failed, Queued, Executed and Failed. A proposal needs to pass from one stage to another to get finally executed (and applied): Creation -> Succeeded -> Queued -> Executed. Once a proposal is successful, a function needs to be called to pass to Queued phase and finally to Executed. There is also other functions that need to be called across networks in case the AIP is multi-chain.

This is where the Keeper comes into play.

The Aave GovKeeper:

- Queues AIPs that are Succeeded
- Executes AIPs that are Queued and the delay has passed.
- Queues ActionsSet in the Governance Cross-chain Bridges.
- Executes ActionsSet in the Governance Cross-chain Bridges.
- Helps transactions to pass through bridges if needed (e.g. L1-L2).

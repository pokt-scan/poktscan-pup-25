# PUP-25: Non-Linear Stake Weighting For PIP-22

This repository contains the analysis behind the PUP-25 and all the data requiered to reproduce the publication results. 

### Abstract


This proposal intends to modify the current linear stake weight model of PIP-22 and enable a non-linear stake weight model. The mechanism for such change is already included in the PIP-22, therefore this proposal is only a parameter update proposal.

This modification is required to address a fairness issue that reduces the rewards of base stake nodes and to enable a stake compounding strategy that is beneficial for the quality of service of the network.

We propose to change the ServicerStakeFloorMultiplierExponent to a value lower than 1.0 (under current network state it should range from 0.7 to 0.8). The need for this change roots in the limitations of the linear model to keep inflation constant without reducing the gain of nodes with base stake (those who decided to not perform any compounding). Forcing the compounding of stake was not part of the PIP-22, we want to correct this effect.

In this document we describe the main mechanisms of the PIP-22 and the effects of the linear stake weight modeling. Our main conclusions are:

- The linear weighting model penalizes the nodes that do not perform compounding. We estimate that non-compounded nodes are loosing at least ~15% of their rewards.
- With the linear staking model the only valid strategy is to compound at maximum stake. This creates a de-facto increase of the minimum viable stake. 
- Observing only the variations of the number of sessions by node does not gives enough information on how the number of relays is modified. Hence, the reduction of the rewards for the base stake nodes is not correctly justified.
- If the performance of the nodes in each bin (measured in relays) is not similar, the calculation of the ServicerStakeFloorMultiplier does not result in constant inflation. Correcting this problem leads to further penalization of nodes in the base stake.


# Ebirah crosschain transfer solution 


## Problem

Alice want to transfer tokens from chain A (source chain) to chain B (destination chain) and do it trustless.

## Solution 

Ebirah offers cross-chain trustless solution. 

### Structure 

Landing contract on source chain is responsible for receiving funds and protecting transfers from unauthorized access

Distribution contract is Ebirah core contract on destination chain responsible for releasing funds safely.  

Ebirah Backend responsible for listening source chain, making deposits to Distribution contract and funds withdrawal as soon as proof is provided.   

### Protocol 

Alice generates note and deposits funds to Landing contract providing commitment and hash of nullifier hash. 

Ebirah Backend transfers funds to Distribution contract along with commitment and hash of nullifier hash. 

Alice makes sure her commitment is on destination chain and requests funds withdrawal from Distribution contract providing valid proof and nullifier hash.

Ebirah Backend sees new withdrawal and requests funds from landing contract providing valid nullifier hash.

If Alice doesn't see her commitment or decided she doesn't want to withdraw funds in destination chain, she requests funds withdrawal from Landing contract providing nullifier hash after freezing period. Backend doesn't know hullifier hash so it cannot withdraw funds.  


### Assumption

This is not privacy protocol, for additional privacy Alice needs to use Ebirah core deployed in destination chain.


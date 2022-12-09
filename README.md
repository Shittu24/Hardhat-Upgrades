# UPGRADEABLE SMART CONTRACT WITH HARDHAT

There are three ways to upgrade a smart contract:
1. PARAMETERIZE
2. MIGRATION
3. PROXIES

PARAMETERIZE is the simplest way of upgrading smart contracts. It is not really upgrading smart contracts because we can't change the logic of the contract. We just ypdate the parameters. This is simple to implement however, not flexible.

MIGRATION is when you deploy a new contract not connected to the old contract in any way and by social convention you tell everyone the newly deployed contract is the real contract such as the migration between Aave V1 -> Aave V2 however, it has some pros and cons 
PROS: Truest blockchain values, Easiest to audit
CONS: Lot of work to convince users to move, Dufferent deployment addresses

In order to have a really robust upgrading mentality or philosophy, we need to have some type of methodology or framework that can update our state, keep our contract addresses, and allow us to update any type of logic in our smart contract in an easy way, we use:
PROXIES: This is the truest form of programmatic upgrades since users can keep interacting with the protocols through these proxies and not notice that anything change or even got upgraded. These are also the places you can screw up the easiest. Proxies uses a lot of low level functionality and the main one being the <b>delegateCall</b> functionality. This is a low level function where the code and target contract is executed in the context of the calling contract

For our contract, we worked with proxies to upgrade our contract using the proxy contract from the openzeppelin library. We built a Box contract and upgraded it to a BoxV2 contract using upgradeable proxies.
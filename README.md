# toke-deployment-upgrade-guide
A guide designed to accompany Ferrum Network's token contract deployment and token upgrade tooling from iterative supply management

**Contract addresses**

- ***Token Deployer***: `REDACTED - Provided during onboarding`
- ***Generic Token Contract***: `REDACTED - Provided during onboarding`
- ***Generic Token Contract with New Total Supply***: `REDACTED - Provided during onboarding`

# Deploy a new token

1. Go to the *Token Deployer* contract. -> *Write*
2. Select *deployToken*
3. For logic, provide the *Generic Token Contract* address
4. Provide `name` `symbol` `totalSupply`
5. For `admin` provide the address of the wallet that will be able to upgrade the token in future
6. Please maintain a separate admin than token holder. Admin should have no token balance
7. Execute the transaction. (Make sure you are not using the admin wallet). You will be minted tokens
8. You can get the token address from the transaction logs.

```
Best practice to have admin be a multisig account. Make sure the multisig account can call smart contracts.
```

# Update supply

1. Go to your token address.
2. Go to *Write*
3. Select *UpgradeToAndCall*
4. Enter `0` for `payableAmount`
5. For `newImplementation` provide *Generic Token Contract with New Total Supply* from above
6. Enter data. Data can be calculated as follows
 - Go to the *Token Deployer* address. *Read*.
 - Select *updateTotalSupplyMethodData*
 - For `to` provide the address that wants to receive the newly minted tokens
 - Provide the `newTotalSupply`
 - Press *Query* and copy the data

# Roll back to the non mintable token contract
1. Go to your token address.
2. Go to *Write*
3. Select *upgradeTo*
4. for `newImplementation` provider *Generic Token Contract* from above

```
 Note: Upgrade transactions must be executed by admin.
```

# Deploy basic token

Uset the following address: `REDACTED - Provided during onboarding`

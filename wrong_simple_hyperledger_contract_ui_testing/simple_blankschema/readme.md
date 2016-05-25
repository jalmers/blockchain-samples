#Simple Blank Schema contract

The schema is key for the IoTP to be able to configure and send data to the contract. This is the first on three incorrect contract scenarios. In this case, the contract code doesn't change, but the schema is blank. It returns an empty string. We need to ensure that the UI can gracefully handle this. 

The simple_contract_hyperledger logic is untouched. Only the schemas.go is modified in this version

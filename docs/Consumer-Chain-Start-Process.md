# Consumer Chain Start Process

The process we are following to start the consumer chains is as follows:
1. Initialize the consumer chain genesis file
2. Generate a hash for the consumer chain binary and genesis file.
3. Submit a consumer addition proposal using these hashes. See the [proposals](proposals) folder for examples from the Game of Chains testnet.
   ```
   gaiad tx gov submit-proposal consumer-addition <proposal JSON file> --from <account name or address>
   ```
4. Once the proposal passes, wait for the spawn time and collect the CCV (Cross Chain Validation) state in the provider chain.
   - If the spawn time is set to a time before the voting period ends, the CCV state will be available as soon as the proposal passes.
   - The `consumer-genesis` query will fail if the spawn time has not been reached.
   ```bash
    gaiad query provider consumer-genesis <consumer chain ID> -o json > ccvconsumer_genesis.json
    ```
5. Update the consumer chain genesis file.
   Insert the CCV state generated by the provider chain.
    ```bash
    jq -s '.[0].app_state.ccvconsumer = .[1] | .[0]' <consumer genesis without CCV state> ccvconsumer_genesis.json > <consumer genesis file with CCV state>
    ```
   Modify the parameters of the CCV module so the `unbonding_period` matches the provider chain's. For a provider chain with a 4-day unbonding period, change this:
   ```
   "ccvconsumer": {
      "params": {
        "enabled": true,
        "blocks_per_distribution_transmission": "1000",
        "distribution_transmission_channel": "",
        "provider_fee_pool_addr_str": "",
        "ccv_timeout_period": "2419200s",
        "transfer_timeout_period": "3600s",
        "consumer_redistribution_fraction": "0.75",
        "historical_entries": "10000",
        "unbonding_period": "1728000s"
      },
   ```
   To this:
   ```
   "ccvconsumer": {
      "params": {
        "enabled": true,
        "blocks_per_distribution_transmission": "1000",
        "distribution_transmission_channel": "",
        "provider_fee_pool_addr_str": "",
        "ccv_timeout_period": "2419200s",
        "transfer_timeout_period": "3600s",
        "consumer_redistribution_fraction": "0.75",
        "historical_entries": "10000",
        "unbonding_period": "345600s"
      },
   ```  

5. Run the consumer chain binary.
6. Set up IBC connections and channels between the provider chain and the consumer chain.
   - Using Hermes:
   ```
   hermes create connection --a-chain <consumer chain ID> --a-client 07-tendermint-0 --b-client <client assigned by provider chain> 
   hermes create channel --a-chain <consumer chain ID> --a-port consumer --b-port provider --order ordered --a-connection connection-0 --channel-version 1
   hermes start
   ```

The diagram below illustrates this process.

![Consumer chain start process](../images/consumer-start-process.svg)


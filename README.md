# Welcome to Opus Testnet

Opus Testnet is an experimental spin-off from the Ethereum Optimism network, designed to serve as a sandbox for learning and innovation.

By forking the Optimism codebase, Opus Testnet provides a unique opportunity to explore the intricacies of roll-up technology and contribute to advancing layer 2 scaling solutions.

This testnet aims to foster a collaborative environment where developers can test new ideas, iterate on existing implementations, and drive improvements to the current deployment.

## Technologies Used:

1. Ethereum Optimism: The project is a fork of the Ethereum Optimism codebase, utilizing their layer 2 scaling solution.
2. Solidity: Smart contracts were written in Solidity, a programming language for Ethereum.
3. Go: The Optimism node software is written in Go, which was used for building and customizing the testnet.
4. Deployment: The Rollup was deployed to Sepolia L1 Testnet
5. GitHub: Version control and collaboration were managed through GitHub.


## Implementations:

1. Custom Rollup Configuration: A custom rollup configuration was implemented to test and experiment with different layer 2 scaling solutions.
2. Partner Technologies: Collaboration with other projects and technologies, such as  Optimism,  Conduit and Tenderly , allowed for knowledge sharing and faster development.


## Challenges and Lessons Learned:

I previously gained experience working with Rollups, specifically the Cartesi Rollup. However, this project marked my first attempt at building a Rollup from scratch. The tutorial guide proved invaluable, but I still encountered some errors along the way, which I managed to resolve through persistence and learning.

I tried deploying to Conduit but couldn't the coupon was not working.

This project offered a fantastic opportunity to delve deeper into the inner workings of Rollups and the intricacies of setting one up. I gained insight into the roles of additional contracts like the batcher, proposer, and sequencers, which I plan to explore further to understand how they integrate seamlessly.

By exploring the Ethereum Optimism codebase, I discovered the various components that come together to form a network. I'm eager to continue studying this in more detail and potentially contribute to the codebase by addressing existing issues.

A significant milestone was successfully connecting my Opus testnet to both op-geth (the execution client) and op-node (the consensus client). This achievement marked a significant step forward in my understanding of Rollup technology and its implementation.


## Code Modification
My code changes to the fork are available in the  `tutorial/chain` branch on the `packages/contract-bedrock` directory

## Opus Testnet Deployment Info
Here are the testnet info:

I initially deployed using the default chain 42069 and later made some modifications to the deploy contract and the getting started script added my own network with this chainId 81423.

The `genesis.json` and  `rollup.json` files are available in [opus-config](./opus-config/) directory.

## How to Run and Interact with the Opus Testnet Locally

## Start op-geth
Initialize op-geth
```build/bin/geth init --datadir=datadir genesis.json```

Run the EL client
```bash
./build/bin/geth \
  --datadir ./datadir \
  --http \
  --http.corsdomain="*" \
  --http.vhosts="*" \
  --http.addr=0.0.0.0 \
  --http.api=web3,debug,eth,txpool,net,engine \
  --ws \
  --ws.addr=0.0.0.0 \
  --ws.port=8546 \
  --ws.origins="*" \
  --ws.api=debug,eth,txpool,net,engine \
  --syncmode=full \
  --gcmode=archive \
  --nodiscover \
  --maxpeers=0 \
  --networkid=42069 \
  --authrpc.vhosts="*" \
  --authrpc.addr=0.0.0.0 \
  --authrpc.port=8551 \
  --authrpc.jwtsecret=./jwt.txt \
  --rollup.disabletxpoolgossip=true
```

### Run the op-node client
```
./bin/op-node \
  --l2=http://localhost:8551 \
  --l2.jwt-secret=./jwt.txt \
  --sequencer.enabled \
  --sequencer.l1-confs=5 \
  --verifier.l1-confs=4 \
  --rollup.config=./rollup.json \
  --rpc.addr=0.0.0.0 \
  --rpc.port=8547 \
  --p2p.disable \
  --rpc.enable-admin \
  --p2p.sequencer.key=$GS_SEQUENCER_PRIVATE_KEY \
  --l1=$L1_RPC_URL \
  --l1.rpckind=$L1_RPC_KIND
```

## Tutorial Guide
Incase you run into any issues while setting the clients up you can check this tutorial [guide](https://docs.optimism.io/builders/chain-operators/tutorials/create-l2-rollup#start-op-geth).
It was a great resource for spinning up the testnet rollup.

## Future Plans

- Study the op stack more extensively and contribute to the
ethereum optimism repo
- Introduce new smart contract features and functionalities
- Enhance developer tools and documentation for improved user experience
- Launch incentivized testnet programs for dApp developers
- Conduct thorough security audits
- Implement mainnet-specific features and configurations
- Launch Opus Mainnet
- Introduce governance mechanisms for community involvement

## Additional Development
In addition to spinning up the testnet rollup. I also attempted working on OP Stack health dashboard tooling. The link to the dashboard design can be found [here](https://www.figma.com/design/610NMqJ4R9A0upp8jMqSK5/SuperchainList-Dashboard?node-id=9-1844&t=GGj34D6zHBXPjhNR-0) and the link to the dashboard repo can be found [here](https://github.com/gconnect/superchainlist).


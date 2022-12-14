# Interchain Security Testnets

* [Private Testnet information](private-testnet/README.md)
* [Game of Chains information](game-of-chains-2022/README.md)

---

## 코스모스테이션 GoC task 리포트

### GoC Timeline
* 2022-11-10 13:00 UTC ~ 2022-12-09 UTC

### 🔎 Auditor Tasks

#### Review and Vote on Proposals

| Phase | Completed | # | Points | Task | Evidence |
|---|---|---|-----|-----|---|
| 1 | ✅ | 1 | 1  | Vote yes on the Sputnik `create-consumer-chain` proposal | TX hash |
| 1 | ✅ | 2 | 1  | Vote yes on the Apollo `create-consumer-chain` proposal | TX hash |
| 2 | ✅ | 3 | 1  | Vote yes on the Neutron `create-consumer-chain` proposal | TX hash |
| 2 | ✅ | 4 | 1 | Vote yes on the Gopher `create-consumer-chain` proposal | TX hash |
| 2 | 🚫 | ~~5~~ | ~~1~~ | ~~Vote yes on the Stride `create-consumer-chain` proposal~~ | ~~TX hash~~ |
| 2 | ✅ | 6 | 1 | Vote yes on the Apollo `stop-consumer-chain` proposal | TX hash |
| 3 | ✅ | 7 | 1 | Vote no on at least one proposal that contains incorrect metadata | TX hash and reason for votivoting no |
| 3 | ✅ | 8 | 2 | Vote no on at least one proposal that links to malicious binaries | TX hash and reason for voting no |
| 2 | ✅ | 26 | 1 | Vote yes on the Hero `create-consumer-chain` proposal | TX hash |
| 3 | ❌ | 30 | 1 | Vote **yes** on the `slasher` chain `consumer-addition` proposal | TX hash |
| 3 | ❌ | 32 | 2 | Vote on at least 70% of all proposals | TX hashes or block explorer link |

#### Validator Sets Monitoring

**‼ 📢 The following task can be completed at any point throughout the testnet program**

| # | Points | Task | Evidence |
|---|-----|-----|---|
| 9 | 50 | Find a consumer chain validator set that has not existed in the provider chain | Log, block height |
| 10 | 50 | Find a validator set update that is received in the wrong order in a consumer chain | Log, block height |

### 👷 Builder Tasks

#### Start and Stop Consumer Chains

| Phase | Completed | #  | Points | Task | Evidence |
|----|----|----|-----|-----|---|
| 1 | ✅ | 11 | 1 | Sign the first block after genesis of the Sputnik chain | None required* |
| 1 | ✅ | 12 | 1 | Sign the first block after genesis of the Apollo chain | None required* |
| 2 | ✅ | 13 | 1 | Sign the first block after genesis of the Neutron chain | None required* |
| 2 | ✅ | 14 | 1 | Sign the first block after genesis of the Gopher chain | None required* |
| 2 | 🚫 | ~~15~~ | ~~1~~ | ~~Sign the first block after genesis of the Stride chain~~ | ~~None required*~~ |
| 2 | ✅ | 16 | 1 | Sign the last block of the Apollo chain without having been jailed for downtime since the first block | None required* |
| 3 | ❌ | 17 | 2 | Sign the last block of the Sputnik chain without having been jailed for downtime since the first block | None required* |
| 3 | ❌ | 18 | 5 | Create at least one custom consumer chain binary for a proposal that passes   | Source code |
| 3 | ❌ | 19 | 5 | Submit at least one `create-consumer-chain` proposal for a chain that starts  | TX hash |
| 3 | ❌ | 20 | 5 | Submit at least one `stop-consumer-chain` proposal that results in the chain stopping at the specified stop time | TX hash |
| 2 | ✅ | 27 | 1 | Sign the first block after genesis of the Hero chain | None required* |
| 3 | 🚫 | ~~28~~ | ~~1~~ | Assign a key on a consumer chain | TX hash |
| 3 | 🚫 | ~~29~~ | ~~1~~ |  ~~Assign a key on a new consumer chain~~ | ~~TX hash~~ |
| 3 | 🚫 | 31 | 2 |  Get unjailed after being slashed by the `slasher` chain | TX hash |

* \*For tasks that do not require evidence, testnet coordinators will query the relevant blocks.

#### Run a Relayer

| Phase | Completed | # | Points | Task | Evidence |
|---|----|----|---|----|----|
| 3 | ✅ | 21 | 20 | Run a relayer between a provider and consumer chain that relays at least 500 validator set changes | [Consumer chain block heights with validator set updates](https://github.com/cosmostation/goc2022-relayer-evidence) |

### 🌪 Chaotic Tasks 

**‼ 📢 Chaotic tasks can be completed at any point throughout the testnet program**

#### Validator Misbehaviour

| Completed | #  | Points | Task | Evidence |
|----|----|---|----|----|
| ✅ | 22 | 22 | 5 | Get unjailed at least twice after downtime in Sputnik or Apollo | TX hashes |
| ❌ | 23 | 23 | 5 | Double sign in Sputnik or Apollo and create a new validator | Block height for double-signing and TX hash for creating new validator |
| ❌ | 24 | 24 | 150 | Double sign in a consumer chain without getting jailed | Write-up |

#### Relayer Misbehaviour

| Completed | #  | Points | Task | Evidence |
|----|----|---|----|----|
| ❌ | 25 | 150 | Break the protocol through relayer misbehaviour | Write-up that demonstrates behaviour that deviates from [the ICS-028 spec](https://github.com/cosmos/ibc/blob/main/spec/app/ics-028-cross-chain-validation/README.md). 

### 🏅 Testnet Awards

The testnet jury will decide who is the winner of the following awards:

| Completed | Points | Award | Description |
|---|---|---|---|
| ❌ | 200 | Best Auditor | Find any unexpected critical issues that were not found through planned tasks |
| ❌ | 100 | Public Goods Awards (Up to two) | Integrates a block explorer, wallet, dashboard, or creates a novel tool that is useful for testing Interchain Security |
| ❌ | 50  | Most Helpful Validator | Provides guidance and onboarding support to others, answers questions in Discord |
| ❌ | 25  | Best Memes | Gets people excited on social media through tweets and memes |

If you would like to provide the jury with more information about your pariticipation in the testnet that should be considered for these awards, feel free to use the evidence submission form. You may submit issue writeups, descriptions for public goods, or any other evidence that can help us make an informed jury decision.

---

## GoC Task details

### ICS nodes On-borading Process
  1. provider 체인 셋업 후 밸리데이터 키(priv_validator_key.json) 백업
  2. 현재 온체인에 등록된 컨슈머 체인 셋업 
  3. consumer 체인의 밸리데이터 키(priv_validator_key.json) 삭제
  4. provider 체인의 백업된 밸리데이터 키를 consumer 체인에 원복
  **(즉, provider & consumer chain은 동일한 밸리데이터 키를 사용해야 함)**


### ICS Consumer Chain Proposal On-borading Process
  1. 프로바이더 체인에 제네시스와 바이너리 해시값과 spwan time를 적은 json 파일을 온체인에 제출 
  ```
  $ gaiad tx gov submit-proposal consumer-addition <proposal JSON file> --from <validator-keyname>

  // sample JSON file
  {
      "title": "Create the Neutron chain",
      "description": "This is the proposal to create the consumer chain \"neutron\". Visit https://github.com/hyphacoop/ics-testnets/tree/main/game-of-chains-2022/neutron for details on this proposal's data and how to join the chain.",
      "chain_id": "neutron",
      "initial_height": {
          "revision_height": 1
      },
      "genesis_hash": "b728614990cb97389e784ad45670a03eb40c119f1d7342aae427eb4afb739eb4",
      "binary_hash": "1eb39959c25c5d6300b4624db882cfa9668aa83d58eed208e0fa28620e7af8ea",
      "spawn_time": "2022-11-23T15:00:00.000000Z",
      "deposit": "1uprov"
  }
  ```
  2. 프로포절이 올라오면 각 프로바이더의 밸리데이터들은 해당 컨슈머체인의 메타데이터가 정상인지 체크하고 통과시킴
  ```  
  // sample consumer-chain metadata
  Chain Data
  Binary
  The reference binary published in this repo is the neutrond binary built using the neutron repo commit f5f1ce84a18d9b274a3caa2719997e26c43d3448. You should generate the binary following the build instructions.

  Linux amd64 build
  SHA256: 1eb39959c25c5d6300b4624db882cfa9668aa83d58eed208e0fa28620e7af8ea
  Genesis file
  The genesis file for Interchain Security consumer chains must include the CCV (Cross Chain Validation) state generated by the provider chain after the spawn time is reached.

  Final genesis file with CCV state: neutron-genesis.json

  SHA256: 3be634c2772731cc6bf2998ebc47fc89069382c98bc785675788ffa81403dbb5
  Validators must replace their config/genesis.json file with this one before running the binary.

  프로포절 통과 시 쿼리를 날리면 온체인에 컨슈머체인이 펜딩된 것을 볼 수 있음
  $ gaiad q provider list-start-proposals
  proposals:
  pending: []
  ```

  3. 그리고 해당 consumer-chain 의 spwantime이 경과하면 온체인에 등록됨
  ```
  gaiad q provider list-consumer-chains

  // result
  chains:
  - chain_id: duality
    client_id: 07-tendermint-6
  - chain_id: flash
    client_id: 07-tendermint-16
  - chain_id: gopher
    client_id: 07-tendermint-5
  - chain_id: hero-1
    client_id: 07-tendermint-3
  - chain_id: neutron
    client_id: 07-tendermint-4
  - chain_id: schwifty-1
    client_id: 07-tendermint-13
  - chain_id: slasher
    client_id: 07-tendermint-17
  ```

  4. 이후 쿼리를 하면 앱체인 스테이트가 나오고 기존 fresh genesis에 스테이트를 넣어줘서 consumer-chain 
  ```
  $ gaiad q provider consumer-genesis duality -o json
  ```

  5. 앞으로 내려갈 체인은 반대로 stop-list에 pending 
  ```
  $ gaiad q provider list-stop-proposals
  proposals:
    pending:
    - chain_id: flash
      description: ""
      stop_time: "2022-12-09T20:00:00Z"
      title: ""
  ```
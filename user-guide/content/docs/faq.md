---
weight: 999
title: FAQ
---

{{<expand "Why aren't my unused addresses imported when I restore a wallet?" "...">}}

This is by vertue of the blockchain. An unused address is by definition unused. Meaning that is doesn't exist on the chain and only exists locally, in the context of the software that has generated it. Different softwares may use different rules to generate addresses. For example in the past, _cardano-sl_ wallets used a method called random derivation where addresses will be created from a root seed and a random index that is stored with the address itself. Because indexes are random, it is not possible to restore randomly generated addresses that haven't been used on chain! 

More recently, `cardano-wallet` have been using sequential derivation which follows a very similar principle with the major difference that indexes are derived in sequence, starting from 0. Following this method, wallets aren't allowed to pre-generated too many addresses in advance, which as a consequence, makes it possible to restore a wallet across many machines while keeping a very consistent state. 
{{</expand>}}

{{<expand "I’ve noticed that other blockchains create accounts for wallets?" "...">}}

There are two sides to this question. Either, you are referring to accounts as in Ethereum accounts, or you may refer to accounts of hierarchical deterministic wallets.

In the first scenario, assets in the form of accounts are only supported in the Shelley era of Cardano and only for a specific use-case: rewards. Rewards are indeed implicitely published on the blockchain to mitigate the risk of flooding the network at the end of every epoch with rewards payouts! Hence, each core node keeps track of the current value of each reward account in a Ledger. Money can be withdrawn from this account and is then turned as a UTxO. Funds can never be manually sent to a reward account however. The creation of a reward account is done when registering a staking key, via a specific type of transaction.

In the second case, refer to the [HD wallets]({{< ref "hierarchical-deterministic-wallets.md" >}}) section in the _Key concepts_. Cardano wallets typically follow an HD tree of derivation as described in this section. 
{{</expand>}}

{{<expand "It seems like I have to install and configure many APIs and libraries, what is the fastest and most simple way to do this at once?" "...">}}

🐳 [docker](https://docs.docker.com/) is your friend here! Every component is packaged as docker images. Releases are tagged and the very edge is always accessible. See the various docker guides on the components' repository, and also how to compose services using [docker-compose](https://docs.docker.com/compose/).
{{</expand>}}

{{<expand "Is there a reason why I would have to build from src?" "...">}}

If you intend to contribute to Cardano by making code changes to one of the core components, then yes. We recommend using [stack](https://docs.haskellstack.org/en/stable/README/) for a better developer experience. 

If you only intend to use the services as-is then, using either the pre-compiled release artifacts on your appropriate platform or, a pre-packaged docker image would be preferable.
{{</expand>}}

{{<expand "Where is the faucet and do I get test ADA?" "...">}}

- On Byron, have a look at: https://testnets.cardano.org/en/cardano/byron/tools/faucet
- On Shelley, this is coming soon.

{{</expand>}}

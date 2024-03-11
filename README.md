<div align="center">
  <img src="docs/logos/zkthread.png" alt="zkthread" height="300"/>

  <h1>ZkThread</h1>
  
  ***Fractal scaling without fragmentation***

  [![Exploration_Team](https://img.shields.io/badge/Exploration_Team-29296E.svg?&style=for-the-badge&logo=data:image/svg%2bxml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz48c3ZnIGlkPSJhIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxODEgMTgxIj48ZGVmcz48c3R5bGU+LmJ7ZmlsbDojZmZmO308L3N0eWxlPjwvZGVmcz48cGF0aCBjbGFzcz0iYiIgZD0iTTE3Ni43Niw4OC4xOGwtMzYtMzcuNDNjLTEuMzMtMS40OC0zLjQxLTIuMDQtNS4zMS0xLjQybC0xMC42MiwyLjk4LTEyLjk1LDMuNjNoLjc4YzUuMTQtNC41Nyw5LjktOS41NSwxNC4yNS0xNC44OSwxLjY4LTEuNjgsMS44MS0yLjcyLDAtNC4yN0w5Mi40NSwuNzZxLTEuOTQtMS4wNC00LjAxLC4xM2MtMTIuMDQsMTIuNDMtMjMuODMsMjQuNzQtMzYsMzcuNjktMS4yLDEuNDUtMS41LDMuNDQtLjc4LDUuMThsNC4yNywxNi41OGMwLDIuNzIsMS40Miw1LjU3LDIuMDcsOC4yOS00LjczLTUuNjEtOS43NC0xMC45Ny0xNS4wMi0xNi4wNi0xLjY4LTEuODEtMi41OS0xLjgxLTQuNCwwTDQuMzksODguMDVjLTEuNjgsMi4zMy0xLjgxLDIuMzMsMCw0LjUzbDM1Ljg3LDM3LjNjMS4zNiwxLjUzLDMuNSwyLjEsNS40NCwxLjQybDExLjQtMy4xMSwxMi45NS0zLjYzdi45MWMtNS4yOSw0LjE3LTEwLjIyLDguNzYtMTQuNzYsMTMuNzNxLTMuNjMsMi45OC0uNzgsNS4zMWwzMy40MSwzNC44NGMyLjIsMi4yLDIuOTgsMi4yLDUuMTgsMGwzNS40OC0zNy4xN2MxLjU5LTEuMzgsMi4xNi0zLjYsMS40Mi01LjU3LTEuNjgtNi4wOS0zLjI0LTEyLjMtNC43OS0xOC4zOS0uNzQtMi4yNy0xLjIyLTQuNjItMS40Mi02Ljk5LDQuMyw1LjkzLDkuMDcsMTEuNTIsMTQuMjUsMTYuNzEsMS42OCwxLjY4LDIuNzIsMS42OCw0LjQsMGwzNC4zMi0zNS43NHExLjU1LTEuODEsMC00LjAxWm0tNzIuMjYsMTUuMTVjLTMuMTEtLjc4LTYuMDktMS41NS05LjE5LTIuNTktMS43OC0uMzQtMy42MSwuMy00Ljc5LDEuNjhsLTEyLjk1LDEzLjg2Yy0uNzYsLjg1LTEuNDUsMS43Ni0yLjA3LDIuNzJoLS42NWMxLjMtNS4zMSwyLjcyLTEwLjYyLDQuMDEtMTUuOGwxLjY4LTYuNzNjLjg0LTIuMTgsLjE1LTQuNjUtMS42OC02LjA5bC0xMi45NS0xNC4xMmMtLjY0LS40NS0xLjE0LTEuMDgtMS40Mi0xLjgxbDE5LjA0LDUuMTgsMi41OSwuNzhjMi4wNCwuNzYsNC4zMywuMTQsNS43LTEuNTVsMTIuOTUtMTQuMzhzLjc4LTEuMDQsMS42OC0xLjE3Yy0xLjgxLDYuNi0yLjk4LDE0LjEyLTUuNDQsMjAuNDYtMS4wOCwyLjk2LS4wOCw2LjI4LDIuNDYsOC4xNiw0LjI3LDQuMTQsOC4yOSw4LjU1LDEyLjk1LDEyLjk1LDAsMCwxLjMsLjkxLDEuNDIsMi4wN2wtMTMuMzQtMy42M1oiLz48L3N2Zz4=)](https://github.com/keep-starknet-strange)

</div>

## Introduction

Over the past few years, applications in zero-knowledge proofs (ZKPs) have exploded in popularity, and Starknet has been proud to be one of the standard bearers for its adoption. Thus far though, from ZK rollup systems to zkCoprocessors, many ZK applications and their tech stacks have relied on in-house custom tech-stacks, resulting in a splintering of liquidity, a lack of interoperability, and poor user experience. In this article, however, we introduce “zkThreads,” a new technical standard that introduces a canonical zkCoprocessing framework on Starknet to create a design that balances security, composability, and interoperability for ZK applications.

First, we will establish a rationale for zkThreads, bringing to light the design limitations of having separate proof systems for each modularized component. Then, we will present an architectural design for zkThreads on Starknet, showing how we can implement this technical standard with just a new smart contract. Finally, we will discuss the novel applications that zkThreads may unlock, and how zkThreads transform Starknet into a ZK Operating System.

## Why zkThreads?

History may not often repeat itself, but it often rhymes. Back in November 2015, before the introduction of the ERC-20 standard, creating a new “token” or “coin” was incredibly difficult, as it required the construction and maintenance of an entire blockchain. Even if you only wanted a memecoin, you had to hard fork and bootstrap liquidity on an entire blockchain, such as the case of Dogecoin. As to be expected, not many tokens from the pre ERC-20 era survive today.

The reason here was that tokens were a feature highly integrated with the consensus protocol and transfer mechanisms that could not be plucked out on its own. ERC-20, however, introduced a canonical standard to create and transact tokens on Ethereum’s platform, without the need to hard fork and create a whole new chain. As projects were able to easily launch their own ERC-20s, these tokens’ liquidity became all concentrated on Ethereum’s platform, which made it feasible to construct DEXs, lending protocols, stablecoins, and the entire world of DeFi that we see today.

Today, we’re at a similar juncture in the development of ZK Applications. Although there is a wide variety of applications using ZK proofs, from rollups to bridges to zkCoprocessors, every system has its own proof libraries, VMs, tech stacks, and it is incredibly difficult to have these different tech stacks interoperate.

Take, for instance, the case of the zkCoprocessor. In the simplest sense, a zkCoprocessor relies on a form of “compute off-chain, verify on-chain,” where the “compute” ranges from specific tasks – such as computations over historical data – to Turing-complete general-purpose computation, and the “verification” is the posting of a ZK-proof of execution results onto the “base layer”. This design therefore allows for computationally intensive programs to be “outsourced” to off-chain computing power while retaining execution guarantees. Yet, there are still several problems with the zkCoprocessor design:

- Security: One big concern of zkCoprocessors is that even if they can guarantee proof correctness, they cannot guarantee liveness. In other words, they cannot guarantee that they will actually provide these proofs, instead of taking a nap – they are asynchronous processes.
- Composability: Every zkCoprocessor has their own technical standard, whether it be through custom ZK libraries or circuits, resulting a large lack of composability between these different processors.
- Interoperability: Because of (1) and (2), applications running on zkCoprocessors are siloed from one another, leading to fragmented liquidity and a lack of interoperability.

Although there may be ways to address these issues, such as using common Data Availability layers or other modular components, these are complex and relatively inefficient processes that do not address the root cause of the problem – the “siloed tech stack” design in zkCoprocessors. To develop a ZK application within a coprocessor VM, you have to stick to the way their circuits are written, or bring your own circuits. Switch out the coprocessor provider or proof library, and you have to learn a different system of proofs from scratch. Instead, what we need is a common interface – just like ERC-20 – to standardize the development of ZK applications and allow new use cases for interoperability, pooled liquidity, and other shared resources.

Enter zkThreads. Through leveraging Starknet’s position as a leading tech stack in ZK technologies and Cario’s natural advantage as an easily-provable language, aims to do just that. It provides the following guarantees:

- Security guarantee: Instead of having zkCoprocessors do computation as processes in an asynchronous environment, zkThreads allows ZK applications to do computation within a synchronous environment, thus providing liveness guarantees.
- Composability guarantee: Through introducing the common zkThread standard, developers are provided with a standard, composable toolkit to develop a wide variety of ZK applications – including native bridging, common DA layers, and security mechanisms.
- Interoperability guarantee: All applications built using the zkThread standard will be natively interoperable with each other, thus reducing fragmentation and unlocking a wide variety of new use cases.

## Architectural Design

The overall goal of the zkThreads architecture is to allow ZK applications to achieve a balance between performance, composability, and interoperability. Architecturally, it is composed of (1) the zkThread itself, which has its own “batcher” and “prover,” and (2) a “zkThreadManager,” a contract on the Starknet L2 that verifies state changes in each zkThread.

[![zkThreads Architecture](docs/zkthread_architecture.png)](docs/zkthread_architecture.png)

A zkThread is essentially an application bundle consisting of the thread’s contracts, a batcher, and a prover. The operational logic of the zkThread is as follows:

- Application logic is deployed in the thread’s contracts, which produce transactions and state changes in the zkThread.
- Transactions in the zkThread become batched in a sub-block as a list of state changes.
- The prover creates a STARK proof of the sub-block state changes, and then emits a transaction to the L2 sequencer.
- The zkThreadManager verifies the proof of the state changes against the canonical record it holds of the zkThread
- The zkThreadManager either accepts or rejects the state changes. If accepted, the canonical record is updated, if rejected, it cancels the zkThread transaction on the L2.

In this logic, the zkThreadManager’s primary goal is to verify that the “state changes proof” transaction emitted by a zkThread is valid. It does so by recording the canonical state of each zkThread and the OS version, then taking in the list of state changes and running it against this canonical state. If the resulting answer is the same, then the zkThread transaction is accepted, and the canonical state is updated. If not, then the transaction is reverted.

With the zkThreadManager keeping an updated canonical version of each zkThread recorded, this provides an easy way for other threads and applications on the L2 to keep track of the canonical state within a synchronous environment, thus allowing for much easier interoperability between the different threads. This is unlike the design of an L3, which only settles a single proof onto the L2. Adopting this standard of a zkThread thereby paves the way for a new possibility of interoperability between computationally-intensive applications, as the canonical version of each zkThreads enables atomic interoperability.

## Starknet the ZK Operating System

In the world of traditional operating systems, there is an important distinction between processes and threads. Processes are effectively independent instances of programs with their own memory, resources, and address blocks. Although it is technically possible to interoperate between different processes, this is a highly inefficient process, since there are no shared address blocks between these different processes. Threads, on the other hand, are more lightweight units of execution that share memory space and resources and are thus much more interoperable with one another. Crucially, one is not necessarily “better” than another, as it depends on the priorities of the application.

We can draw a similar analogy in the blockchain world. Starknet L3’s, rollups, and other zkCoprocessors right now are effectively isolated processes – each with their own separate resources, designs, and states. Although it is possible to use shared data availability frameworks and other mechanisms to achieve forms of interoperability, these are far from ideal. As mentioned previously, this is because these ZK systems are designed with isolated tech stacks, optimized for performance rather than composability and interoperability.

zkThreads, as suggested in the name, is the blockchain analogue of “threads” in the world of operating systems, where all these different processes operate on shared system resources and natively interfaced through the zkThreadManager’s canonical representations of each state. zkThreads are designed from the very start to be interoperable, introducing a simple yet elegant design that implements a new canonical framework for zkCoprocessing.

With the combination of L3s and zkThreads – ZK analogues of “processes” and “threads” respectively, Starknet effectively creates a ZK Operating System that is able to balance performance, composability, and interoperability.

In this ZK Operating System, there may be several classes of applications that can benefit from using the zkThreads architecture.

## Applications

### Interoperable Autonomous Game Worlds

zkThreads can play a huge role in allowing for enhanced interoperability between different game worlds, such as allowing different games to thrive from the same set of IP and lore. Consider something like the Mario or Pokémon franchises in the traditional world. Many of the characters and traits all originate from the same story universe, and these are combined in many different ways to create a vast array of games. 

zkThreads enables these interoperable autonomous game worlds as the game characters or IP can be stored on the Starknet L2, and each zkThread is able to not only read and update world states from the IP lore set, but also read state updates from each other. Game assets, evolutions, and achievements are thus transferable amongst the different game derivatives.

Imagine if in an on-chain Mario franchise, beating a level in Super Mario may unlock a new kart with special powers in Mario Kart. This Mario kart can then be bought, sold, or used as collateral to get Mario coins, which can buy you upgrades in Mario Golf. All this in turn unlocks a new dimension to the gameplay experience in these autonomous game worlds.

### ZK Secured Middleware and Shared Liquidity Infrastructure

The canonical version of a zkThread, stored within the zkThreadManager contract, in a sense acts as a common API for all of the different zkThreads. In the context of middleware, this adds a level of both programmability and security. Oracles, bridges, and other forms of middleware do not need to bootstrap a validator set from scratch, nor do they need to rely on forms of restaking that may pose centralization risks to the underlying chain. They can directly build functionality as a zkThread, and let the ZK proofs generated in the zkThread framework guarantee both security and interoperability.

This is especially true in the case of liquidity infrastructure, much of which can be shared between different applications. Consider something similar to Uniswap Hooks, where the boilerplate code is the same, but it is possible to customize certain aspects of the protocol to tailor it to specific needs. Under the zkThread design, the bulk of the program can be hosted as a zkThread, and the stored canonical version serves an easily customizable API with various hooks that other zkThreads and applications can implement. As mentioned before, zkThreads are designed to allow different programs to take advantage of shared resources and reap the benefits of economies of scale. Liquidity and shared TVL is perhaps one of the best examples of resources that can be leveraged between all of these zkThreads.

### On-Chain AI, Social Graphs, and Other Common Utilities

An extension of the shared middleware and liquidity infrastructure is a vast library of common digital resources. This includes on-chain AI systems, social graphs, and other libraries that can be shared across a variety of different applications. zkThreads provides the computational flexibility and resources to host an on-chain AI agent or model, whose canonical state can then be reflected in the zkThreadManager to be used in other applications, from gaming to social networking to productivity use-cases.

Similarly, a richly annotated and complex social graph can be hosted as a zkThread. Changes in the social graph can then be reflected across a wide range of different social networking applications. Thus, zkThreads provides a canonical framework for common utilities that have a high intensity of computation, allowing many applications to take advantage of these common resources.

## Credits

- Props to [Louis Guthmann](https://github.com/louisguthmannStarkware), dad of the original ZkThread concept. He spent consideral time and effort to convince us to start an exploration project on this topic.

## Towards Verifiable Applications

The above list, of course, is not exhaustive of all the applications that can be built using zkThreads, but gives some insight into the design space that zkThreads enables: one that merges together security, composability and interoperability, and one that just like ERC-20s, mark a pivotal point in the maturation of the blockchain space.

Through zkThreads, L3s, and a suite of other industry-leading technologies, Starknet enables a new ZK operating system that aims to create a thriving ecosystem of verifiable applications, where all arbitrary computation can be “proved” to be correct, from autonomous AI agents to high-frequency DeFi applications.

Trustlessness has long been a promise of the crypto space. Zero Knowledge Proofs epitomize this pursuit of trustlessness, as one of the best examples of how the industry marks a paradigm shift in computing history. And so we march onwards, towards a world of verifiable applications.

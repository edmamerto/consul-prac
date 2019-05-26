# Consul What is

> This is Consul 101

Agent what is 
> A simpler, more structured definition is to say that a software agent is a computer program that exhibits the characteristics of **agency** or **software agency**.

Agency what is
> a business or organization established to provide a particular service, typically one that involves organizing transactions between two other parties.

In our case
> entities are human and the computer

Characteristcs of Agents, Good Read
Link: [https://medium.com/@jackkrupansky/what-is-a-software-agent-6089dfe8f99](https://medium.com/@jackkrupansky/what-is-a-software-agent-6089dfe8f99)

Consul Agents
> Can run either in client mode or in server mode

Client
> The client is a very lightweight process that registers services, runs health checks and forwards queries to servers.

Cluster what is
> a set of interconnected instances that are treated as a single entity to enable load balancing, auto scaling and high availability.

Agent in cluster
> The agent must be running on every node that is part of the cluster.

Starting the agent in dev mode
> This mode is useful for bringing up a single-node Consul environment quickly and easily

```
$ consul agent -dev
```
In another terminal check members of the consul cluster
```
$ consul members
```
> out put of the members command is based on the "gossip protocol"

Gossip protocol
> Essentially a peer-to-peer messaging system



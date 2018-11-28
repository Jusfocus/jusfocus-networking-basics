## MPLS

## In a brief

MPLS is protocol used by Service Providers to provide VPN services to it's different customers using the same core network. 

## Scenario

Imagine a customer Apple. Apple has 2 branch sites, 1 HQ, 2 DC. 

### Requirement
Need connectivity between all 5 sites. ie, they need a *Private Wire Area Network (WAN)* which only they have access to. 

### Definition of private
secure - we controll the access.
invisible to other companies and even service providers from an application perspective.

### Solution Options

*Dedicated Options - Truly private*

1. Lay your own cable - close to impossible
2. Get dedicated leased lines between all sites - full mesh/hub and spoke - Very Expensive

*Shared Options - Virtual Private Network* 

The underlying *core* physical infra is shared by different entities. There are 2 options

1. Over internet - use the existing internet connection and use self managed DMPVPN
2. Get a dedicated local loop from a service provider and use service provider core network for connectivity between sites. - MPLS is the technology used in the SP core to make this happen.

## Topology

customer LAN(core switch/firewall) ---> CE router ----L2 wan link--- PE router--->Core(P,PE) ---> PE --> CE --> LAN

2 options for CE
1. Managed CE
2. Un-managed CE

## CE-PE Routing

BGP / static route

CE and PE - L3 link in the same /30 subnet. Interface will be a vlan interface with subscribed bandwidth (10MB)

### Local loop

ce-pe link is called local loop

1. Serial - SDH - multiplexers - terminates in serial interfaces in router
	ce - serial - E1/T1
	pe - STM-1
2. Ethernet (Metro Ethernet) - optical with convertor for less than 100M; more than 100M optical with SFP
3. DSL - using the existing telephone infra of copper wires to transmit data also. Usually download speed will be more than upload. uses 2 different frequency range for voice and data, seperated by a splitter ; quality/speed decreases over distance from exchange. 

#### On-Net
If the SP owns and manages the entire local loop transmission network.

#### Off-net
If the SP doesn't own and manage the tx network and instead buys it from a 3d party(OLO). 


### Provisioning
1. Presales / Design
2. Implementation
3. Testing
4. Handover to Ops

## Operations

1. Circuit Hard Down
2. Performance Degradation - slow speed/ flapping / packet loss


### Ops team responsiblities

1. Front-end --> interacts with customers. providing them updates etc. need to have excellent communication skills

2. Back-end / technical --> responsible for technical resolution of the issue.

### Backend Team Responsiblities

0. Gather all details about the circuit and assess and validate the issue.(triage)
1. Checks/troubleshoot the routers and other devices in the network( CE,PE, any other L3 devices) - logs, configuration mismatches, status, ping, traceroute
2. Collaborate with the transmission team to check the issues in tx network if the circuit is on-net and drive it to resolution.
3. Collaborate with the OLO if it's off-net
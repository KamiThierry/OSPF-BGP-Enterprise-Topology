**PROJECT OVERVIEW**

This project simulates a Tier-2 ISP network architecture, designed to demonstrate dynamic routing, path selection, and failover mechanisms in a multi-domain environment.

The topology integrates OSPF (Open Shortest Path First) for intra-domain routing and BGP (Border Gateway Protocol) for inter-domain connectivity, mimicking a real-world scenario where an ISP connects to upstream providers (e.g., MTN, Airtel) and cloud services.


**NETWORK TOPOLOGY**
The network consists of three distinct layers:

1. Provider Edge (PE) Routers: Handle customer connections and run internal routing protocols.
2. Core Routers: Manage high-speed traffic switching within the backbone.
3. ISP/External Routers: Simulate external Autonomous Systems (AS) like MTN and Cloud providers.

**Key Architecture Features**

1. Internal Routing (IGP): OSPFv2 configured in Area 0 (Backbone) for fast convergence between Core and PE routers.
2. External Routing (EGP): BGP used to exchange prefixes between the internal Autonomous System (AS 65000) and external ISP networks.
3. Redundancy: Point-to-point links configured with backup routes to ensure failover in case of link failure.

**IMPLEMENTATION**
1. OSPF Configuration (Intra-Domain)
  - configured single-area OSPF (Area 0) on all internal routers.

  - Established full neighbor adjacencies using Hello/Dead timers.

  - Validation: show ip ospf neighbor confirms Full/DR and Full/BDR states.

2. BGP Configuration (Inter-Domain)
   - eBGP: Established sessions between the Enterprise Edge and upstream ISPs (MTN/Airtel).

   - iBGP: Configured full-mesh iBGP between internal PE routers to ensure route propagation across the AS.

   - Route Redistribution: Redistributed OSPF routes into BGP to allow external visibility of internal public prefixes.

**Traffic Engineering**
   - Optimized path selection using BGP attributes to prefer stable, high-bandwidth links.

   - Implemented Loopback Interfaces (e.g., 172.16.10.1/32) to simulate stable management IP addresses.
   

**Tools Used**

   - Cisco Packet Tracer / GNS3 (Network Simulation) 

   - Cisco IOS (Router Configuration)

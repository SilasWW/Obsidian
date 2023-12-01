In distributed systems, the terms "message" and "broadcast" refer to different modes of communication between nodes (which are individual computers, servers, or devices in the network).

1. **Message**: This usually refers to communication from one node to another single node. It's a one-to-one form of communication. For example, if Node A sends data or a request to Node B, that's a message.
    
2. **Broadcast**: This is when one node communicates with all or a group of nodes in the system. It's a one-to-many form of communication. Broadcasting involves sending the same message to multiple nodes. For instance, if Node A has a message or data that needs to be sent to Nodes B, C, and D, it can broadcast this message, and all these nodes will receive it.
    

Broadcasting can be further categorized into different types based on the scope and method used:

- **Unicast**: One node sends a message to exactly one other node.
- **Multicast**: One node sends a message to a specific group of nodes.
- **Broadcast**: One node sends a message to all nodes in the network.
- **Anycast**: One node sends a message to any one out of a group of nodes, typically the one nearest to it.

These communication methods are crucial for coordinating actions, sharing data, and maintaining consistency across the distributed system.


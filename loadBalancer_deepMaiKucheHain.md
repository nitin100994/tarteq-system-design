Load Balancer – Deep Dive (System Design)

> Think of it as the traffic cop for your app. Smooth, smart, and strategic.




---

1. What is a Load Balancer?

A Load Balancer is a system component that distributes incoming traffic across multiple servers so that no single server gets overloaded.

Real-life analogy: Imagine a busy highway toll booth. If everyone goes to just one window, it gets jammed. The load balancer is the guy who says:

> “You go to lane 1, you to lane 2, you to lane 3...”




---

2. Why is it needed?

Prevents server overload

Improves speed and reliability

Adds redundancy — if one server fails, others take over

Scales horizontally (add more servers easily)



---

3. Types of Load Balancing Algorithms


---

4. Layer 4 vs Layer 7 Load Balancing

Layer 4:

Blunt but fast. Based on IP/port.


Layer 7:

Smart. Can route /api to backend1 and /images to backend2.



---

5. Health Checks

A good load balancer constantly pings servers to check if they're alive. If one goes down, it stops sending traffic to it.

Server 1: ✅
Server 2: ❌ (down)
Server 3: ✅
→ Route traffic to 1 & 3 only


---

6. Failover Handling

If a server fails:

Traffic gets rerouted

Sometimes a standby server (hot backup) takes over

Users may not even notice a hiccup



---

7. Where is Load Balancer Placed?

[Client Request] → [Load Balancer] → [Server 1, 2, 3]

It sits between users and servers, like a bouncer at a club.


---

8. Popular Tools


---

9. Diagram (Simple Text Version)

+----------------------+
           |     Load Balancer    |
           +----------+-----------+
                      |
     +----------------+----------------+
     |                |                |
+--------+        +--------+       +--------+
| Server |        | Server |       | Server |
|   1    |        |   2    |       |   3    |
+--------+        +--------+       +--------+


---

✅ Summary – What to Remember

Load balancer = traffic manager

Prevents overload, increases reliability

Works on Layer 4 or Layer 7

Has smart routing + health checks

Key to scaling real-world apps like Instagram, Flipkart, or ChaiSewa




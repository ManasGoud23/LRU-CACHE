📜 README: LRU Cache Implementation & Caching Concepts:

1️⃣ What is Caching? Why is it Needed?
**Caching is a technique used to store frequently accessed data in a temporary storage space to improve retrieval speed. Instead of fetching data from a slow primary source (database, disk, or API) every time, caching helps reduce latency and improve system performance.

Need for Caching:
✔ Faster Data Access – Reduces load on primary storage.
✔ Improves Performance – Reduces response time in applications.
✔ Efficient Memory Usage – Stores only frequently used data.
✔ Minimizes Redundant Computation – Saves processing power.

2️⃣ In-Memory Caching: Redis & Memcached
In-memory caching stores frequently accessed data in RAM instead of disks or databases, making retrieval significantly faster. Two popular in-memory caching systems are:

🔹 Redis (Remote Dictionary Server)
✔ Stores key-value pairs with optional data persistence.
✔ Supports data structures like lists, sets, and hashes.
✔ Used for real-time applications (leaderboards, chat systems).
✔ Supports LRU eviction for efficient memory management.

🔹 Memcached
✔ High-speed distributed memory caching system.
✔ Simple key-value storage model.
✔ Multi-threaded and optimized for high-speed caching.
✔ Used for reducing database load in web applications.

3️⃣ Cache Memory in Computer Organization
Cache Memory is a high-speed memory located between the CPU and RAM, storing frequently used instructions for faster processing.

✔ Levels of Cache Memory:

L1 Cache: Small, inside the CPU, fastest access.
L2 Cache: Slightly larger, located near the CPU.
L3 Cache: Shared among multiple CPU cores, larger but slower.
✔ Cache Mapping Techniques:

Direct Mapped Cache – Each block maps to a single cache line.
Fully Associative Cache – Any block can be stored in any cache line.
Set-Associative Cache – Hybrid approach allowing multiple placements.
4️⃣ Different Cache Replacement Strategies
When the cache is full, the system must evict old data to store new data. Different strategies include:

🔹 LRU (Least Recently Used) – Removes least recently accessed item.
🔹 FIFO (First In First Out) – Removes oldest stored item.
🔹 LFU (Least Frequently Used) – Removes least frequently accessed data.
🔹 Random Replacement – Randomly selects an item for eviction.

5️⃣ Designing LRU Cache using Doubly Linked List & HashMap
LRU Cache can be designed using a Doubly Linked List and HashMap:

✔ Doubly Linked List – Maintains the order of access (Most Recently Used → Least Recently Used).
✔ HashMap – Provides O(1) access to stored key-value pairs.
✔ Head & Tail Nodes – Dummy nodes for easy insertion/deletion.

Operations:
✅ GET (key): If key exists, move it to the front (Most Recently Used).
✅ PUT (key, value): Add the new key to the front. If full, remove Least Recently Used (tail).

6️⃣ UML Diagram for LRU Cache Design
plaintext
Copy
Edit

+----------------+
|   LRUCache     |
+----------------+
| - capacity     |
| - map (HashMap)|
| - head (Node)  |
| - tail (Node)  |
+----------------+
| + get(key)     |
| + put(key, val)|
| - insert(Node) |
| - delete(Node) |
+----------------+

           ┌──────────┐
           │  HashMap │
           └──────────┘
                │
                ▼
    +----------------------------------+
    │         Doubly Linked List       │
    +----------------------------------+
    │ head ⇄ Node1 ⇄ Node2 ⇄ ... ⇄ tail│
    +----------------------------------+

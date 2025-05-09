Cache – Deep Dive (System Design)

> Make your app feel instant. Explained like you're ordering chai the smart way.




---

1. What is a Cache?

A Cache is a super-fast storage layer that holds frequently accessed data so it can be retrieved quickly.

Analogy: If Pooja orders chai every day, the chaiwala keeps it ready near the counter. No need to go make it again and again.


---

2. Why Use Cache?

Speed up response time ⚡

Reduce load on main database

Improve app performance for users



---

3. Where is Cache Used?


---

4. Popular Cache Systems


---

5. Cache Types


---

6. Eviction Policies (When Cache is Full)

Example: Redis uses LRU by default (but supports others).


---

7. Time to Live (TTL)

You can set an expiry time for any cached item.

SET my_key "pooja_profile" EX 3600

= Expire in 1 hour

Useful for:

Session tokens

Trending news

Stock prices



---

8. Diagram: Where Cache Sits

[User] → [API] → [Cache] → [Database]
                     ↓
           (If hit, DB is skipped)

Cache Hit: Data found in cache (fast!) Cache Miss: Data not in cache → fetch from DB → store in cache


---

9. When Not to Use Cache

Highly dynamic data (e.g. live auction price)

Extremely secure data (e.g. banking passwords)

Very low traffic (no benefit from caching)



---

✅ Summary – What to Remember

Cache = fast memory for frequent data

Use Redis or Memcached

Strategies = Read-Through, Write-Through, Cache-Aside

Eviction = LRU, LFU, FIFO

Use TTL to expire old data

Great for speed, but don’t rely blindly — always have DB as source of truth


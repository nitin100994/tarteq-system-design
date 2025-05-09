CDN – Content Delivery Network (Deep Dive)

> Make your app feel lightning-fast, worldwide. Explained like Netflix on wheels.




---

1. What is a CDN?

A CDN (Content Delivery Network) is a network of servers placed around the world to deliver static content (like images, videos, CSS, JS) faster to users based on their location.

Real-life analogy:

Think of it as chai stalls placed in every mohalla so Pooja gets her chai faster — instead of waiting for it from Delhi HQ.


---

2. Why Use a CDN?

Speed up delivery of images, videos, files

Reduce load on your main server

Protect against DDoS attacks

Improve SEO and user experience



---

3. What Does a CDN Deliver?


---

4. How Does a CDN Work?

[User in Mumbai] → Requests image.jpg
→ Hits CDN server in Delhi (nearest PoP)
→ If cached → served instantly
→ If not → pulled from origin server → stored in cache

PoP = Point of Presence = CDN server closest to user


---

5. Popular CDN Providers


---

6. Cache-Control Headers

Control how long data stays in the CDN:

Cache-Control: public, max-age=3600

= Cache for 1 hour


---

7. Benefits of Using a CDN


---

8. When Not to Use a CDN

Internal enterprise apps with limited users

If most users are from one region only

If app is under development / frequent changes



---

✅ Summary – What to Remember

CDN = global delivery network for static content

Boosts speed, security, and user experience

Cache is king: deliver from nearest PoP

Use Cloudflare, AWS CloudFront, Akamai, etc.

Set proper cache headers to control behavior



---

Ready to move into your first system design case study? (Like designing Instagram, Zomato, or ChaiSewa?)


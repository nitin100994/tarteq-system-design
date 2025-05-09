System Design: URL Shortener (like bit.ly)

> Start small. Learn big. This is your gateway system.




---

1. What is a URL Shortener?

A service that takes a long URL like:

https://chat.openai.com/share/very-long-id-here

and returns:

https://sho.rt/Xyz123

Clicking the short URL redirects you to the long one.


---

2. Core Requirements

Functional:

Shorten a long URL → return a short link

Redirect short URL → long URL

Track number of clicks

Support expiry for short links

Provide analytics (geo, timestamp, device)

Generate QR code for each short link


Non-Functional:

High availability

Low latency

Scalability



---

3. High-Level Architecture

[Client] → [API Server] → [Database]
                  ↓
             [Cache Layer]
                  ↓
            [Analytics Service]


---

4. API Design

1. POST /shorten

Input:

{ 
  "long_url": "https://pooja.com/love/forever",
  "expiry": "2024-12-31T23:59:59Z"
}

Output:

{ 
  "short_url": "https://sho.rt/aZ91d",
  "qr_code_url": "https://sho.rt/aZ91d/qr.png"
}

2. GET /aZ91d

Redirects to original URL (if not expired)


3. GET /aZ91d/stats

Returns analytics data:

{
  "clicks": 1500,
  "last_accessed": "2024-05-01T18:30:00Z",
  "geo": ["India", "US"],
  "devices": ["Mobile", "Desktop"]
}


---

5. Short Code Generation

Auto-increment ID + Base62 encoding

Or UUID shortened and encoded

Optional: Allow user-defined aliases (e.g., sho.rt/pooja)



---

6. Database Schema

TABLE urls (
  id INT PRIMARY KEY AUTO_INCREMENT,
  long_url TEXT,
  short_code VARCHAR(10),
  created_at TIMESTAMP,
  expiry TIMESTAMP,
  clicks INT DEFAULT 0
);

TABLE analytics (
  id INT,
  access_time TIMESTAMP,
  ip_address VARCHAR(45),
  user_agent TEXT,
  location TEXT
);


---

7. Cache Layer (Redis)

Cache short → long URL

Cache expiry status

TTL based on expiry field



---

8. QR Code Generation

Generate using library (e.g., qrcode in Node.js or Python)

Store or regenerate on demand



---

9. Scaling Considerations


---

✅ Summary – Design Checklist

Accept long URL + optional expiry

Generate short code + QR

Store mapping in DB + Redis

Redirect only if link not expired

Track clicks + device + geo info

Show analytics in stats API

Cache smartly, scale safely



---

Next up: Design ChaiSewa App (Nitin & Pooja's dream tea startup — simple, lovable)


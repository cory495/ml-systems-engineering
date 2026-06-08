# Load

Date: 2026-06-05

---

## 1. Definition

---
Load is a measure of stress caused by the requests per second, the ratio of reads to writes, the number of simultaneously active users, the hit rate on cache, or some other load parameter.
## 2. Why It Matters

---
Load matters because it is how we accurately measure and analyze the rate of scaling.
## 3. Key Ideas

---
- Load parameters are a measure of load.
## 4. Examples

---
![[pic_twitter_SQL.png]]
The above is the first technique employed by Twitter. This technique was to insert a new tweet into a global collection of tweets. A user's home timeline looked up all people they followed, found all recent tweets, and merged them.
![[pic_twitter_method_2.png]]
The above is the second technique used by Twitter. Instead, each user's home timeline was created by maintaining a cache. When a tweet is posted by a user, all users who follow said user have this tweet added to their cache.

The first version was used until there were way more people using Twitter (magnitudes of 10). Thus, the second approach was implemented.

Now, Twitter is using a hybrid method. High-followed accounts use approach 1, while low-followed accounts use approach 2.
## 5. How It Is Achieved

---
Load is managed using different, smarter systems.
- Scaling Up / Vertical Scaling: Upgrading the machine to be better at managing higher loads.
- Scaling Out / Horizontal Scaling: Adding more machines.
- Elastic systems: Automatically adding computing resources when load is increased.
- When load increases, systems must scale. Magic scaling sauce (one-size-fits-all architecture) is not real.
## 6. Tradeoffs

---
The above example of Amazon shows a clear tradeoff. For instance, celebrities with high followings can cause bugs in method 2, but only implementing method 1 can cause high levels of load. Thus, a hybrid method should be used to optimally minimize load.
## 7. Related Concepts

- [[Scalability ]]
---

## 8. Summary
Load is the stress on a system caused by things like users or read/writes.
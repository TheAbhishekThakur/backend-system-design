# Cache Eviction Techniques (LRU, LFU, MRU, LIFO, FIFO & RR)

When a cache becomes **full**, the system needs to **decide which data to remove** to make space for new data. That decision-making process is called a **cache eviction policy** (or replacement policy).


## **1. LRU (Least Recently Used)**

- `Concept`: Remove the data that was used *least recently*.
- `Idea`: If it hasn’t been used for a long time, it’s less likely to be used again soon.
- `Advantage`: Works well when recent data is more likely to be reused.
- `Disadvantage`: Needs tracking of access order → slightly more memory overhead.

**Example:**

| Cache Content | Access Sequence     | Evicted               |
| ------------- | ------------------- | --------------------- |
| [A, B, C]     | Access D (A oldest) | A removed → [B, C, D] |


## **2. LFU (Least Frequently Used)**

- `Concept`: Remove the item that has been used *least often*.
- `Idea`: If something is rarely accessed, it’s less valuable to keep.
- `Advantage`: Good when some items are *hot* (used repeatedly).
- `Disadvantage`: Can retain old but frequently accessed items even if they’re no longer relevant.

**Example:**

| Cache            | Frequency | Evicted                |
| ---------------- | --------- | ---------------------- |
| A(5), B(3), C(1) | Add D     | C removed (least used) |


## **3. MRU (Most Recently Used)**

- `Concept`: Evict the *most recently used* item first.
- `Idea`: If something was just used, it might not be needed again soon (useful in specific scenarios like cyclic data).
- `Advantage`: Suitable for workloads where recently accessed items are less likely to be reused.
- `Disadvantage`: Performs poorly for typical caching patterns (where recent = relevant).


## **4. FIFO (First In, First Out)**

- `Concept`: Evict the item that entered the cache *first*.
- `Idea`: Oldest-in gets removed, regardless of usage.
- `Advantage`: Simple to implement (like a queue).
- `Disadvantage`: Ignores how often or how recently items are used.

**Example:**

| Order Added | Evicted          |
| ----------- | ---------------- |
| A → B → C   | Add D → Remove A |


## **5. LIFO (Last In, First Out)**

- `Concept`: Evict the *last* item added to the cache first.
- `Idea`: Like a stack — most recent entry gets removed.
- `Advantage`: Easy to implement.
- `Disadvantage`: Rarely efficient for real-world caching (recent data often useful).


## **6. RR (Random Replacement)**

- `Concept`: Randomly pick an item and evict it.
- `Idea`: No logic — purely random removal.
- `Advantage`: No overhead for tracking usage/frequency.
- `Disadvantage`: Can remove important items unpredictably → inconsistent performance.


## **Summary Table**

| Technique | Full Form             | Removes              | Ideal Use Case              | Example Tools            |
| --------- | --------------------- | -------------------- | --------------------------- | ------------------------ |
| **LRU**   | Least Recently Used   | Oldest accessed item | Most general purpose        | Redis, Memcached         |
| **LFU**   | Least Frequently Used | Least accessed item  | Highly repetitive workloads | Redis 4+                 |
| **MRU**   | Most Recently Used    | Newest accessed item | Cyclic or sequential data   | Some DB caches           |
| **FIFO**  | First In First Out    | Oldest inserted item | Simple queues               | Basic cache logic        |
| **LIFO**  | Last In First Out     | Last inserted item   | Rare, stack-like access     | Experimental             |
| **RR**    | Random Replacement    | Random item          | When simplicity > precision | Tiny caches, simulations |
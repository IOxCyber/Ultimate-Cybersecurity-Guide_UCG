SQLi = Attack database logic.


### 🔸 1. **In-Band SQLi**

**Definition:** Attacker gets data in the **same channel** as the injection (quick & easiest).

* **a. Error-based SQLi:** Extracts data using **DB error messages**.
* **b. Union-based SQLi:** Uses `UNION SELECT` to combine results from other tables.

---

### 🔸 2. **Blind SQLi**

**Definition:** No data shown directly — attacker infers results from **true/false behavior**.

* **a. Boolean-based Blind:** Observes **page changes** from true/false queries.
* **b. Time-based Blind:** Uses **delays** (e.g., `SLEEP()`) to infer true/false.

---

### 🔸 3. **Out-of-Band SQLi**

**Definition:** Uses a **separate channel** (e.g., DNS, HTTP) for data retrieval — useful when in-band/blind is blocked.

* ⚠️ Requires external interaction support (like DNS exfiltration) from DB.

---

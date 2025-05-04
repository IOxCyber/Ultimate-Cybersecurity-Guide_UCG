> ✅ **SQLMap works on Relational Databases**, because they use **SQL** (Structured Query Language), and SQLMap's job is to manipulate those SQL queries.

---

# 🔹 Is SQL-based DB = Relational DB?

**Almost always, yes.**
Because **SQL is the query language used by Relational Databases**.
So when we say “SQL-based DB,” it generally **means** a **Relational Database**.

---

# 🗂️ Common Relational Databases (RDBMS)

These are **targetable by SQLMap**:

| RDBMS                    | SQLMap Support | Notes                                           |
| ------------------------ | -------------- | ----------------------------------------------- |
| **MySQL / MariaDB**      | ✅              | Widely used in web apps                         |
| **PostgreSQL**           | ✅              | Open-source, very robust                        |
| **Microsoft SQL Server** | ✅              | Popular in enterprise systems                   |
| **Oracle DB**            | ✅              | Often used in corporate backends                |
| **SQLite**               | ✅              | Lightweight, used in mobile apps, local storage |
| **IBM DB2**              | ✅              | Used in legacy/enterprise apps                  |
| **SAP MaxDB**            | ✅              | Specialized systems                             |
| **Sybase**               | ✅              | Older enterprise systems                        |
| **Firebird**             | ✅              | Niche systems                                   |

All these are **Relational**, and SQLMap supports detection and exploitation for them.

---

# 🚫 Not Targeted by SQLMap:

These are **non-relational (NoSQL)** and SQLMap does **not** support them:

* MongoDB
* CouchDB
* Firebase
* Redis
* Neo4j (graph DB)
* Elasticsearch

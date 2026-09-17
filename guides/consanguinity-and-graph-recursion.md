# 🧬 Consanguinity, Pedigree Collapse & Recursive Graph Traversal

> Resolving cousin marriages, duplicate ancestors, and cyclic dependencies in genealogical graph databases.

---

## 1. The Pedigree Collapse Phenomenon (*Implex*)

In standard genealogical theory, an individual has:
- $2^1 = 2$ parents
- $2^2 = 4$ grandparents
- $2^3 = 8$ great-grandparents
- $2^n$ ancestors at generation $n$

In South Asian and Middle Eastern cultures, endogamy and cousin marriages (*first-cousin unions*) are historically common. When cousins marry:
- Children share common ancestors through multiple distinct paths.
- The theoretical number of ancestors collapses dramatically (known mathematically as **Pedigree Collapse** or *Implex*).

---

## 2. Graph Database Modeling vs Relational Tables

### The Cyclic Challenge
If a family tree is modeled as a strict tree data structure (where each node has exactly one parent), cousin marriages cause a crash or infinite recursion because a single person occupies two different ancestor slots simultaneously.

### Solution: Directed Acyclic Graph (DAG) with Union Nodes
Instead of attaching children directly to two independent parent nodes, model unions explicitly:

```
      [ Common Ancestor ]
          ┌───┴───┐
          ▼       ▼
      [ Father ] [ Mother ]
          └───┬───┘
              ▼
         [ (Marriage) ]
              │
              ▼
           [ Child ]
```

### Preventing Infinite Recursion in Eloquent / SQL
When querying ancestors recursively (e.g. Common Table Expressions `WITH RECURSIVE`), cycle prevention logic is mandatory:

```sql
WITH RECURSIVE ancestor_chain AS (
    SELECT id, father_id, mother_id, 1 as depth, ARRAY[id] as visited_ids
    FROM users
    WHERE id = :target_id

    UNION ALL

    SELECT u.id, u.father_id, u.mother_id, ac.depth + 1, visited_ids || u.id
    FROM users u
    JOIN ancestor_chain ac ON u.id = ac.father_id
    WHERE NOT (u.id = ANY(visited_ids)) -- Prevents cyclic loops
)
SELECT * FROM ancestor_chain;
```

Explore more real-world lineage data at [shajjra.com](https://shajjra.com).

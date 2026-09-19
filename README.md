## Anh Khoa Doan Ngoc

Backend and systems engineering. I'm most interested in the part of a system
where correctness is provable — invariants, concurrency, data integrity — and in
putting the rules somewhere they cannot be bypassed rather than somewhere they
are merely followed.

Master of IT, La Trobe University Melbourne.

---

### Selected work

**[obol-ledger](https://github.com/dnakhoa/obol-ledger)** · TypeScript, Postgres, Next.js — [live](https://obol-ledger.vercel.app)

A double-entry accounting ledger built around the idea that an invariant
belongs in the database, not in application code that has to remember it.

- Entries are balanced by a `DEFERRABLE INITIALLY DEFERRED` constraint trigger
  that runs at `COMMIT` — an immediate one fires after the first posting, when
  no entry has ever balanced.
- Tenant isolation is row-level security with `FORCE`, so a connection that has
  not named a tenant sees an empty database. A runtime probe asserts the
  policies are actually in force, because a `SUPERUSER` connection bypasses
  them silently.
- Money is `bigint` minor units with a currency-exponent registry — JPY has
  zero decimals, BHD has three — and crosses the wire as exact decimal strings,
  never JSON numbers.
- Idempotency claims its key *before* doing work, inside the same transaction,
  so a concurrent duplicate blocks rather than races.
- Concurrency claims are tested against a real Postgres over real connections,
  and each test was verified by deleting the thing it protects: remove the lock
  ordering and Postgres reports `40P01 deadlock detected`.

**[system-design-playground](https://github.com/dnakhoa/system-design-playground)** · Python

System design from fundamentals through to LLM-backed systems. Free and open.

**[stockflow](https://github.com/dnakhoa/stockflow)**

Multi-store inventory redistribution modelled as a minimum-cost flow problem —
an optimisation formulation rather than a heuristic.

**[kelp-dao-hack-analysis](https://github.com/dnakhoa/kelp-dao-hack-analysis)** · **[rollbit-scam-report](https://github.com/dnakhoa/rollbit-scam-report)**

Incident forensics: the KelpDAO rsETH / LayerZero DVN / Aave interaction, and an
investigation into Rollbit Casino. Reading systems adversarially, for what they
do rather than what they claim.

**[everything-data-structures](https://github.com/dnakhoa/everything-data-structures)** · **[llm-engineering-playground](https://github.com/dnakhoa/llm-engineering-playground)** · **[frontier-llm-engineering](https://github.com/dnakhoa/frontier-llm-engineering)**

Teaching material. Writing something down is how I find out whether I actually
understand it.

---

### Reach me

[LinkedIn](https://www.linkedin.com/in/anh-khoa-doan-ngoc/)

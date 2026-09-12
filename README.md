<!--
  PROFILE README — D-KAMALKALYAN
  3. Deploy your own github-readme-stats instance (see the setup guide) and swap
     the vercel.app hostnames below for yours.
-->

# Kamal Kalyan

**Backend engineer at TCS.** Java, Spring Boot, PostgreSQL. I spent my first six months in software doing application security, which permanently changed how I write code — I tend to assume the input is hostile and the network is unreliable, because for six months it always was.

Right now I'm most interested in the boring-hard parts of backend work: tenant isolation, transaction boundaries, what happens to your API on the third retry, and why the query that was fast in dev is not fast in prod.

<p align="left">
  <a href="https://www.linkedin.com/in/kamalkalyan/">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="https://backend-driven-portfolio.vercel.app/">
    <img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" />
  </a>
  <a href="mailto:kamalkalyan1260@gmail.com">
    <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
  </a>
</p>

---

## What I work with

**Daily, in production**

<p align="left">
  <img src="https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white" alt="Java" />
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white" alt="Spring Boot" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/REST_APIs-005571?style=flat-square&logo=fastapi&logoColor=white" alt="REST APIs" />
  <img src="https://img.shields.io/badge/OpenAPI-6BA539?style=flat-square&logo=openapiinitiative&logoColor=white" alt="OpenAPI" />
  <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white" alt="Git" />
</p>

**Comfortable with**

<p align="left">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker" />
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" alt="GitHub Actions" />
  <img src="https://img.shields.io/badge/JUnit-25A162?style=flat-square&logo=junit5&logoColor=white" alt="JUnit" />
  <img src="https://img.shields.io/badge/Node.js-5FA04E?style=flat-square&logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white" alt="MongoDB" />
  <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React" />
</p>

**Security background**

<p align="left">
  <img src="https://img.shields.io/badge/OWASP_Top_10-000000?style=flat-square&logo=owasp&logoColor=white" alt="OWASP Top 10" />
  <img src="https://img.shields.io/badge/SAST_%2F_DAST-1F6FEB?style=flat-square&logo=sonarqube&logoColor=white" alt="SAST / DAST" />
  <img src="https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white" alt="JWT" />
</p>

---

## Projects

### Multi-Tenant SaaS Core Platform

Java · Spring Boot · PostgreSQL · Docker · GitHub Actions

A shared-application, isolated-data platform core. The interesting decision here was tenant isolation strategy: database-per-tenant is the safest and the most expensive to operate, a discriminator column is the cheapest and the easiest to leak across, and schema-per-tenant sits between them.  **I chose discriminator-column-based isolation with tenant context enforced at the application/persistence layer because it keeps the platform operationally simple while making tenant boundaries explicit in every request and data-access path.**

* Tenant context is resolved per request and propagated through the persistence layer, so a missing `tenant_id` filter fails loudly rather than silently returning another tenant's rows
* Authentication uses **JWT access tokens with refresh tokens**, with **API-key authentication** for service-to-service/programmatic access; tenant resolution is tied to the authenticated request context and authorization is enforced through tenant-aware roles
* CI on every push via **GitHub Actions**: Maven build, compilation, test execution, and application verification

**[Read the architecture →](https://github.com/D-KAMALKALYAN/saas-multitenant-core-platform)**

---

### Legacy Code Modernization Assistant

Node.js · MongoDB · LLM APIs

Feeds legacy source files through an LLM to produce structured modernization reports. The engineering problem was not the prompting — it was that analysis runs take minutes, so the request/response model breaks down.

- Async job lifecycle: submit returns a job ID immediately, work happens off the request thread, clients poll for status
- Service boundaries kept narrow enough that the analysis workers could be split out of the monolith without a rewrite

**[Repository →](https://github.com/D-KAMALKALYAN/legacy-codebase-modernizer-agent)**

---

### CodeGuardian — Vulnerability Scanner

Node.js · React

Built while I was working as a security analyst, mostly to understand SAST tooling from the inside instead of just consuming its output.

- Rule-based detection across a subset of OWASP Top 10 categories 
- Scan orchestration API with authenticated, per-user scan history

**[Repository →](https://github.com/D-KAMALKALYAN/CodeGuardian)**

---

## Currently

- Going deep on **distributed systems fundamentals** — consistency models, partial failure, idempotency, and why "just retry it" is a design decision and not a fix
- Rebuilding my **DSA foundations** properly, from patterns rather than memorized solutions. Notes are public: **[dsa-notes →](REPO-URL)**
- Reading production Spring Boot codebases to steal better ideas than mine

## Things I believe about backend code

- If a bug is possible, it will happen at 2 AM at the worst tenant's scale
- A schema you can't migrate is a schema you don't own
- "It works on my machine" is a statement about your machine, not your code
- Most performance problems are one missing index and one N+1 query

---

## Reach me

- **LinkedIn** — [in/kamalkalyan](https://www.linkedin.com/in/kamalkalyan/)
- **Email** — kamalkalyan1260@gmail.com
- **Portfolio** — [backend-driven-portfolio.vercel.app](https://backend-driven-portfolio.vercel.app/)

Happy to talk about Spring Boot internals, Postgres query plans, or why your JWT implementation is probably fine but your refresh token handling isn't.

<!--
  OPTIONAL STATS BLOCK — uncomment once you've deployed your own instance.
  Replace YOUR-INSTANCE.vercel.app with your deployment hostname.

<div align="center">
  <img height="150" src="https://YOUR-INSTANCE.vercel.app/api?username=D-KAMALKALYAN&show_icons=true&hide_border=true&include_all_commits=true&count_private=true&theme=github_dark&hide_title=true" alt="GitHub stats" />
  <img height="150" src="https://YOUR-INSTANCE.vercel.app/api/top-langs/?username=D-KAMALKALYAN&layout=compact&hide_border=true&langs_count=6&hide=html,css,php&theme=github_dark" alt="Top languages" />
</div>
-->

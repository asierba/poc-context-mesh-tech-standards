# Security council — Secrets management and authentication

- **Date:** 2026-04-23, 10:00–11:05 UK
- **Attendees:** Aisha Bello (Head of Security), Daniel Kim (Security engineer), Priya Raman (Platform lead), Hannah Moore (SRE lead), Tom Okafor (Principal engineer, payments)
- **Recording:** auto-generated transcript, lightly cleaned up

---

**[00:00] Aisha Bello:** Two topics. Secrets first, because of last month's leaked API key. Then authentication.

## Secrets

**[00:07] Daniel Kim:** Rule one: all secrets live in AWS Secrets Manager. Nowhere else — not env files, not repos, not CI variables, not Kubernetes Secrets manifests.

**[00:17] Priya Raman:** Services read them at startup through the External Secrets Operator. It syncs them into the pod. Platform already runs it.

**[00:24] Daniel Kim:** Rotation: database credentials every 30 days, automated. Third-party API keys every 90 days. Signing keys yearly.

**[00:32] Hannah Moore:** What about humans needing a prod secret during an incident?

**[00:35] Aisha Bello:** Break-glass role only. Using it pages the security on-call, and every use is reviewed within 24 hours.

**[00:42] Daniel Kim:** And `gitleaks` in every repo's CI and as a pre-commit hook. A detected secret blocks the merge.

**[00:48] Aisha Bello:** Leak response, in this order. One: rotate it immediately — don't wait to confirm exposure. Two: open a Sev2 incident. Three: tell security in `#sec-incidents`. Four: scrub it from git history — after rotating, not before.

**[01:02] Tom Okafor:** Why after?

**[01:03] Aisha Bello:** Because people spend an hour rewriting history while the key is still live. Rotate first.

## Authentication

**[01:10] Daniel Kim:** Customers. Identity is Auth0. Services never store customer passwords. Web and mobile clients get a short-lived access token — JWT, 15 minutes — and a refresh token, 30 days, rotating.

**[01:23] Priya Raman:** The API gateway validates the JWT and forwards `X-Acme-Customer-Id` to backends.

**[01:28] Aisha Bello:** And backends trust that header only from the gateway. Anything else setting it is an attack.

**[01:33] Daniel Kim:** Service-to-service. All in-cluster traffic uses mTLS through Istio. Plain HTTP between services is blocked by network policy.

**[01:41] Priya Raman:** Authorisation uses the mesh's SPIFFE identity. Each service declares an allow-list of callers in its `AuthorizationPolicy`.

**[01:48] Aisha Bello:** And no shared API keys between internal services. That's how last month's key ended up in three repos.

**[01:54] Daniel Kim:** Staff. Okta SSO with hardware-key MFA — YubiKeys. SMS MFA is not allowed after the phishing attempt in February.

**[02:03] Hannah Moore:** Production access for engineers?

**[02:05] Daniel Kim:** Just-in-time through the access portal. Maximum eight hours, and it needs a linked ticket.

**[02:11] Aisha Bello:** Decisions. Secrets: AWS Secrets Manager only; External Secrets Operator; rotation 30/90/yearly; break-glass for humans with security page and 24h review; gitleaks blocks merges; leak response rotate → Sev2 → `#sec-incidents` → scrub history. Auth: Auth0 for customers, 15-minute JWT and 30-day rotating refresh, gateway-only `X-Acme-Customer-Id`; Istio mTLS with SPIFFE allow-lists and no shared internal API keys; Okta with YubiKey, no SMS; just-in-time prod access max 8 hours with a ticket.

**[02:40] (agreed)**

## Actions

- Daniel — publish secrets management and authentication docs.
- Priya — enforce the network policy blocking plain HTTP in all clusters.

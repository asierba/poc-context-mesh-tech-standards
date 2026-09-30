# Authentication & Authorisation

## Customers

- Customer identity is handled by **Auth0**. Services never store customer passwords.
- Web and mobile clients get a short-lived access token (JWT, 15 min) and a refresh token (30 days, rotating).
- The API gateway validates the JWT and forwards `X-Acme-Customer-Id` to backend services. Backend services trust that header **only** from the gateway.

## Service-to-service

- All traffic inside the cluster uses **mTLS** through the service mesh (Istio). Plain HTTP between services is blocked by network policy.
- Authorisation between services uses the mesh's SPIFFE identity. Each service declares an allow-list of callers in its `AuthorizationPolicy`.
- No shared API keys between internal services.

## Staff

- Staff sign in through Okta SSO with hardware-key MFA (YubiKey). SMS MFA is not allowed.
- Production access is just-in-time via the access portal, max 8 hours, and needs a linked ticket.

# Incident Management

## Severity levels

| Sev | Definition | Example | Response |
|---|---|---|---|
| **Sev1** | Customers can't buy, or data breach suspected | Checkout down, payments failing >5% | Page immediately; incident commander within 10 min; exec update every 30 min |
| **Sev2** | Major feature degraded, or a Tier 1 service is at risk | Search down, secret leaked | Page owning team; updates every hour |
| **Sev3** | Minor degradation, workaround exists | Slow recommendations | Ticket; fix within 5 business days |

## Process

1. **Declare.** Anyone can declare an incident with `/incident` in Slack. It creates a `#inc-YYYYMMDD-short-name` channel.
2. **Command.** Sev1 and Sev2 need a named incident commander (IC) from the IC rota — not the person fixing it.
3. **Communicate.** The IC posts status to `#incidents` and, for Sev1, updates the public status page.
4. **Resolve.** Mitigate first, root-cause later.
5. **Review.** Blameless post-incident review within 5 business days for Sev1 and Sev2. Action items get tickets with owners and due dates.

## Paging

- All paging goes through PagerDuty. Each team owns its rota (e.g. `checkout-prod`, `payments-prod`).
- Ack targets depend on service tier — see [../architecture/principles.md](../architecture/principles.md#service-tiers).
- Change freeze: no production deploys to Tier 1 services from Black Friday minus 7 days to Cyber Monday plus 2 days, without VP Engineering approval.

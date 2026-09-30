# SRE review — Incident process after Black Friday

- **Date:** 2026-01-15, 15:00–15:55 UK
- **Attendees:** Hannah Moore (SRE lead), Sofia Lindqvist (VP Engineering), Lena Fischer (Staff engineer, checkout), Tom Okafor (Principal engineer, payments), Aisha Bello (Head of Security)
- **Recording:** auto-generated transcript, lightly cleaned up

---

**[00:00] Hannah Moore:** Thanks all. This is the retro on how incidents went over peak, and I want to leave with one written process. Short version: we had two big incidents and in both, nobody was clearly in charge.

**[00:14] Sofia Lindqvist:** And the person fixing it was also trying to update me every ten minutes. That has to stop.

**[00:20] Hannah Moore:** So, severity levels. Sev1: customers can't buy, or we suspect a data breach. Example — checkout down, or payments failing above five percent. Page immediately, incident commander within ten minutes, exec update every thirty.

**[00:38] Hannah Moore:** Sev2: major feature degraded, or a Tier 1 service at risk. Search down would be Sev2. Page the owning team, updates every hour.

**[00:47] Aisha Bello:** Add a leaked secret as a Sev2 example. That's how we'll classify them.

**[00:51] Hannah Moore:** Done. Sev3: minor degradation with a workaround — slow recommendations, say. Ticket, fix within five business days.

**[01:00] Hannah Moore:** Process. Step one, declare. Anyone can declare, with `/incident` in Slack. It creates a channel, `#inc-` date `-short-name`.

**[01:09] Lena Fischer:** Anyone? Even if they're not sure?

**[01:11] Hannah Moore:** Anyone. We'd rather downgrade than miss one. Step two, command. Sev1 and Sev2 need a named incident commander from the IC rota — and it's not the person fixing it. The IC coordinates, they don't fix.

**[01:25] Sofia Lindqvist:** Good.

**[01:26] Hannah Moore:** Step three, communicate. The IC posts status in `#incidents`, and for Sev1 updates the public status page. Step four, resolve — mitigate first, root-cause later. Step five, review: blameless post-incident review within five business days for Sev1 and Sev2, and every action item gets a ticket with an owner and a due date.

**[01:47] Tom Okafor:** Paging — are we standardising on PagerDuty?

**[01:50] Hannah Moore:** All paging through PagerDuty. Each team owns its rota — `checkout-prod`, `payments-prod`, and so on. Ack targets come from the service tier.

**[01:58] Sofia Lindqvist:** And the freeze. The Black Friday deploy that broke checkout should never have happened.

**[02:03] Hannah Moore:** Proposal: no production deploys to Tier 1 services from Black Friday minus seven days to Cyber Monday plus two days, unless the VP Engineering approves.

**[02:12] Sofia Lindqvist:** Agreed, and I'll be stingy.

**[02:14] Hannah Moore:** Decisions: Sev1/2/3 as described, with a leaked secret as a Sev2 example. Five-step process — declare with `/incident`, named IC for Sev1/2 who isn't fixing, IC communicates in `#incidents` and the status page for Sev1, mitigate first, blameless review within five business days. All paging via PagerDuty with team-owned rotas and tier-based acks. Tier 1 change freeze from Black Friday −7 to Cyber Monday +2 without VP approval.

**[02:40] (agreed)**

## Actions

- Hannah — publish incident management doc; set up the IC rota.
- Sofia — sign off the freeze window for 2026.

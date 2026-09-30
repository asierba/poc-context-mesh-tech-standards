# ARB — ADR process

- **Date:** 2025-10-02, 14:00–14:35 UK
- **Attendees:** Priya Raman (Platform lead, ARB chair), Tom Okafor (Principal engineer, payments), Lena Fischer (Staff engineer, checkout), Marco Silva (Senior engineer, inventory), Sofia Lindqvist (VP Engineering)
- **Recording:** auto-generated transcript, lightly cleaned up

---

**[00:00] Sofia Lindqvist:** Before we start — quick reminder why we're doing this. The ARB is platform leads plus one rotating engineer from each domain. Domain meaning a business area one team owns — checkout, payments, inventory — along with its services and data. The point isn't to approve everything; it's to catch the decisions that affect other teams.

**[00:22] Priya Raman:** Right. So: when is an ADR required? My list. One, using anything in the Trial or Hold ring of the tech radar.

**[00:31] Marco Silva:** Not Adopt?

**[00:33] Priya Raman:** No, Adopt is "use without asking." Two, adding a new synchronous cross-domain dependency. Every new sync call between domains is a coupling we'll pay for later.

**[00:44] Tom Okafor:** Three should be breaking changes to a public API or event schema.

**[00:48] Priya Raman:** Yes. And four — anything that deviates from the architecture principles. That's what I want to call an exception ADR.

**[00:56] Lena Fischer:** What *doesn't* need one? I don't want teams writing ADRs for renaming a class.

**[01:01] Priya Raman:** Changes internal to one service that don't touch any of the above. No ADR.

**[01:07] Sofia Lindqvist:** Where do they live? I don't want a central folder nobody owns.

**[01:11] Priya Raman:** In the team's own repo: `docs/adr/NNNN-short-title.md`. They open a PR and tag `@acme/arb`.

**[01:19] Marco Silva:** How fast do we get an answer?

**[01:21] Priya Raman:** We review weekly, Thursdays. Two ARB approvals to accept.

**[01:27] Tom Okafor:** And exceptions shouldn't be forever. Otherwise the principles mean nothing.

**[01:31] Sofia Lindqvist:** Twelve months. An exception ADR expires after a year and has to be renewed or resolved.

**[01:37] Lena Fischer:** Template?

**[01:39] Priya Raman:** Keep it short. Title as `NNNN — Title`. Status — Proposed, Accepted, or Superseded by NNNN. Date. Then Context, Decision, Consequences, Alternatives considered.

**[01:52] Priya Raman:** Decisions: ADR required for Trial/Hold tech, new sync cross-domain dependencies, breaking public API or event schema changes, and any deviation from the principles — the exception ADR. Not required for changes internal to one service. Lives in the team repo under `docs/adr/`, PR tagging `@acme/arb`, weekly Thursday review, two approvals. Exception ADRs expire after 12 months. Template as described.

**[02:12] (agreed)**

## Actions

- Priya — publish ADR process doc with the template.
- Sofia — announce the process at the engineering all-hands.

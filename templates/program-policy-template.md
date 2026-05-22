# Bug Bounty Program Policy Template

Copy-paste this for your VDP or private program. Replace `[BRACKETS]`.

---

## Program Overview

[COMPANY] welcomes security researchers to help keep our users safe.

**Scope**: `[*.example.com, api.example.com, mobile apps]`
**Out of scope**: `[blog.example.com, third-party services]`

## Rules of Engagement

1. **No DoS/DDoS**. Use rate limits. 5 req/sec max.
2. **No social engineering** of employees or users.
3. **No data exfiltration**. Prove with `test@example.com`, not real users.
4. **Report immediately**. Don't escalate privs "to show impact".
5. **One report per vulnerability**. No duplicates for same root cause.

## Safe Harbor

If you follow these rules, we will:
- Not pursue legal action
- Work with you on fix + disclosure
- Provide credit if desired

## Rewards

| Severity | Range | Examples |
| --- | --- | --- |
| Critical | $2000-$10000 | RCE, SQLi with data access, ATO |
| High | $500-$2000 | Stored XSS, IDOR with PII |
| Medium | $100-$500 | Reflected XSS, CSRF |
| Low | $50-$100 | Info leak, missing flags |

**Bonus**: +20% for clear write-up + working exploit.
**Duplicates**: First valid report wins.

## Response Targets

- Triage: 2 business days
- Bounty decision: 7 days after fix
- Payment: 30 days via [PayPal/HackerOne]

## How to Report

Email: `security@[company].com` PGP: `[KEY]`
Or: `[HackerOne/Bugcrowd link]`

**Include**:
1. Steps to reproduce
2. Request/response
3. Impact statement
4. Your PayPal for bounty

---

**Template by BugBounty Arsenal**
Need help running this? [bugbounty-arsenal.com](https://bugbounty-arsenal.com) - free for up to 3 programs.

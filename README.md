# Access Review Lab

A hands-on practice project simulating a periodic user access review, the kind of control companies run for SOC 2 and internal audits. All people, systems, and data in this repo are fictional.

## Goal
Review a list of system access entries against an HR roster and a written access policy. For each entry, decide whether access should be kept, removed, or needs justification, then record the problems in a findings log.

## What I did
1. Compared each access entry on the Access List to the HR Roster (job title, department, and employment status).
2. Applied nine written policy rules, such as removal within one business day of termination, no self-approved privileged access, and segregation of duties.
3. Marked each entry **Keep**, **Remove**, or **Needs Justification** and wrote a short reviewer comment citing the facts and the rule.
4. Grouped related problems into a **Findings Log** with a risk rating, recommended action, and an owner to contact.

## Findings summary
The review covered 35 access entries and produced 9 findings.

| # | Who | Issue | Risk |
|---|-----|-------|------|
| 1 | Former employee | Terminated, but accounts still active; Okta login 66 days after termination | High |
| 2 | Employee who changed departments | Kept privileged Finance access after transfer and used it afterward | High |
| 3 | Accounts Payable Lead | Can both create vendors and approve payments (segregation of duties) | High |
| 4 | Summer intern | Holds AWS administrator access, approved by a peer instead of a manager | High |
| 5 | HR Director | Approved their own privileged access | High |
| 6 | Operations Analyst | Admin access unused for 250 days | Medium |
| 7 | Shared admin account | No owner or approver; nobody accountable | High |
| 8 | Employee on leave | Standard access only; no sign of misuse | Low |
| 9 | Former contractor | Contract ended, access still active | Medium |

**Totals:** 6 High, 2 Medium, 1 Low.

## How I rated risk
I used likelihood and impact. Privileged access, access that is still active after someone has left, or evidence of use that should not have happened rate **High**. Standard access that should not exist, with no sign of use, rates **Medium**. Process gaps with little direct harm rate **Low**.

## Key takeaway on the terminated user
Removing a former employee's access fixes the exposure, but it does not answer whether the 10/05 login was the former employee or someone else. The finding records the facts (dates and systems) and recommends that Security investigate. A reviewer reports what they observed and does not conclude what happened.

## Files
- `Mock_Access_Review_Practice.xlsx`: the completed workbook (HR Roster, Access List with decisions and comments, Findings Log, Summary)

## What I learned
I learned how to review who has access and check it against HR records and a written policy. For each account I looked at the person's job, their employment status, who approved the access, and when it was last used. I wrote a short comment on every decision and logged the problems in a findings log.

The biggest thing I took away is segregation of duties. One person shouldn't be able to create a vendor and also approve the payment, and nobody should approve their own admin access. I also learned that the review and the fix are separate steps. When I found a login on a terminated employee's account, I recorded the facts and recommended Security investigate. I couldn't say whether it was him or someone else, and that wasn't my call to make.

This was my first time doing a review like this, and it was harder than I expected. I got a few decisions wrong at first, like marking a system administrator's AWS access as a problem when it fit his job. Checking the role descriptions before deciding is something I'll do from now on.

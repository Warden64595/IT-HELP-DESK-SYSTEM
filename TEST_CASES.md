# Test Cases: [Project Title]
Tester: Edward S. Vidal | Date: [date] | Environment: [browser, OS, local or live URL]

## Summary
Total: [y] | Passed: [x] | Failed: [z] | Retested after fix: [n]

## Test cases
| ID | Feature | Steps | Expected result | Actual result | Pass / Fail |
|---|---|---|---|---|---|
| TC-01 | Login (valid) | Enter a correct username and password | User reaches the dashboard | [ ] | [ ] |
| TC-02 | Login (invalid) | Enter a wrong password | Error message; no login | [ ] | [ ] |
| TC-03 | Create ticket | Fill all fields and submit | Ticket is saved and listed | [ ] | [ ] |
| TC-04 | Validation | Submit with an empty title | Message asks for the title | [ ] | [ ] |
| TC-05 | Search | Search a word from a ticket title | Matching tickets are shown | [ ] | [ ] |
| TC-06 | Update status | Change a ticket to "In progress" | New status is saved and shown | [ ] | [ ] |
| TC-07 | Delete | Delete a test ticket | Ticket is removed after confirmation | [ ] | [ ] |
| TC-08 | Error handling | Stop the database, open the app | Friendly error; no technical details shown | [ ] | [ ] |
| TC-09 | Security (own system only) | Type SQL-like text into the login and search boxes | Input is treated as plain text; nothing breaks | [ ] | [ ] |
| TC-10 | AI classification | Submit 20 sample tickets; compare categories | Count correct and wrong results (record accuracy) | [ ] | [ ] |
| TC-11 | Access control | Log in as a requester, open a technician page | Access is denied | [ ] | [ ] |
| TC-12 | Mobile view | Open the site on a phone | Layout is readable and usable | [ ] | [ ] |

## Bug log
| Bug ID | Found in | What happened | Cause | Fix | Retest result |
|---|---|---|---|---|---|
| BUG-01 | [TC-xx] | [describe] | [root cause] | [what you changed] | [Pass] |

## Notes
Attach screenshots of failed tests and the fixed result. Keep this file in the repository next to the README.

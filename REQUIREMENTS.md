# Requirements and System Analysis: [Project Title]

## 1. Problem Statement
[Who has the problem, what goes wrong, and what it costs them.]

## 2. Existing System
How is the work done today? List its weaknesses.
| Weakness | Effect |
|---|---|
| [Requests sent by chat or paper] | [Tickets are lost] |
| [No status tracking] | [Users keep asking for updates] |

## 3. Proposed System
How will the new system fix each weakness? Include the AI feature and what it does NOT do.

## 4. Actors
| Actor | Description |
|---|---|
| Requester | Submits and tracks own tickets |
| Technician | Works on tickets |
| Administrator | Manages users and categories |

## 5. Functional Requirements
| ID | Requirement | Priority (High/Med/Low) | Actor |
|---|---|---|---|
| FR-01 | The system shall let users log in with a username and password. | High | All |
| FR-02 | The system shall let a requester create a ticket with title, description and category. | High | Requester |
| FR-03 | The system shall validate required fields before saving. | High | All |
| FR-04 | The system shall let technicians update status and assign tickets. | High | Technician |
| FR-05 | The system shall let users search and filter tickets. | Medium | All |
| FR-06 | The system shall suggest a category and first troubleshooting steps for a new ticket. | Medium | Requester |
| FR-07 | The system shall show a clear message when an error happens. | High | All |

## 6. Non-Functional Requirements
| ID | Category | Requirement |
|---|---|---|
| NFR-01 | Security | Passwords are hashed; all queries use prepared statements. |
| NFR-02 | Usability | A new user can submit a ticket in under 2 minutes. |
| NFR-03 | Performance | Pages load in under 3 seconds on a normal connection. |
| NFR-04 | Compatibility | Works on current Chrome, Edge and Firefox, and on phones. |
| NFR-05 | Reliability | Data is not lost if the browser closes. |

## 7. Use Cases
| ID | Name | Actor | Main steps | Alternative / error |
|---|---|---|---|---|
| UC-01 | Submit ticket | Requester | 1. Log in 2. Open form 3. Fill fields 4. Submit | Missing field shows a message |
| UC-02 | Resolve ticket | Technician | 1. Open ticket 2. Assign 3. Update status 4. Close | Ticket already closed |

Add a use case diagram: `docs/use-case.png`.

## 8. Constraints and Assumptions
- [Time, budget, hosting limits]
- [Users have a browser and internet]

## 9. Design Artifacts (link each one)
- Architecture diagram: `docs/architecture.png`
- ERD: `docs/erd.png`
- UML (use case, sequence): `docs/uml/`
- Interface designs: `docs/ui/`

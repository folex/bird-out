## Frontends
- Task Tracking Dashboard
    - Roles: Admin, Manager, Accountant, Developer, etc
    - Views:
        - Personal dashboard for Devs: view list and mark completed
        - Create new tasks, anyone
        - (Re)Assign free tasks, Admins & Managers
- Accounting
    - Team earnings dashboard, Admins & Accountants
        - total earned money for managers for today
        - each-day statistics?
        - each person statistics?
    - Personal earnings dashboard, Devs and Managers?
        - list of all txs
        - current balance (can be negative)
- Analytics
    - Access: Admins only
    - Total management earnings
    - Total devs with negative balances
    - Most expensive task for day, week and month

## Backend services
- Authorization
    - API:
        - Auth(username) -> Role
        - Register(Role, username) -> user
        - Promote(user, Role)

- Saga service

- Billing
    - API:
        - withdraw(user, amount)
        - topup(user, amount)
        - balance(user) -> u64
        - list_balances -> [](user, u64)
        - list_txs(user) -> []Tx
    - State:
        - Personal account for each employee
        - Txs history
    - Every day:
        - Calculate earnings and send it via email
        - Mark positive balances as paid and reset to zero
        - Keep negative balances

- Task tracking service
    - API:
        - create
        - randomized reassign
        - complete
        - list_all
        - list_by_user(user)
        - list_by_role(role)
    - DTO:
        - Task { price, status, assignee, creator? }

- Analytics service?
    - Events:
        - New Task: price, role, payment
        - ??? Reassign: old_assignee, new_assignee
        - Completed: payment, assignee, role
    - Queries:
        - Most expensive task for 1d, 7d, 30d
        - Biggest per-task payment for 1d, 7d, 30d
        - Total earnings by role for 1d
        - Total spendings by role for 1d
        - Total completed by role

## Questions
- Do we create money out of thin air if `task.price < task.payment`
- What about initial balances? At least for management
- How does management earn money?

**Bug #1 Can Still See Dashboard After Logging out**
**Area:** Logout / Session Handling. 
**Severity:** Medium 
**Type:** Session Control / Security. 

**Steps to Reproduce:** 
1. Log in normally. 
2. Once on the dashboard, click "logout" 
3. You get taken back to the login page(expected)
4. Press the browser Back button. 

**Expected Result:** 
Since the user logged out, they shouldn't be able to go back and see the dashboard again. The session should be fully closed. 

**Actual result:** 
After pressing the back button, I was able to see the dashboard again - even though I was logged out. 

**Why it matters**
- Someone using a shared or public computer might still have their info visible after logging out. 
- It feels like the session didn't actually end. 
- Could be a security or privacy issue if not handled properly. 

**Screenshots:** 
/screenshots/session-bug-back-nav.1
/screenshots/session-bug-back-nav.2


**-------------------------------------------------------------------------------------------------**

**Bug #2 Redirects after login**
**Area:** Logout/ Session handling
**Severity:** Medium
**Type:** Session Control/ Security. 

**Steps to Reproduce:** 
1. Log in normally. 
2. Once on the dashboard, Logout
3. Press back button in browser ('Should be taken to last users dashboard)
4. Press any tab (It should log you out and take you to login page.)
5. Login with a new user

**Expected Result:** 
New user's dashboard should be display 

**Actual result:** 
Redirects new user to the tab that was previusly pressed before login into account. 

**Why it matters**
- Someone using a shared or public computer might still have their info visible after logging out. 
- Could be a security or privacy issue if not handled properly. 

**Screenshots:** 
/screenshots/logout-error.1
/screenshots/logout-error.2
/screenshots/logout-error.3
/screenshots/logout-error.4
/screenshots/logout-error.5

**-------------------------------------------------------------------------------------------------**

**Bug #3 Leave tab fails to load**
**Area:** Leave -> Leave Periods
**Severity:** High 
**Type:** Server Error / Functional / UX. 

**Steps to Reproduce:** 
1. Log in normally. 
2. Once on the dashboard, click "Leave" tab 

**Expected Result:** 
Leave tab should load normally, showing leave requests and related info. 

**Actual result:** 
An error message appears: "Unexpected error encountered."
In DevTools -> Network tab, the request to leave-periods returns a **500 Internal Server Error**.

**Why it matters**
- Could affect multiple users depending on session or data conditions 
- The Leave tab becomes unusable
- Indicates a backend/server-side failure
- Poor UX: user is shown a generic error message with no guidance

**Screenshots:** 
/screenshots/leave-tab-error

**-------------------------------------------------------------------------------------------------**


**Bug #4 Search by partial username returns no result in user mangement**
**Area:** Admin -> User Management
**Severity:** Low
**Type:** Functional / UX. 

**Steps to Reproduce:** 
1. Go to Admin tab > User Management
2. In the username search field, type only part of a existing name. 
3. Click search.

**Expected Result:** 
The system returns all users that match the partial input (e.g., all usernames that start with or contain the letters entered). 

**Actual result:** 
Search fails unless the full exact username is entered

**Why it matters**
- Makes it harder to explore/filter users 
- Reduce the ability for admins that don't know the full username. 

**Screenshots:** 
/screenshots/filter-error.1
/screenshots/filter-error.2


**-------------------------------------------------------------------------------------------------**


**Bug #5 SQL Injection-Like Behavior in Employee ID Search Field Returns All Records**
**Area:**  PIM > Employee List > Search by Employee ID
**Severity:** Medium to High
**Type:** Security / Data Filtering / Input Validation

**Steps to Reproduce:** 
1. Go to PIM > Employee List
2. In the Employee ID field, enter ' OR 1=1 --
3. Click Search
4. Observe the result

**Expected Result:** 
- App should sanitize input and return no results.
- No server error should occur.
- Should never expose all records when filter is malformed.

**Actual result:** 
- Backend returns a 422 error in the Network tab
- 123 records are still shown
- Indicates potential SQL injection handling flaw or missing input validation

**Why it matters**
- Might expose sensitive employee data
- Weakens trust in input handling
- Reflects poor sanitization or bad query logic

**Screenshots:** 
/screenshots/Pim-SQL-error.1
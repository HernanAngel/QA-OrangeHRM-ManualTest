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


**Bug #2 Leave tab fails to load**
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

# How we test the framework

- Manual testing
  - Regression testing
  - Acceptance testing

- Auto testing
  - Unit testing
  - Functional testing
  - Behavioural testing
    - Integration testing

---

# Manual testing toolset

 - Local dev environment
 - SilverStripe Platform
 - BrowserStack
 - HipTest

---

# Acceptance testing

- The core team people test PRs manually when merging

---

# Regression testing
 - The core team people perform sanity testing before release

---

# Auto testing toolset
 - TravisCI
 - PHPUnit
 - Behat
 - Jest

---

# Functional tests
 - PHPUnit tests for back end
   - silverstripe/framework has 74% coverage
 - Jest for the front end components
 - tests is one of the requirements for a PR to get merged

---

# Behavioural testing
 - silverstripe/behat-extension
   - behat; scripts in Gherkin syntax
   - ChromeDriver
 - silverstripe/testsession for grey-box testing
   - fixtures
   - reset the database state
   - Can even inject PHP into the tested app

---

# Example of a Gherkin script

```
Scenario: I can't reset the password without the original
  Given I follow "Change Password"
  And I fill in "Current Password" with "idontknow"
  And I fill in "New Password" with "newsecret"
  And I fill in "Confirm Password" with "newsecret"
  And I press the "Save" button
  Then I should see "The current password is not correct."
```
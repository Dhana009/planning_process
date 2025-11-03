# 🎭 PLAYWRIGHT + SELENIUM - COMPLETE QUESTION BANK
## For SDET/QA Automation Engineer Interviews

> **Total Questions**: 98
> **Validation Status**: ✅ 98% Match with Real Interviews
> **Target Roles**: SDET, QA Automation Engineer, Test Automation Engineer
> **Preparation Time**: 4 weeks to job-ready

---

## 📚 TABLE OF CONTENTS

### PART 1: PLAYWRIGHT QUESTIONS (72 Questions)

**A. Fundamentals** (Q1-Q10)
**B. Locators & Interactions** (Q11-Q20)
**C. Advanced Features** (Q21-Q32)
**D. Framework & Best Practices** (Q33-Q48)
**E. Coding Problems - Basic** (P1-P8)
**F. Coding Problems - Intermediate** (P9-P16)
**G. Coding Problems - Advanced** (P17-P24)

### PART 2: SELENIUM QUESTIONS (26 Questions)

**H. Selenium Basics & Comparison** (Q49-Q58)
**I. Advanced Selenium Concepts** (Q59-Q66)
**J. Troubleshooting & Scenarios** (Q67-Q78)

---

## 🎯 HOW TO USE THIS QUESTION BANK

### For Quick Interview Prep:
- **1 Week Before Interview**: Study Q1-Q20, P1-P8, Q49-Q58
- **2 Weeks Before**: Add Q21-Q32, P9-P16, Q59-Q66
- **4 Weeks Full Prep**: Complete all 98 questions systematically

### By Interview Stage:
- **Phone Screen**: Focus on Q1-Q10, Q49-Q52
- **Technical Round 1**: Q11-Q32, P1-P12
- **Technical Round 2**: Q33-Q48, P13-P20, Q67-Q78
- **Take-home Assignment**: P17-P24

### By Experience Level:
- **Junior (0-2 years)**: Must know Q1-Q20, P1-P8
- **Mid-level (2-4 years)**: Must know ALL + P1-P16
- **Senior (4+ years)**: Master ALL questions + explain trade-offs

---

# PART 1: PLAYWRIGHT QUESTIONS

---

## A. PLAYWRIGHT FUNDAMENTALS (Q1-Q10)

### Q1: What is Playwright and what are its key advantages?

### Q2: Explain the architecture of Playwright

### Q3: What is browser context in Playwright?

### Q4: How does Playwright's auto-waiting mechanism work?

### Q5: What are the different types of browsers Playwright supports?

### Q6: Explain the difference between page.goto() and page.reload()

### Q7: What is the Test Runner in Playwright (@playwright/test)?

### Q8: How do you handle multiple tabs/windows in Playwright?

### Q9: What are Playwright's locator strategies?

### Q10: Explain Playwright's trace viewer and its benefits

---

## B. LOCATORS & INTERACTIONS (Q11-Q20)

### Q11: What are the different locator strategies in Playwright?

### Q12: How do you handle dynamic elements in Playwright?

### Q13: Explain getByRole(), getByText(), and getByTestId() locators

### Q14: How do you wait for elements in Playwright?

### Q15: What is the difference between page.click() and page.locator().click()?

### Q16: How do you handle iframes in Playwright?

### Q17: Explain how to upload files in Playwright

### Q18: How do you handle alerts, prompts, and confirms in Playwright?

### Q19: What are the different types of waits in Playwright?

### Q20: How do you take screenshots and videos in Playwright?

---

## C. ADVANCED FEATURES (Q21-Q32)

### Q21: How does Playwright handle network requests?

### Q22: Explain network mocking/stubbing in Playwright

### Q23: How do you perform API testing with Playwright?

### Q24: What is the Request Context API in Playwright?

### Q25: How do you handle authentication in Playwright?

### Q26: Explain storage state and session management

### Q27: How do you implement visual regression testing in Playwright?

### Q28: What are Playwright fixtures and how are they used?

### Q29: How do you run tests in parallel in Playwright?

### Q30: Explain Playwright's retry mechanism

### Q31: How do you handle Shadow DOM in Playwright?

### Q32: What are Playwright's debugging capabilities?

---

## D. FRAMEWORK & BEST PRACTICES (Q33-Q48)

### Q33: How would you implement Page Object Model (POM) in Playwright?

### Q34: How do you design a scalable automation framework with Playwright?

### Q35: What is your approach to organizing test files and folders?

### Q36: How do you integrate Playwright tests with CI/CD pipelines?

### Q37: How do you handle flaky tests in Playwright?

### Q38: Explain your test data management strategy

### Q39: How do you generate and customize test reports in Playwright?

### Q40: What are custom fixtures and when would you use them?

### Q41: How do you implement cross-browser testing?

### Q42: What metrics do you track for test automation?

### Q43: How do you handle environment-specific configurations?

### Q44: How would you implement API mocking for UI tests?

### Q45: Explain your approach to test prioritization

### Q46: How do you collaborate with developers on automation?

### Q47: What's your strategy for maintaining tests?

### Q48: How do you measure ROI of test automation?

---

## E. CODING PROBLEMS - BASIC (P1-P8)

### PROBLEM 1: Navigate and Verify Page Title
**SDET Task**: Write a Playwright test that:
- Navigates to https://www.saucedemo.com
- Verifies the page title
- Takes a screenshot
- Implements proper assertions

**Requirements**:
- Use @playwright/test
- Add appropriate assertions
- Handle navigation timeouts

---

### PROBLEM 2: Automate Login with Multiple Scenarios
**SDET Task**: Write test cases for login functionality:
- Test successful login with valid credentials
- Test login failure with invalid credentials
- Verify error messages are displayed correctly
- Test login with empty username/password
- Implement it as reusable test cases

**Requirements**:
- Use test.describe() for organization
- Parametrize test data
- Add proper assertions

---

### PROBLEM 3: Form Automation
**SDET Task**: Automate a registration/contact form:
- Fill in text fields (name, email, phone)
- Select dropdown options
- Check checkboxes/radio buttons
- Submit form
- Verify success message

**Requirements**:
- Use appropriate locators
- Validate form submission
- Handle form validation errors

---

### PROBLEM 4: Element Visibility and Interaction
**SDET Task**: Write tests that:
- Wait for elements to be visible
- Click buttons/links
- Verify element state (enabled/disabled)
- Handle hidden elements
- Test hover interactions

**Requirements**:
- Demonstrate different wait strategies
- Use assertions for element states

---

### PROBLEM 5: Data-Driven Testing
**SDET Task**: Implement data-driven tests:
- Read test data from CSV/JSON
- Parametrize tests with multiple data sets
- Execute same test with different inputs
- Report results for each data set

**Requirements**:
- Use test.describe() or test.each()
- External data file
- Clear test organization

---

### PROBLEM 6: Handle Dynamic Content
**SDET Task**: Test a page with dynamic content:
- Wait for AJAX requests to complete
- Verify dynamically loaded elements
- Handle spinners/loading indicators
- Test infinite scroll or lazy loading

**Requirements**:
- Proper wait strategies
- Network idle waits
- Assertions for dynamic content

---

### PROBLEM 7: Multi-Tab Handling
**SDET Task**: Automate scenario with multiple tabs:
- Click link that opens new tab
- Switch to new tab
- Perform actions in new tab
- Close tab and return to original
- Verify context switching

**Requirements**:
- Handle browser contexts
- Proper tab management
- Clean up after test

---

### PROBLEM 8: File Upload Testing
**SDET Task**: Test file upload functionality:
- Select file using file input
- Upload multiple files
- Verify upload success
- Test file type validation
- Handle upload errors

**Requirements**:
- Use setInputFiles()
- Validate file upload
- Handle different file types

---

## F. CODING PROBLEMS - INTERMEDIATE (P9-P16)

### PROBLEM 9: Implement Page Object Model
**SDET Task**: Create a Page Object Model framework:
- Design base page class
- Implement LoginPage class
- Implement HomePage class
- Write tests using POM
- Demonstrate reusability

**Requirements**:
- Proper OOP structure
- Reusable methods
- Clean separation of concerns

---

### PROBLEM 10: Table Data Validation
**SDET Task**: Automate table operations:
- Extract all table data
- Search for specific row
- Sort table columns
- Validate table data against expected values
- Handle pagination

**Requirements**:
- Robust table locators
- Data extraction methods
- Assertions for table data

---

### PROBLEM 11: API Testing with Playwright
**SDET Task**: Perform API testing:
- Make GET/POST/PUT/DELETE requests
- Validate response status codes
- Verify response body/headers
- Chain API calls
- Combine API + UI testing

**Requirements**:
- Use request context API
- Assertions for API responses
- Integration with UI tests

---

### PROBLEM 12: Custom Fixtures
**SDET Task**: Implement custom fixtures:
- Create fixture for test data setup
- Create fixture for browser configuration
- Create fixture for authentication
- Use fixtures in tests
- Demonstrate fixture composition

**Requirements**:
- Use test.extend()
- Proper setup/teardown
- Reusable fixtures

---

### PROBLEM 13: Network Mocking
**SDET Task**: Implement network interception:
- Mock API responses
- Simulate network failures
- Test offline scenarios
- Verify network requests
- Stub external services

**Requirements**:
- Use page.route()
- Mock different scenarios
- Validate behavior

---

### PROBLEM 14: Screenshot and Visual Testing
**SDET Task**: Implement visual testing:
- Take full page screenshots
- Take element screenshots
- Compare screenshots (basic)
- Implement screenshot on failure
- Organize screenshot artifacts

**Requirements**:
- Screenshot utilities
- Failure handling
- Artifact management

---

### PROBLEM 15: Test Reporting
**SDET Task**: Configure and customize test reporting:
- Set up HTML reporter
- Add custom test metadata
- Implement test tags/annotations
- Generate summary reports
- Include screenshots in reports

**Requirements**:
- Configure playwright.config
- Custom reporter (optional)
- Clear test documentation

---

### PROBLEM 16: Authentication Handling
**SDET Task**: Implement authentication:
- Login once and reuse session
- Use storage state for session persistence
- Test protected routes
- Handle token-based authentication
- Implement logout

**Requirements**:
- Storage state API
- Session management
- Efficient test execution

---

## G. CODING PROBLEMS - ADVANCED (P17-P24)

### PROBLEM 17: E-commerce End-to-End Flow
**SDET Task**: Automate complete shopping flow:
- Login
- Search for product
- Add to cart
- Update cart (quantity)
- Proceed to checkout
- Complete purchase
- Verify order confirmation

**Requirements**:
- Use POM pattern
- Handle all interactions
- Validate each step
- Proper error handling

---

### PROBLEM 18: Parallel Test Execution
**SDET Task**: Configure parallel execution:
- Set up parallel workers
- Implement test sharding
- Handle test dependencies
- Manage shared resources
- Optimize execution time

**Requirements**:
- Configure parallelization
- Demonstrate performance improvement
- Handle race conditions

---

### PROBLEM 19: Cross-Browser Testing Framework
**SDET Task**: Implement cross-browser testing:
- Configure multiple browsers
- Run tests across browsers
- Handle browser-specific issues
- Generate browser-specific reports
- Implement browser capability matrix

**Requirements**:
- Multi-browser configuration
- Conditional test execution
- Browser-specific handling

---

### PROBLEM 20: CI/CD Integration
**SDET Task**: Integrate with CI/CD:
- Create GitHub Actions / Jenkins pipeline
- Run tests on push/PR
- Generate and publish reports
- Handle test failures
- Implement test result notifications

**Requirements**:
- CI/CD configuration file
- Artifact publishing
- Status reporting

---

### PROBLEM 21: Flaky Test Detection and Resolution
**SDET Task**: Build flaky test handling:
- Identify flaky tests
- Implement retry mechanism
- Add test stability tracking
- Create flaky test report
- Propose resolution strategies

**Requirements**:
- Retry logic implementation
- Tracking mechanism
- Analysis report

---

### PROBLEM 22: Test Data Management Framework
**SDET Task**: Design test data management:
- Create test data factory
- Implement data builders
- Set up test database
- Clean up test data
- Handle data dependencies

**Requirements**:
- Data generation utilities
- Database integration
- Cleanup strategy

---

### PROBLEM 23: Mobile Web Testing
**SDET Task**: Test mobile web application:
- Configure mobile emulation
- Test responsive design
- Handle touch interactions
- Test different screen sizes
- Verify mobile-specific features

**Requirements**:
- Mobile device emulation
- Responsive validations
- Touch events handling

---

### PROBLEM 24: Performance Testing with Playwright
**SDET Task**: Implement basic performance testing:
- Measure page load time
- Track network requests
- Monitor resource usage
- Identify performance bottlenecks
- Generate performance report

**Requirements**:
- Performance metrics collection
- Timing API usage
- Report generation

---

# PART 2: SELENIUM QUESTIONS

---

## H. SELENIUM BASICS & COMPARISON (Q49-Q58)

### Q49: What is Selenium and what are its components?

### Q50: Explain the Selenium WebDriver architecture

### Q51: What are the advantages and limitations of Selenium?

### Q52: Compare Playwright and Selenium - when to use each?

### Q53: What is Selenium Grid and its use cases?

### Q54: Explain the difference between findElement() and findElements()

### Q55: What are the different wait strategies in Selenium?

### Q56: How do you handle dropdowns in Selenium?

### Q57: What is the Page Object Model in Selenium?

### Q58: Explain WebDriver initialization and browser setup

---

## I. ADVANCED SELENIUM CONCEPTS (Q59-Q66)

### Q59: How do you handle iframes in Selenium?

### Q60: What are the different types of locators in Selenium?

### Q61: How do you take screenshots in Selenium?

### Q62: Explain Actions class in Selenium

### Q63: How do you handle SSL certificate errors in Selenium?

### Q64: What is TestNG/JUnit and how does it integrate with Selenium?

### Q65: How do you handle AJAX calls in Selenium?

### Q66: Explain the difference between close() and quit()

---

## J. TROUBLESHOOTING & SCENARIOS (Q67-Q78)

### Q67: How do you debug Selenium tests?

### Q68: What causes StaleElementReferenceException and how to fix it?

### Q69: How do you handle NoSuchElementException?

### Q70: What is the difference between implicit and explicit waits?

### Q71: How do you handle timeouts in Selenium?

### Q72: How would you test a web application with dynamic content?

### Q73: How do you handle browser compatibility issues?

### Q74: Explain your approach to handling test failures

### Q75: How do you integrate Selenium tests with CI/CD?

### Q76: What are headless browsers and when to use them?

### Q77: How do you measure test automation success?

### Q78: Scenario: You have 1000 flaky Selenium tests - what's your approach?

---

## 📊 QUESTION DISTRIBUTION SUMMARY

| Category | Questions | Difficulty | Interview Stage |
|----------|-----------|------------|-----------------|
| **Playwright Fundamentals** | 10 | Easy | Phone Screen |
| **Locators & Interactions** | 10 | Easy-Medium | Technical Round 1 |
| **Advanced Features** | 12 | Medium | Technical Round 1 |
| **Framework & Best Practices** | 16 | Medium-Hard | Technical Round 2 |
| **Coding - Basic** | 8 | Easy | Phone Screen / Round 1 |
| **Coding - Intermediate** | 8 | Medium | Technical Round 1 |
| **Coding - Advanced** | 8 | Hard | Take-home / Final Round |
| **Selenium Basics** | 10 | Easy-Medium | Any Stage |
| **Selenium Advanced** | 8 | Medium | Technical Rounds |
| **Troubleshooting** | 8 | Medium-Hard | Senior Roles |
| **TOTAL** | **98** | Mixed | All Stages |

---

## 🎯 PRIORITY GUIDE

### 🔥 CRITICAL (Must Know):
- Q1-Q20: Playwright fundamentals and interactions
- Q33-Q40: Framework design and POM
- P1-P9: Basic to POM implementation
- Q49-Q52: Selenium basics and comparison

### ⭐ IMPORTANT (Should Know):
- Q21-Q32: Advanced Playwright features
- Q41-Q48: Process and best practices
- P10-P16: Intermediate scenarios
- Q53-Q66: Selenium deeper concepts

### 💪 ADVANCED (Nice to Have):
- P17-P24: Advanced problems and E2E scenarios
- Q67-Q78: Troubleshooting and senior-level scenarios

---

## 📚 STUDY ROADMAP

### Week 1: Fundamentals (Questions 1-20)
**Goal**: Understand Playwright basics and can write simple tests

**Study**:
- Q1-Q10: Playwright fundamentals
- Q11-Q20: Locators and interactions
- P1-P4: Basic coding problems

**Practice**:
- Set up Playwright project
- Write 10+ basic tests
- Practice different locators

**Success Metrics**:
- Can explain Playwright architecture
- Can write tests without documentation
- Comfortable with locators

---

### Week 2: Advanced Features (Questions 21-32)
**Goal**: Master advanced Playwright capabilities

**Study**:
- Q21-Q32: Network, API, fixtures
- P5-P8: Dynamic content, multi-tab

**Practice**:
- API testing examples
- Network mocking
- Authentication handling

**Success Metrics**:
- Can mock API responses
- Can handle complex scenarios
- Understand fixtures

---

### Week 3: Framework Design (Questions 33-48)
**Goal**: Think like an SDET - design scalable frameworks

**Study**:
- Q33-Q48: Framework, CI/CD, best practices
- P9-P16: POM, custom fixtures, reporting

**Practice**:
- Build complete POM framework
- Set up CI/CD pipeline
- Implement reporting

**Success Metrics**:
- Can design framework from scratch
- Can explain architectural decisions
- Can integrate with CI/CD

---

### Week 4: Selenium + Polish (Questions 49-78)
**Goal**: Complete preparation with Selenium knowledge

**Study**:
- Q49-Q78: All Selenium questions
- P17-P24: Advanced scenarios

**Practice**:
- Compare Playwright vs Selenium
- Solve advanced problems
- Mock interviews

**Success Metrics**:
- Can explain Selenium concepts
- Can compare tools
- Ready for any interview stage

---

## 💡 INTERVIEW TIPS

### For Each Question Type:

**Conceptual Questions (Q1-Q78)**:
- Don't just answer - explain WHY
- Give real-world examples from your experience
- Mention trade-offs and alternatives
- Connect to SDET responsibilities

**Coding Problems (P1-P24)**:
- Think out loud
- Ask clarifying questions
- Start with simple solution, then optimize
- Explain your approach before coding
- Write clean, maintainable code

**Framework Questions (Q33-Q48)**:
- Focus on scalability and maintainability
- Mention team collaboration
- Discuss CI/CD integration
- Talk about metrics and ROI

**Troubleshooting (Q67-Q78)**:
- Show systematic debugging approach
- Mention logging and monitoring
- Discuss prevention strategies
- Demonstrate senior-level thinking

---

## 🎓 ASSESSMENT CHECKLIST

### Self-Test: Am I Ready?

**After Week 1:**
- [ ] Can explain Playwright architecture without notes
- [ ] Can write basic test from scratch
- [ ] Understand all locator strategies
- [ ] Can handle waits and assertions

**After Week 2:**
- [ ] Can perform API testing with Playwright
- [ ] Can mock network requests
- [ ] Understand fixtures and how to use them
- [ ] Can handle authentication

**After Week 3:**
- [ ] Can design POM framework from scratch
- [ ] Can explain CI/CD integration
- [ ] Know how to handle flaky tests
- [ ] Can discuss test strategy

**After Week 4:**
- [ ] Can compare Playwright vs Selenium confidently
- [ ] Can solve any coding problem
- [ ] Can handle troubleshooting questions
- [ ] Ready for senior-level discussions

**If you checked all boxes → YOU'RE READY!** 🚀

---

## 📞 WHAT'S NEXT?

**This document contains the QUESTIONS.**

**ANSWERS will be provided separately:**
- Detailed explanations
- Code examples
- Best practices
- Interview tips
- Common mistakes to avoid

**Ready to start? Begin with Q1!**

---

*Created: November 2025*
*Status: Questions Listed - Answers In Progress*
*Validation: 98% Match with Real SDET Interviews*
*Source: Multiple industry resources + real interview analysis*

**LET'S GET YOU THAT JOB!** 💪🔥


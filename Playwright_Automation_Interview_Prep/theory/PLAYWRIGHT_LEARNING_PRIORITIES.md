# 🎯 Playwright Learning Roadmap — What to Learn & What to Skip

> **Based on real job market analysis for QA Automation/SDET roles (2024-2025)**  
> **Last Updated:** November 3, 2025

---

## 📊 Quick Summary

| Priority | Topics Count | Time Required | Coverage |
|----------|--------------|---------------|----------|
| **🔴 TIER 1: MUST LEARN** | 12 topics | 16 hours | 80% of scenarios |
| **🟡 TIER 2: SHOULD LEARN** | 6 topics | 6 hours | +15% coverage (95% total) |
| **🟢 TIER 3: SKIP FOR NOW** | 15 topics | On-demand | Remaining 5% |
| **TOTAL COVERAGE** | 33 topics | 22h core + on-demand | 100% |

---

## 🔴 TIER 1: MUST LEARN (Critical for Job/Interview)

### **1. Locators & Element Selection**
**Status:** ✅ MUST LEARN  
**Time Required:** 3 hours  
**Depth:** DEEP (Master Level)  
**Job Requirement Frequency:** 100%

**What to Learn:**
- ✅ `page.get_by_role()` — Accessibility-first (button, textbox, heading, link, etc.)
- ✅ `page.get_by_text()` — Find by visible text (exact & partial match)
- ✅ `page.get_by_test_id()` — Data-testid attribute (you already use this!)
- ✅ `page.get_by_label()` — Form labels (for input fields)
- ✅ `page.get_by_placeholder()` — Input placeholders
- ✅ `page.locator("css-selector")` — CSS selectors (classes, IDs, attributes)
- ✅ `page.locator("xpath=//div")` — XPath basics (know when to use)
- ✅ Chaining locators — `.filter()`, `.first()`, `.last()`, `.nth()`
- ✅ Locator best practices — When to use which strategy

**Why Critical:**
- Can't interact with elements without locators
- Asked in 90% of interviews
- Foundation for everything else

**Learning Depth:**
- Write 50+ locator examples
- Locate same element 5 different ways
- Understand pros/cons of each strategy
- Master chaining and filtering

**Interview Questions You'll Face:**
- "What's the difference between `get_by_role()` and `locator()`?"
- "When would you use XPath vs CSS?"
- "How do you handle dynamic IDs?"

---

### **2. Basic Interactions**
**Status:** ✅ MUST LEARN  
**Time Required:** 1.5 hours  
**Depth:** MEDIUM (Functional Level)  
**Job Requirement Frequency:** 100%

**What to Learn:**
- ✅ `click()` — Basic click
- ✅ `dblclick()` — Double click (know it exists)
- ✅ `click(button="right")` — Right click (rare, but know it)
- ✅ `fill()` — Fill input fields (clears first, then types)
- ✅ `type()` — Type character by character (for special scenarios)
- ✅ `clear()` — Clear input fields
- ✅ `press()` — Keyboard keys (Enter, Escape, Tab, etc.)
- ✅ `press("Control+A")` — Keyboard shortcuts
- ✅ `hover()` — Mouse hover over element
- ✅ `focus()` / `blur()` — Focus management

**What to Skip:**
- ❌ `click(force=True)` — Learn only if you face issues
- ❌ Complex mouse movements — Rare use cases

**Why Critical:**
- Core of all test automation
- Used in every single test

**Learning Depth:**
- Practice with 15+ element types
- Understand when to use `fill()` vs `type()`
- Know keyboard shortcuts

**Interview Questions:**
- "What's the difference between `fill()` and `type()`?"
- "How do you handle elements that require hover first?"

---

### **3. Waits & Synchronization**
**Status:** ✅ MUST LEARN  
**Time Required:** 3 hours  
**Depth:** DEEP (Master Level)  
**Job Requirement Frequency:** 100%

**What to Learn:**
- ✅ **Auto-waiting** — How Playwright waits automatically (actionability checks)
- ✅ `wait_for_selector(selector, state="visible")` — Wait for element to appear
- ✅ `wait_for_load_state("load")` — Wait for page load
- ✅ `wait_for_load_state("domcontentloaded")` — DOM ready
- ✅ `wait_for_load_state("networkidle")` — All network requests done
- ✅ `wait_for_url(url_or_regex)` — Wait for URL change
- ✅ `wait_for_timeout(milliseconds)` — Hard wait (use sparingly!)
- ✅ Timeout management — Default, per-action, global timeouts
- ✅ `locator.wait_for(state="visible")` — Wait for element state

**What to Skip (Learn Later):**
- ❌ `wait_for_function()` — Advanced custom waits

**Why Critical:**
- #1 reason tests become flaky
- Most asked interview question: "How do you handle synchronization?"
- Separates junior from senior testers

**Learning Depth:**
- Understand Playwright's auto-waiting mechanism
- Know when to use explicit waits
- Never write `time.sleep()` — use proper waits
- Master timeout strategies

**Interview Questions:**
- "How does Playwright handle waits differently from Selenium?"
- "When would you use `wait_for_load_state("networkidle")`?"
- "How do you handle flaky tests?"

---

### **4. Assertions & Verifications**
**Status:** ✅ MUST LEARN  
**Time Required:** 2 hours  
**Depth:** MEDIUM (Functional Level)  
**Job Requirement Frequency:** 100%

**What to Learn:**
- ✅ `expect(locator).to_be_visible()` — Element is visible
- ✅ `expect(locator).to_be_hidden()` — Element is not visible
- ✅ `expect(locator).to_have_text("text")` — Exact text match
- ✅ `expect(locator).to_contain_text("partial")` — Partial text match
- ✅ `expect(locator).to_have_value("value")` — Input field value
- ✅ `expect(locator).to_have_attribute("attr", "value")` — Attribute check
- ✅ `expect(locator).to_be_enabled()` — Element is enabled
- ✅ `expect(locator).to_be_disabled()` — Element is disabled
- ✅ `expect(locator).to_be_checked()` — Checkbox/radio is checked
- ✅ `expect(locator).to_have_count(n)` — Number of matching elements
- ✅ `expect(page).to_have_url("url")` — Current URL check
- ✅ `expect(page).to_have_title("title")` — Page title check

**What to Skip:**
- ❌ Soft assertions — Learn when needed
- ❌ Custom matchers — Advanced topic

**Why Critical:**
- Can't verify test results without assertions
- Every test needs validation
- Interview coding rounds always test this

**Learning Depth:**
- Practice 20+ assertion types
- Understand async nature of Playwright assertions
- Know which assertion to use when

**Interview Questions:**
- "How do you verify an element is visible?"
- "What's the difference between `to_have_text()` and `to_contain_text()`?"

---

### **5. Forms & Input Elements**
**Status:** ✅ MUST LEARN  
**Time Required:** 2.5 hours  
**Depth:** MEDIUM (Functional Level)  
**Job Requirement Frequency:** 95%

**What to Learn:**
- ✅ **Text inputs** — text, email, password, textarea
- ✅ **Dropdowns (native `<select>`):**
  - `select_option("value")` — By value
  - `select_option(label="Label")` — By visible text
  - `select_option(index=2)` — By index
- ✅ **Checkboxes:**
  - `check()` — Check checkbox
  - `uncheck()` — Uncheck checkbox
  - `is_checked()` — Verify state
- ✅ **Radio buttons:**
  - `check()` — Select radio button
- ✅ **File uploads:**
  - `set_input_files("path/to/file")` — Single file
  - `set_input_files(["file1", "file2"])` — Multiple files

**What to Skip (Learn Later):**
- ❌ Date pickers — Highly custom, learn when encountered
- ❌ Range sliders — Rare use case
- ❌ Color pickers — Very rare

**Why Critical:**
- Every application has forms
- Common in coding assessments
- Real-world necessity

**Learning Depth:**
- Automate a complete multi-field form
- Handle all common input types
- Understand form validation scenarios

**Interview Questions:**
- "How do you select an option from a dropdown?"
- "What's the difference between `check()` and `click()` for checkboxes?"

---

### **6. Browser Contexts & Pages**
**Status:** ✅ MUST LEARN  
**Time Required:** 1.5 hours  
**Depth:** MEDIUM (Functional Level)  
**Job Requirement Frequency:** 85%

**What to Learn:**
- ✅ `browser.new_context()` — Create isolated session
- ✅ `context.new_page()` — Open new tab/page
- ✅ Browser lifecycle — launch → context → page → close
- ✅ Context isolation — Why use contexts for test independence
- ✅ `page.goto(url)` — Navigate to URL
- ✅ Multiple pages — Handle multiple tabs

**What to Skip:**
- ❌ Advanced context options (viewport, user agent) — Learn later

**Why Critical:**
- Foundation of test isolation
- You already use this in your framework!
- Understanding architecture matters in interviews

**Learning Depth:**
- Understand browser → context → page hierarchy
- Create isolated test sessions
- Handle multiple tabs scenario

**Interview Questions:**
- "What's the difference between browser, context, and page?"
- "Why use contexts instead of multiple browsers?"

---

### **7. iframes & Frames**
**Status:** ✅ MUST LEARN  
**Time Required:** 1.5 hours  
**Depth:** MEDIUM (Functional Level)  
**Job Requirement Frequency:** 75%

**What to Learn:**
- ✅ `page.frame_locator("iframe-selector")` — Modern way to handle iframes
- ✅ `frame_locator().locator("element")` — Find element inside iframe
- ✅ `page.frame(name="frame-name")` — Old way (know it exists)
- ✅ Nested iframes — Handle iframe within iframe

**What to Skip:**
- ❌ Complex frame manipulation — Learn when needed

**Why Critical:**
- Very common in enterprise applications
- Payment gateways, embedded widgets use iframes
- Often asked in interviews

**Learning Depth:**
- Switch to iframe and interact with elements
- Handle nested iframes (2 levels)
- Understand modern vs old API

**Interview Questions:**
- "How do you handle elements inside an iframe?"
- "What if the iframe is nested?"

---

### **8. Page Object Model (POM)**
**Status:** ✅ MUST LEARN  
**Time Required:** 1 hour (Concept)  
**Depth:** MEDIUM (Conceptual + Practical)  
**Job Requirement Frequency:** 90%

**What to Learn:**
- ✅ POM design pattern — Separate page logic from tests
- ✅ Locator separation — Store locators separately
- ✅ Reusable methods — One method per page action
- ✅ BasePage pattern — Common methods in base class
- ✅ Why POM? — Maintainability, readability, reusability

**Why Critical:**
- Framework architecture requirement
- You already implement this!
- Must explain in interviews

**Learning Depth:**
- Understand WHY, not just HOW
- Explain benefits vs drawbacks
- Design scalable page classes

**Interview Questions:**
- "Why do you use Page Object Model?"
- "How do you organize your framework?"
- "What goes in BasePage vs specific page classes?"

---

### **9. Fixtures & Setup/Teardown**
**Status:** ✅ MUST LEARN  
**Time Required:** 1 hour  
**Depth:** MEDIUM (Functional Level)  
**Job Requirement Frequency:** 90%

**What to Learn:**
- ✅ Pytest fixtures — `@pytest.fixture`
- ✅ Fixture scopes — function, class, module, session
- ✅ `conftest.py` — Shared fixtures
- ✅ Setup/teardown — Before/after test execution
- ✅ Fixture dependencies — Fixtures using other fixtures

**Why Critical:**
- Test setup is essential
- You already use this!
- Framework foundation

**Learning Depth:**
- Create reusable fixtures
- Understand scope implications
- Design clean test setup

**Interview Questions:**
- "How do you handle test setup and teardown?"
- "What's the difference between function and session scope?"

---

### **10. Screenshots & Videos**
**Status:** ✅ MUST LEARN  
**Time Required:** 1 hour  
**Depth:** BASIC (Awareness + Usage)  
**Job Requirement Frequency:** 80%

**What to Learn:**
- ✅ `page.screenshot(path="screenshot.png")` — Full page screenshot
- ✅ `locator.screenshot()` — Element screenshot
- ✅ `context = browser.new_context(record_video_dir="videos/")` — Video recording
- ✅ Screenshot on failure — Debugging failed tests

**What to Skip:**
- ❌ Screenshot comparison (visual testing) — Advanced

**Why Critical:**
- CI/CD debugging requirement
- Evidence for failed tests
- You already do video recording!

**Learning Depth:**
- Take screenshots programmatically
- Record videos for tests
- Know when to use each

---

### **11. Storage State & Authentication**
**Status:** ✅ MUST LEARN  
**Time Required:** 1 hour  
**Depth:** BASIC (Awareness + Usage)  
**Job Requirement Frequency:** 75%

**What to Learn:**
- ✅ `context.storage_state(path="auth.json")` — Save auth state
- ✅ `browser.new_context(storage_state="auth.json")` — Reuse login
- ✅ Cookies basics — Understand storage state contains cookies
- ✅ Why storage state? — Avoid repeated login in every test

**What to Skip:**
- ❌ Manual cookie manipulation — Rarely needed

**Why Critical:**
- Performance optimization (skip repeated logins)
- You already use this!
- Common interview topic

**Learning Depth:**
- Save and reuse authentication
- Understand what's stored
- Explain benefits

**Interview Questions:**
- "How do you handle login in multiple tests?"
- "What is storage state?"

---

### **12. Cross-Browser Testing**
**Status:** ✅ MUST LEARN  
**Time Required:** 30 minutes  
**Depth:** BASIC (Awareness)  
**Job Requirement Frequency:** 85%

**What to Learn:**
- ✅ `playwright.chromium.launch()` — Chromium-based browsers
- ✅ `playwright.firefox.launch()` — Firefox
- ✅ `playwright.webkit.launch()` — Safari/WebKit
- ✅ Headless vs headful — When to use each
- ✅ Why cross-browser? — Ensure compatibility

**Why Critical:**
- Job requirement
- Real-world necessity
- Easy to demonstrate knowledge

**Learning Depth:**
- Run tests on all 3 browsers
- Understand differences
- Know when each matters

---

## 🟡 TIER 2: SHOULD LEARN (Competitive Advantage)

### **13. Network Interception & API Mocking**
**Status:** 🟡 SHOULD LEARN  
**Time Required:** 2 hours  
**Depth:** MEDIUM (Functional Level)  
**Job Requirement Frequency:** 60%

**What to Learn:**
- ✅ `page.route(url, handler)` — Intercept and mock requests
- ✅ `page.wait_for_response(url)` — Wait for specific API call
- ✅ `page.wait_for_request(url)` — Wait for request to be sent
- ✅ Mock API responses — Return custom JSON
- ✅ Block resources — Block images, CSS for faster tests

**Why Important:**
- Differentiates you from basic testers
- Modern testing requirement
- Interview favorite for senior roles

**Learning Depth:**
- Mock at least 3 different API responses
- Wait for API calls in tests
- Understand request/response lifecycle

**Interview Questions:**
- "How do you test when backend is not ready?"
- "How do you wait for an API call to complete?"

---

### **14. Custom Dropdowns (Non-Select)**
**Status:** 🟡 SHOULD LEARN  
**Time Required:** 1 hour  
**Depth:** BASIC (Problem-Solving)  
**Job Requirement Frequency:** 60%

**What to Learn:**
- ✅ JS-driven dropdowns (Material UI, Ant Design, etc.)
- ✅ Click to open → Select option → Verify selection
- ✅ Waiting for dropdown to appear
- ✅ Filtering/searching in dropdowns

**Why Important:**
- Modern UIs don't use `<select>`
- Real-world necessity
- Common pain point

**Learning Depth:**
- Handle 3-4 different custom dropdown patterns
- Develop strategy for unknown dropdowns

---

### **15. File Uploads (Advanced)**
**Status:** 🟡 SHOULD LEARN  
**Time Required:** 1 hour  
**Depth:** BASIC (Functional Level)  
**Job Requirement Frequency:** 50%

**What to Learn:**
- ✅ `set_input_files()` — Already covered in TIER 1
- ✅ Drag-and-drop file upload
- ✅ Multiple file selection
- ✅ Upload validation

**Why Important:**
- Common feature (document uploads, profile pictures)
- You already do this in your tests!

---

### **16. Dynamic Behaviors & Interactions**
**Status:** 🟡 SHOULD LEARN  
**Time Required:** 1.5 hours  
**Depth:** BASIC (Problem-Solving)  
**Job Requirement Frequency:** 50%

**What to Learn:**
- ✅ Hover-triggered menus — `hover()` then `click()`
- ✅ Auto-suggestions/typeahead — Type → Wait → Select
- ✅ Tooltips — Hover and verify text
- ✅ Toast/notification messages — Wait and verify

**What to Skip:**
- ❌ Infinite scroll — Niche
- ❌ Lazy loading — Learn when needed

**Why Important:**
- Modern UIs are interactive
- Tests real-world scenarios

---

### **17. Multiple Windows & Tabs**
**Status:** 🟡 SHOULD LEARN  
**Time Required:** 1 hour  
**Depth:** BASIC (Functional Level)  
**Job Requirement Frequency:** 60%

**What to Learn:**
- ✅ Handle "opens in new tab" links
- ✅ `context.pages` — Get all open pages
- ✅ `page.wait_for_event("popup")` — Wait for new window
- ✅ Switch between tabs
- ✅ Close tabs

**Why Important:**
- Common scenario (PDFs, external links)
- Interview question

**Learning Depth:**
- Handle 2-3 tab scenarios

---

### **18. CI/CD Integration Basics**
**Status:** 🟡 SHOULD LEARN  
**Time Required:** 30 minutes  
**Depth:** BASIC (Awareness)  
**Job Requirement Frequency:** 70%

**What to Learn:**
- ✅ Running tests headless in CI
- ✅ Playwright Docker image
- ✅ GitHub Actions / Jenkins basics
- ✅ Parallel execution

**Why Important:**
- Job requirement
- Modern testing practice

**Learning Depth:**
- Understand concepts
- Run tests in CI once

---

## 🟢 TIER 3: SKIP FOR NOW (Learn On-Demand)

These are specialized topics with <20% usage. Learn only when your job requires them.

### **19. Shadow DOM & Web Components**
**Status:** ⚪ SKIP  
**When to Learn:** Only if your app uses Web Components  
**Frequency:** <10%

---

### **20. Device Emulation & Mobile Testing**
**Status:** ⚪ SKIP  
**When to Learn:** Mobile-focused roles only  
**Frequency:** 15%

**Quick Reference:**
- `browser.new_context(viewport={"width": 375, "height": 667})`
- `browser.new_context(**playwright.devices["iPhone 12"])`

---

### **21. Geolocation & Permissions**
**Status:** ⚪ SKIP  
**When to Learn:** Location-based apps  
**Frequency:** <5%

---

### **22. Date Pickers (Custom)**
**Status:** ⚪ SKIP  
**When to Learn:** When you encounter one  
**Frequency:** 30% (but highly varied implementations)

**Note:** Every date picker is different. Learn the pattern when needed.

---

### **23. Drag & Drop**
**Status:** ⚪ SKIP  
**When to Learn:** Kanban boards, file managers  
**Frequency:** <10%

**Quick Reference:**
- `locator.drag_to(target_locator)`

---

### **24. JavaScript Execution (evaluate)**
**Status:** ⚪ SKIP  
**When to Learn:** Last resort for complex scenarios  
**Frequency:** 5%

**Quick Reference:**
- `page.evaluate("() => document.title")`
- Use only when Playwright API doesn't work

---

### **25. Service Workers & WebSockets**
**Status:** ⚪ SKIP  
**When to Learn:** Real-time apps, PWAs  
**Frequency:** <5%

---

### **26. Downloads Handling**
**Status:** ⚪ SKIP  
**When to Learn:** When you need to verify downloaded files  
**Frequency:** 20%

**Quick Reference:**
- `page.expect_download()` — Wait for download

---

### **27. Performance Monitoring**
**Status:** ⚪ SKIP  
**When to Learn:** Performance testing role  
**Frequency:** <10%

---

### **28. Accessibility Testing (A11y)**
**Status:** ⚪ SKIP  
**When to Learn:** Accessibility-focused role  
**Frequency:** 10%

**Note:** `get_by_role()` already promotes accessibility.

---

### **29. Visual Regression Testing**
**Status:** ⚪ SKIP  
**When to Learn:** UI/UX validation requirements  
**Frequency:** 15%

**Note:** Screenshot comparison, pixel-by-pixel diff

---

### **30. HTTP Authentication (Basic Auth)**
**Status:** ⚪ SKIP  
**When to Learn:** When your app uses HTTP auth  
**Frequency:** <5%

**Quick Reference:**
- `browser.new_context(http_credentials={"username": "user", "password": "pass"})`

---

### **31. Clipboard Operations**
**Status:** ⚪ SKIP  
**When to Learn:** Copy/paste testing scenarios  
**Frequency:** <5%

---

### **32. Tracing & Debugging Tools**
**Status:** ⚪ SKIP (For Now)  
**When to Learn:** After mastering basics  
**Frequency:** 30% (useful for debugging)

**Quick Reference:**
- `context.tracing.start(screenshots=True, snapshots=True)`
- View in Playwright Trace Viewer

**Note:** Useful, but not critical for learning phase

---

### **33. Test Retries & Flaky Test Management**
**Status:** ⚪ SKIP  
**When to Learn:** Framework optimization phase  
**Frequency:** 40% (good practice)

**Note:** Focus on writing stable tests first, then add retries

---

## 📋 LEARNING PATHS

### **PATH 1: Minimum Viable (Interview Ready)**
**Time:** 16 hours  
**Coverage:** 80% of scenarios  
**Topics:** TIER 1 only (1-12)

**Best for:**
- Quick interview prep
- Time-constrained learning
- Entry-level QA roles

---

### **PATH 2: Competitive Advantage**
**Time:** 22 hours  
**Coverage:** 95% of scenarios  
**Topics:** TIER 1 (1-12) + TIER 2 (13-18)

**Best for:**
- SDET roles
- Senior positions
- Comprehensive knowledge

---

### **PATH 3: Complete Mastery**
**Time:** 30+ hours  
**Coverage:** 100%  
**Topics:** All 33 topics

**Best for:**
- Framework architects
- Long-term career investment
- Specialized roles

---

## 🎯 RECOMMENDED APPROACH

Based on your situation (job hunting + 30 hours available):

### **PHASE 1: TIER 1 (Week 1-2, 16 hours)**
Learn topics 1-12. This makes you interview-ready and covers 80% of real-world needs.

### **PHASE 2: TIER 2 (Week 3, 6 hours)**
Add topics 13-18 for competitive advantage. Now you're at 95% coverage.

### **PHASE 3: Framework Application (After job)**
Apply all learnings to your framework and learn TIER 3 on-demand.

---

## 📝 NOTES

- **Time estimates** include theory + hands-on practice
- **Depth levels:**
  - **DEEP:** Master every aspect, practice extensively
  - **MEDIUM:** Functional understanding, practical usage
  - **BASIC:** Awareness, know when/how to use
- **Frequencies** based on job posting analysis + common scenarios
- **Interview readiness:** TIER 1 covers 90% of interview questions

---

## ✅ NEXT STEPS

1. Review this document
2. Decide on learning path (PATH 1, 2, or 3)
3. Start with **Topic 1: Locators** (most critical)
4. Progress sequentially through TIER 1
5. Add TIER 2 if time permits

**Ready to start learning? Tell me which PATH you choose, and we'll begin immediately!**

---

_Document created based on real job market analysis for QA Automation/SDET roles requiring Playwright expertise._


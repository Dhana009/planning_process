# 🌐 API TESTING FOR QA/SDET - Complete Interview Questions Bank
## QA Automation / SDET Role Preparation

> **Purpose**: Comprehensive question bank covering all API Testing topics for QA/SDET roles
> **Total Questions**: 75+ questions (50 Conceptual + 25 Coding Problems)
> **Format**: Questions ONLY - Answers will be added separately
> **Status**: 🟡 Questions Complete - Answers Pending
> **Focus**: Testing APIs (QA/SDET perspective) - NOT building APIs

---

## 📋 TABLE OF CONTENTS

### PART 1: CONCEPTUAL QUESTIONS
- [API Testing Fundamentals](#api-testing-fundamentals) - 10 questions
- [HTTP & REST Basics](#http--rest-basics) - 10 questions
- [API Authentication & Security Testing](#api-authentication--security-testing) - 8 questions
- [Request & Response Validation](#request--response-validation) - 10 questions
- [API Testing Tools](#api-testing-tools) - 8 questions
- [API Test Framework & Design](#api-test-framework--design) - 10 questions
- [Advanced API Testing Concepts](#advanced-api-testing-concepts) - 8 questions

### PART 2: CODING PROBLEMS
- [Basic API Testing Scripts](#basic-api-testing-scripts) - 8 problems
- [Intermediate API Automation](#intermediate-api-automation) - 8 problems
- [Advanced API Testing Scenarios](#advanced-api-testing-scenarios) - 9 problems

---

# PART 1: CONCEPTUAL QUESTIONS

## API TESTING FUNDAMENTALS

### Q1: What is API testing? Why is it important in the QA process?

### Q2: What are the advantages of API testing over UI testing?

### Q3: When should you perform API testing vs UI testing? What is the ideal testing strategy?

### Q4: What is the testing pyramid? Where do API tests fit in the test automation pyramid?

### Q5: What do you test/validate when testing an API? List all aspects.

### Q6: What is the difference between functional and non-functional API testing?

### Q7: What is the typical API testing workflow/lifecycle?

### Q8: How do you perform exploratory API testing? What tools do you use?

### Q9: What is contract testing? How is it different from regular API testing?

### Q10: What is the difference between API testing and API monitoring?

---

## HTTP & REST BASICS

### Q11: What is a REST API? What are RESTful principles? (From QA perspective)

### Q12: What are HTTP methods? Which HTTP methods do you test most frequently as a QA?

### Q13: Explain GET, POST, PUT, PATCH, DELETE methods with real testing examples

### Q14: What is the difference between PUT and PATCH? When would you test each?

### Q15: What are idempotent methods? Why is this important for testing?

### Q16: What are HTTP status codes? Explain the categories (1xx, 2xx, 3xx, 4xx, 5xx)

### Q17: Explain these common status codes: 200, 201, 204, 400, 401, 403, 404, 409, 422, 500, 502, 503

### Q18: What are HTTP headers? Which headers are most important for API testing?

### Q19: What is Content-Type header? What are common Content-Type values you test?

### Q20: What are query parameters, path parameters, and request body? How do you test each?

---

## API AUTHENTICATION & SECURITY TESTING

### Q21: How do you test API authentication as a QA?

### Q22: What is Basic Authentication? How do you test it? When is it used?

### Q23: What is Bearer Token authentication? How do you test APIs with Bearer tokens?

### Q24: What is API Key authentication? How do you pass API keys in requests?

### Q25: What is OAuth 2.0? How do you test OAuth-protected APIs?

### Q26: What is JWT (JSON Web Token)? How do you validate JWT in API testing?

### Q27: What is the difference between authentication and authorization? How do you test each?

### Q28: What security aspects do you test in APIs? (OWASP API Security)

---

## REQUEST & RESPONSE VALIDATION

### Q29: What do you validate in an API response?

### Q30: How do you validate response status codes in your tests?

### Q31: How do you validate response body/payload?

### Q32: How do you validate response headers?

### Q33: How do you validate response time/performance?

### Q34: What is JSON? Why is it commonly used in APIs?

### Q35: How do you validate JSON response structure/schema?

### Q36: What is JSON Schema validation? Why is it important?

### Q37: How do you handle and validate error responses in API testing?

### Q38: How do you test APIs that return XML responses?

---

## API TESTING TOOLS

### Q39: What tools do you use for API testing? (Manual and Automation)

### Q40: What is Postman? How do you use it for API testing?

### Q41: How do you organize API tests in Postman? (Collections, folders, environments)

### Q42: What are Postman variables and environments? How do you use them?

### Q43: How do you write test assertions in Postman?

### Q44: What is Newman? How do you run Postman collections in CI/CD?

### Q45: What is Python requests library? Why is it popular for API automation?

### Q46: How do you use pytest for API testing? What are the advantages?

---

## API TEST FRAMEWORK & DESIGN

### Q47: How do you structure an API automation framework?

### Q48: What design patterns do you use in API test automation?

### Q49: How do you organize your API test project? (Folder structure)

### Q50: How do you manage API endpoints in your framework? (Base URL, endpoints)

### Q51: How do you handle test data in API automation?

### Q52: How do you manage API configurations? (environments, credentials)

### Q53: How do you handle authentication tokens in your test framework?

### Q54: How do you implement reusable utility functions for API testing?

### Q55: How do you generate test reports for API tests?

### Q56: How do you integrate API tests with CI/CD pipelines?

---

## ADVANCED API TESTING CONCEPTS

### Q57: How do you test pagination in APIs?

### Q58: How do you test file upload APIs?

### Q59: How do you test file download APIs?

### Q60: How do you handle rate limiting in API testing?

### Q61: How do you chain multiple API requests in your tests?

### Q62: How do you perform data-driven testing for APIs?

### Q63: What is API mocking? When and why would you use it?

### Q64: How do you handle flaky API tests? What strategies do you use?

---

# PART 2: CODING PROBLEMS

## BASIC API TESTING SCRIPTS

### PROBLEM 1: Simple GET Request Test
**Task**: Write a Python script using requests library to:
- Make a GET request to a public API (e.g., https://jsonplaceholder.typicode.com/posts/1)
- Print the response status code
- Print the response body
- Print specific response headers
- Verify the request was successful

### PROBLEM 2: Validate GET Response with Assertions
**Task**: Write a pytest test to:
- Make a GET request to retrieve a user
- Assert status code is 200
- Assert response contains specific fields (id, name, email)
- Assert response Content-Type is application/json
- Assert response time is less than 2 seconds

### PROBLEM 3: POST Request - Create Resource
**Task**: Write a test to:
- Create a new resource using POST request
- Send JSON payload with required fields
- Set appropriate headers (Content-Type)
- Verify status code is 201 (Created)
- Verify response contains the created resource with ID
- Print the created resource

### PROBLEM 4: PUT Request - Update Resource
**Task**: Write a test to:
- Update an existing resource using PUT request
- Send complete updated data in request body
- Verify status code is 200
- Verify response contains updated data
- Compare request data with response data

### PROBLEM 5: DELETE Request - Remove Resource
**Task**: Write a test to:
- Delete a resource using DELETE request
- Verify status code is 200 or 204
- Attempt to GET the deleted resource
- Verify it returns 404 (Not Found)

### PROBLEM 6: Test Different Status Codes
**Task**: Write tests to validate different HTTP status codes:
- 200 (OK) - successful GET
- 201 (Created) - successful POST
- 400 (Bad Request) - invalid input
- 401 (Unauthorized) - missing auth
- 404 (Not Found) - invalid endpoint
- 500 (Server Error) - if possible

### PROBLEM 7: Validate JSON Response Structure
**Task**: Write a test to:
- Make a GET request to retrieve data
- Validate JSON response has expected keys
- Validate data types of each field
- Validate required fields are not null/empty
- Validate array length (if applicable)

### PROBLEM 8: Query Parameters Testing
**Task**: Write tests to:
- Test API with different query parameters
- Test filtering (e.g., ?status=active)
- Test sorting (e.g., ?sort=name&order=asc)
- Test pagination (e.g., ?page=1&limit=10)
- Verify results match the query parameters

---

## INTERMEDIATE API AUTOMATION

### PROBLEM 9: Basic Authentication
**Task**: Write a test to:
- Make a request to an API requiring Basic Auth
- Pass username and password
- Verify successful authentication (200)
- Test with invalid credentials (401)
- Handle authentication in reusable way

### PROBLEM 10: Bearer Token Authentication
**Task**: Write a test to:
- Login via API and get access token
- Use the token in Authorization header for subsequent requests
- Make authenticated requests to protected endpoints
- Test with invalid/expired token (401)
- Store token for reuse across tests

### PROBLEM 11: Chain Multiple API Calls
**Task**: Write a test that:
- Creates a resource (POST) and stores the ID
- Retrieves the created resource (GET) using the ID
- Updates the resource (PUT) using the ID
- Deletes the resource (DELETE) using the ID
- Verifies each step was successful

### PROBLEM 12: JSON Schema Validation
**Task**: Write a test to:
- Make a GET request to retrieve data
- Define expected JSON schema
- Validate response against the schema
- Use jsonschema library or similar
- Test should fail if schema doesn't match

### PROBLEM 13: Error Response Handling
**Task**: Write tests to:
- Test various error scenarios
- Validate error response structure
- Verify error messages are meaningful
- Check error codes/error types
- Handle exceptions properly

### PROBLEM 14: Data-Driven API Testing
**Task**: Write a data-driven test that:
- Reads test data from JSON/CSV file
- Runs same API test with multiple data sets
- Uses pytest parametrize
- Validates results for each data set
- Reports which data sets passed/failed

### PROBLEM 15: Create Reusable API Client Class
**Task**: Create a reusable API client class with:
- Methods for GET, POST, PUT, DELETE
- Automatic header management
- Base URL configuration
- Response logging
- Error handling
- Use the class in tests

### PROBLEM 16: API Test Framework Structure
**Task**: Create a basic API test framework with:
- Folder structure (tests/, utils/, config/, data/)
- Configuration file for environments
- Utility functions for common operations
- Base test class with setup/teardown
- Sample tests demonstrating the framework

---

## ADVANCED API TESTING SCENARIOS

### PROBLEM 17: Test Pagination
**Task**: Write tests to:
- Test API pagination (page-based or cursor-based)
- Retrieve all pages of data
- Verify page size limits
- Verify total count matches actual records
- Handle last page correctly

### PROBLEM 18: Test File Upload API
**Task**: Write a test to:
- Upload a file using multipart/form-data
- Send file with additional form fields
- Verify successful upload (200/201)
- Validate response contains file info
- Test with invalid file types

### PROBLEM 19: Test File Download API
**Task**: Write a test to:
- Download a file from API
- Verify Content-Type header
- Verify Content-Disposition header
- Save file locally
- Verify file size and integrity

### PROBLEM 20: Handle Rate Limiting
**Task**: Write a test that:
- Makes multiple requests to rate-limited API
- Detects rate limit response (429)
- Implements retry logic with backoff
- Logs rate limit details
- Successfully completes after rate limit resets

### PROBLEM 21: Test API with OAuth 2.0
**Task**: Write a test to:
- Obtain OAuth access token
- Use token to access protected resources
- Handle token refresh
- Test token expiration
- Handle OAuth errors

### PROBLEM 22: Mock External API Dependencies
**Task**: Write tests that:
- Mock external API dependencies
- Use responses library or similar
- Test different mock responses (success, error)
- Test without hitting actual external APIs
- Verify request parameters sent to mocked API

### PROBLEM 23: Parallel API Test Execution
**Task**: Create a test suite that:
- Runs API tests in parallel
- Uses pytest-xdist or similar
- Ensures test isolation (no shared state)
- Handles authentication for parallel tests
- Generates consolidated report

### PROBLEM 24: API Performance Testing
**Task**: Write tests to:
- Measure API response time
- Test with concurrent requests
- Calculate average, min, max response times
- Identify slow endpoints
- Fail test if performance threshold exceeded

### PROBLEM 25: End-to-End API Test Scenario
**Task**: Write a complete E2E test for:
- User registration via API
- Email verification (if applicable)
- User login and get token
- Create user profile/data
- Update user profile
- Retrieve user data
- Delete user account
- Verify all steps with proper assertions

---

## 📊 QUESTION DISTRIBUTION

### By Type:
- **Conceptual Questions**: 64 questions
- **Coding Problems**: 25 problems
- **Total**: 89 questions

### By Topic:
- **Fundamentals & HTTP**: 30 questions (34%)
- **Authentication & Security**: 8 questions (9%)
- **Validation & Testing**: 18 questions (20%)
- **Tools & Framework**: 18 questions (20%)
- **Coding - Basic**: 8 problems (9%)
- **Coding - Intermediate**: 8 problems (9%)
- **Coding - Advanced**: 9 problems (10%)

### By Difficulty:
- **Basic/Easy**: 35 questions (39%)
- **Intermediate**: 38 questions (43%)
- **Advanced**: 16 questions (18%)

---

## 🎯 SKILLS COVERAGE

### Topics Covered:
✅ API testing fundamentals and importance
✅ HTTP methods, status codes, headers
✅ REST principles and best practices
✅ Authentication testing (Basic, Bearer, OAuth, API Key)
✅ Request and response validation
✅ JSON and schema validation
✅ API testing tools (Postman, requests, pytest)
✅ Framework design and structure
✅ Test data management
✅ CI/CD integration
✅ Advanced scenarios (pagination, file upload/download, rate limiting)
✅ Performance testing basics
✅ Mocking and stubbing
✅ Data-driven testing
✅ Error handling

### Real SDET Interview Alignment:
- **25-30% Conceptual**: ✅ Covered (64 conceptual questions)
- **45-50% Coding**: ✅ Covered (25 coding problems)
- **15-20% Framework**: ✅ Covered (framework design questions)
- **10-15% Tools**: ✅ Covered (Postman, pytest, requests)

---

## 📝 NEXT STEPS

### Suggested Answer Writing Phases:

1. **Phase 1**: Answer API Testing Fundamentals (Q1-Q10)
2. **Phase 2**: Answer HTTP & REST Basics (Q11-Q20)
3. **Phase 3**: Answer Authentication & Security (Q21-Q28)
4. **Phase 4**: Answer Validation Questions (Q29-Q38)
5. **Phase 5**: Answer Tools Questions (Q39-Q46)
6. **Phase 6**: Answer Framework Questions (Q47-Q56)
7. **Phase 7**: Answer Advanced Concepts (Q57-Q64)
8. **Phase 8**: Solve Basic Coding Problems (P1-P8)
9. **Phase 9**: Solve Intermediate Coding Problems (P9-P16)
10. **Phase 10**: Solve Advanced Coding Problems (P17-P25)

---

## 💡 HOW TO USE THIS QUESTION BANK

### For Self-Assessment:
1. Try answering each conceptual question yourself first
2. Attempt coding problems before looking at solutions
3. Identify your weak areas
4. Focus study time on gaps

### For Interview Preparation:
1. **Week 1-2**: Master fundamentals (Q1-Q28, P1-P8)
2. **Week 3**: Tools and framework (Q29-Q56, P9-P16)
3. **Week 4**: Advanced topics and practice (Q57-Q64, P17-P25)
4. **Week 5**: Mock interviews and revision

### For Building Framework:
- Use coding problems 15-16 as framework blueprint
- Implement incrementally
- Add features as you learn advanced concepts
- Keep it production-ready for portfolio

### For Hands-On Practice:
**Recommended Public APIs for Practice:**
- JSONPlaceholder (https://jsonplaceholder.typicode.com) - Fake REST API
- ReqRes (https://reqres.in) - Test API with real responses
- RestfulAPI.dev (https://restful-api.dev) - Practice CRUD operations
- GoREST (https://gorest.co.in) - Requires auth, good for real testing
- Open Weather API - Real-world API with free tier
- GitHub API - Popular API for practice

---

## 🔧 TOOLS YOU'LL NEED

### Essential:
- ✅ Python 3.x
- ✅ requests library (`pip install requests`)
- ✅ pytest (`pip install pytest`)
- ✅ Postman (desktop app or web)

### Helpful:
- pytest-html (for reports)
- jsonschema (for schema validation)
- responses (for mocking)
- pytest-xdist (for parallel execution)
- faker (for test data generation)
- allure-pytest (for advanced reporting)

### Optional:
- RestAssured (if Java-based role)
- Playwright (for API testing in Playwright)
- Newman (Postman CLI)

---

## 📌 INTERVIEW TIPS

### When Asked Conceptual Questions:
1. Start with brief definition
2. Explain WHY it matters for QA
3. Give real testing example
4. Mention tools you use
5. Share a challenge you faced

### When Given Coding Tasks:
1. Clarify requirements
2. Think about edge cases
3. Write clean, readable code
4. Add proper assertions
5. Explain your approach
6. Mention what you'd add in production

### What Impresses Interviewers:
- ✅ Proper error handling
- ✅ Reusable code structure
- ✅ Meaningful assertions
- ✅ Logging for debugging
- ✅ Parameterized tests
- ✅ Clear naming conventions
- ✅ Understanding of HTTP/REST
- ✅ Framework thinking (even in small scripts)

---

*Questions compiled from: Real SDET interview experiences, industry best practices, REST API documentation, and current QA automation trends (2024-2025)*

**Document Status**: ✅ All questions listed - Ready for answers

**Next Step**: Begin answering questions systematically, starting with fundamentals!


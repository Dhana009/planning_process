# 📚 Theory Learning Plan (15 Hours)

**Goal**: Master essential API testing theory to understand and explain your framework

**Depth Guide**:
- 🔴 **DEEP** = Master this completely (60-80% of time)
- 🟡 **MEDIUM** = Understand well enough to explain (40-60% of time)
- 🟢 **SHALLOW** = Know the concept only (20-30% of time)
- ⚪ **SKIP** = Not needed, learn later

---

## Part 1: HTTP & Web Fundamentals (3 hours)

### Topic 1.1: HTTP Request-Response Cycle (45 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:
- Client sends request → Server processes → Server sends response
- Request components: Method, URL, Headers, Body
- Response components: Status code, Headers, Body

**What to Skip**:
- ❌ DNS resolution details
- ❌ TCP/IP layers
- ❌ Network packet inspection

---

### Topic 1.2: HTTP Methods (1 hour)
**Depth**: 🔴 **DEEP** ← Most important

**What to Learn**:
- **GET**: Retrieve data (no body, idempotent, cacheable)
- **POST**: Create resource (has body, not idempotent)
- **PUT**: Replace entire resource (has body, idempotent)
- **PATCH**: Update partial resource (has body, may not be idempotent)
- **DELETE**: Remove resource (idempotent)

**Key Concepts**:
- Idempotency: Same request = same result (multiple times)
- Safe methods: GET (doesn't change server state)

**What to Skip**:
- ❌ HEAD, OPTIONS, TRACE methods
- ❌ HTTP/2, HTTP/3 protocol details

**Interview Questions**:
- Q: Difference between PUT and PATCH?
- Q: Is POST idempotent? Why not?
- Q: When to use GET vs POST?

---

### Topic 1.3: HTTP Status Codes (45 mins)
**Depth**: 🔴 **DEEP** ← Asked in every interview

**What to Learn**:

**2xx Success**:
- 200 OK: Successful GET, PUT, PATCH
- 201 Created: Successful POST (resource created)
- 204 No Content: Successful DELETE (no response body)

**4xx Client Errors**:
- 400 Bad Request: Invalid input, validation error
- 401 Unauthorized: Missing or invalid authentication
- 403 Forbidden: Authenticated but not authorized
- 404 Not Found: Resource doesn't exist
- 422 Unprocessable Entity: Validation error (semantic)

**5xx Server Errors**:
- 500 Internal Server Error: Server crash/bug
- 502 Bad Gateway: Proxy/gateway error
- 503 Service Unavailable: Server overloaded/down

**What to Skip**:
- ❌ 1xx Informational codes
- ❌ Less common codes (405, 409, 429 - learn later if needed)

**Interview Questions**:
- Q: Difference between 401 and 403?
- Q: When do you return 201 vs 200?
- Q: What's 422 used for?

---

### Topic 1.4: HTTP Headers (30 mins)
**Depth**: 🔴 **DEEP**

**What to Learn**:

**Request Headers**:
- `Content-Type`: Format of request body (application/json, application/xml)
- `Accept`: Format client expects in response (application/json)
- `Authorization`: Authentication token (Bearer <token>, Basic <base64>)

**Response Headers**:
- `Content-Type`: Format of response body
- `Content-Length`: Size of response body

**What to Skip**:
- ❌ Cache-Control, ETag, If-Modified-Since
- ❌ CORS headers (Access-Control-*)
- ❌ Cookie headers

**Interview Questions**:
- Q: What's Content-Type header?
- Q: How do you send authentication?

---

## Part 2: REST APIs (3 hours)

### Topic 2.1: What is an API? (30 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:
- API = Application Programming Interface (how systems communicate)
- Web API = API accessed over HTTP
- Request → Processing → Response
- Used for: Frontend-Backend, System-System, Mobile-Backend

**What to Skip**:
- ❌ Library APIs, Operating System APIs
- ❌ History of APIs

**Interview Questions**:
- Q: What is an API?
- Q: Why use APIs instead of direct database access?

---

### Topic 2.2: REST Principles (1 hour)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:

**Core Principles**:
1. **Stateless**: Each request contains all info needed (no server-side session)
2. **Resource-based**: URLs represent resources (/users, /users/123)
3. **HTTP Methods**: Use standard methods (GET, POST, PUT, DELETE)
4. **Uniform Interface**: Consistent API design

**REST URL Design**:
- `/users` → Collection
- `/users/123` → Specific resource
- `/users/123/orders` → Nested resource

**What to Skip**:
- ❌ HATEOAS (hypermedia links)
- ❌ Richardson Maturity Model
- ❌ REST vs RESTful debate

**Interview Questions**:
- Q: What makes an API RESTful?
- Q: What's statelessness? Give example.
- Q: How do you design REST URLs?

---

### Topic 2.3: REST vs SOAP (30 mins)
**Depth**: 🟢 **SHALLOW**

**What to Learn**:
- **REST**: Uses HTTP, JSON, lightweight, stateless
- **SOAP**: Uses XML, heavy protocol, strict standards

**When asked, say**:
"REST is simpler, uses HTTP and JSON. SOAP is older, XML-based, more rigid. REST is more common for modern web APIs."

**What to Skip**:
- ❌ SOAP protocol details
- ❌ WSDL files
- ❌ GraphQL (unless asked)

---

### Topic 2.4: JSON Format (1 hour)
**Depth**: 🔴 **DEEP**

**What to Learn**:

**JSON Structure**:
```json
{
  "key": "value",
  "number": 123,
  "boolean": true,
  "array": [1, 2, 3],
  "object": {
    "nested": "value"
  },
  "null_value": null
}
```

**Data Types**:
- String: "text"
- Number: 123, 45.67
- Boolean: true, false
- Array: [1, 2, 3]
- Object: {"key": "value"}
- Null: null

**Parsing JSON**:
```python
import json
data = json.loads(response.text)
value = data['key']
```

**What to Skip**:
- ❌ XML format
- ❌ YAML (unless your framework uses it)

**Interview Questions**:
- Q: What data types does JSON support?
- Q: How do you parse JSON in Python?

---

## Part 3: Authentication (2 hours)

### Topic 3.1: Authentication Types (45 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:

**1. Basic Authentication**:
- Format: `Authorization: Basic <base64(username:password)>`
- Simple but not secure (send credentials every request)

**2. API Keys**:
- Format: `Authorization: ApiKey <key>` or custom header
- Static token, no expiry

**3. Bearer Token (JWT)**:
- Format: `Authorization: Bearer <token>`
- Token has expiry, stateless
- Your framework uses this ← Focus here

**What to Skip**:
- ❌ OAuth 2.0 flows (authorization code, implicit, etc.)
- ❌ OpenID Connect
- ❌ SAML

**Interview Questions**:
- Q: What authentication methods do you know?
- Q: Difference between Basic Auth and Token Auth?

---

### Topic 3.2: JWT Tokens (1 hour 15 mins)
**Depth**: 🔴 **DEEP** ← Your framework uses JWT

**What to Learn**:

**JWT Structure**:
```
header.payload.signature
```

**Header**: Algorithm and token type
```json
{"alg": "HS256", "typ": "JWT"}
```

**Payload**: User data and claims
```json
{
  "user_id": 123,
  "username": "john@example.com",
  "exp": 1735689600,  // Expiry timestamp
  "iat": 1735686000   // Issued at timestamp
}
```

**Signature**: Verifies token wasn't tampered

**How JWT Works**:
1. User logs in with username/password
2. Server generates JWT token
3. Client stores token (memory, not localStorage for security)
4. Client sends token in every request: `Authorization: Bearer <token>`
5. Server validates token signature and expiry

**Token Expiry**:
- `exp` claim = expiration timestamp (Unix time)
- Compare `current_time` >= `exp` → Expired
- Expired token → 401 Unauthorized

**Decoding JWT** (Python):
```python
import jwt
decoded = jwt.decode(token, options={"verify_signature": False})
exp = decoded['exp']
```

**What to Skip**:
- ❌ Refresh tokens (learn later)
- ❌ JWT signing algorithms deep dive
- ❌ JWT security vulnerabilities

**Interview Questions**:
- Q: What's the structure of a JWT token?
- Q: How do you check if token is expired?
- Q: Where do you send the JWT token?
- Q: What's the difference between 401 and 403?
  - **401**: No token or invalid token (authentication failed)
  - **403**: Valid token but no permission (authorization failed)

---

## Part 4: API Testing Fundamentals (5 hours)

### Topic 4.1: Testing Types Overview (30 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:
- **Functional Testing**: Does API return correct data?
- **Non-Functional Testing**: Performance, security, load
- **Positive Testing**: Valid inputs, happy path
- **Negative Testing**: Invalid inputs, error cases
- **Boundary Testing**: Edge cases (min, max, limits)
- **Integration Testing**: Multiple APIs working together

**What to Skip**:
- ❌ Performance/Load testing details
- ❌ Security testing deep dive

---

### Topic 4.2: Positive Testing (1 hour)
**Depth**: 🔴 **DEEP**

**What to Learn**:

**What is Positive Testing?**
- Test with valid inputs
- Verify expected behavior (happy path)
- All data is correct and complete

**What to Assert**:
1. Status code (200, 201, 204)
2. Response structure (JSON keys exist)
3. Data values (correct data returned)
4. Data types (string, int, boolean)
5. Response time (< acceptable threshold)

**Example: Login API Positive Tests**:
- ✅ Valid username and password → 200, token returned
- ✅ Token is valid JWT format
- ✅ Token contains user_id
- ✅ Token expiry is in future

**What to Skip**:
- ❌ Advanced assertions (complex schemas)

---

### Topic 4.3: Negative Testing (2 hours)
**Depth**: 🔴 **DEEP** ← Most asked in interviews

**What to Learn**:

**What is Negative Testing?**
- Test with invalid inputs
- Verify API handles errors gracefully
- Assert proper error codes and messages

**Categories of Negative Tests**:

**1. Missing Required Fields**:
- Missing username → 400 or 422
- Missing password → 400 or 422
- Missing all fields → 400 or 422

**2. Invalid Data Types**:
- Username is integer instead of string → 400
- Age is string instead of integer → 400
- Boolean field is string → 400

**3. Invalid Values**:
- Invalid email format (no @) → 400 or 422
- Negative age → 400
- Future birth date → 400
- Empty string when required → 400

**4. Invalid Credentials**:
- Wrong password → 401
- Non-existent username → 401
- Expired token → 401
- Invalid token → 401

**5. Authorization Errors**:
- Access without token → 401
- Access resource owned by another user → 403

**6. Boundary Values** (covered in 4.4):
- String too long (> max length) → 400
- String too short (< min length) → 400
- Number too large/small → 400

**What to Assert**:
1. Correct error status code (400, 401, 403, 422)
2. Error message exists
3. Error message is descriptive
4. Response structure (error format)

**Example: Login API Negative Tests** (10+ cases):
1. ❌ Missing username → 400/422
2. ❌ Missing password → 400/422
3. ❌ Empty username → 400/422
4. ❌ Empty password → 400/422
5. ❌ Null username → 400
6. ❌ Null password → 400
7. ❌ Invalid email format → 400/422
8. ❌ Wrong password → 401
9. ❌ Non-existent user → 401
10. ❌ Username as integer → 400
11. ❌ Password as boolean → 400
12. ❌ Extra unknown fields → 200 (ignored) or 400

**What to Skip**:
- ❌ SQL injection testing
- ❌ XSS testing
- ❌ Deep security testing

**Interview Questions**:
- Q: Give 5 negative test cases for login API
- Q: What status code for missing required field?
- Q: Difference between 400 and 422?
  - **400**: Generic bad request, malformed JSON
  - **422**: Valid JSON but semantic validation failed

---

### Topic 4.4: Boundary Testing (1 hour)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:

**What is Boundary Testing?**
- Test at limits/edges of acceptable values
- Min, max, just below min, just above max

**Examples**:

**String Length**:
- Username: min=3, max=50
  - Test: 2 chars → 400 (below min)
  - Test: 3 chars → 200 (min, valid)
  - Test: 50 chars → 200 (max, valid)
  - Test: 51 chars → 400 (above max)

**Numeric Ranges**:
- Age: min=0, max=120
  - Test: -1 → 400 (below min)
  - Test: 0 → 200 (min, valid)
  - Test: 120 → 200 (max, valid)
  - Test: 121 → 400 (above max)

**Special Values**:
- 0 (zero)
- -1 (negative)
- Empty string ""
- Empty array []
- Null

**What to Skip**:
- ❌ Equivalence partitioning theory

**Interview Questions**:
- Q: What's boundary value analysis?
- Q: Give boundary test cases for age field (0-120)

---

### Topic 4.5: Test Chaining / Integration Testing (30 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:

**What is Test Chaining?**
- Use output of one API as input to another
- Test realistic user workflows
- Verify data consistency across APIs

**Example Flow**:
1. **POST /users** → Create user → Get user_id
2. **POST /auth/login** → Login with user → Get token
3. **GET /users/{user_id}** → Get user profile with token
4. Assert: Profile data matches created user data

**What to Assert**:
- Each API returns correct status
- Data flows correctly between APIs
- Data consistency (same user_id, username)

**What to Skip**:
- ❌ Complex multi-step workflows (save for real tests)

---

### Topic 4.6: Idempotency Testing (30 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:

**What is Idempotency?**
- Same request → Same result (even if repeated)

**Idempotent Methods**:
- **GET**: Always returns same data
- **PUT**: Replace resource → Same result if repeated
- **DELETE**: Delete resource → 404 if repeated (still idempotent)

**Non-Idempotent Methods**:
- **POST**: Create resource → Multiple calls create multiple resources

**How to Test**:
1. Send PUT/DELETE request
2. Send same request again
3. Assert same result

**Example**:
```
DELETE /users/123 → 204 No Content
DELETE /users/123 → 404 Not Found (idempotent - same end state)
```

**What to Skip**:
- ❌ Deep idempotency theory

**Interview Questions**:
- Q: What's idempotency?
- Q: Is POST idempotent? Why not?
- Q: How do you test idempotency of PUT?

---

## Part 5: Test Data & Validation (2 hours)

### Topic 5.1: Test Data Strategies (45 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:

**Types of Test Data**:
1. **Static Data**: JSON files, CSV files (test_data/)
2. **Dynamic Data**: Generated on-the-fly (Faker library)
3. **Data Models**: Pydantic models for validation

**Static Data** (JSON file):
```json
{
  "valid_user": {
    "username": "test@example.com",
    "password": "Test@123"
  },
  "invalid_user": {
    "username": "invalid",
    "password": "wrong"
  }
}
```

**Dynamic Data** (Faker):
```python
from faker import Faker
fake = Faker()
email = fake.email()
name = fake.name()
```

**When to Use Each**:
- Static: Predictable scenarios, specific test cases
- Dynamic: Unique data needed (avoid conflicts), exploratory testing

**What to Skip**:
- ❌ Database seeding
- ❌ Test data management tools

---

### Topic 5.2: Response Validation (45 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:

**What to Validate**:
1. Status code
2. Response structure (keys exist)
3. Data types (string, int, bool)
4. Data values (expected data)
5. Required fields present

**Example Validations**:
```python
assert response.status_code == 200
data = response.json()
assert 'token' in data
assert 'user' in data
assert isinstance(data['user']['id'], int)
assert data['user']['username'] == expected_username
```

**What to Skip**:
- ❌ JSON Schema validation (learn later if needed)
- ❌ Complex validation libraries

---

### Topic 5.3: JSON Schema Validation (30 mins)
**Depth**: 🟢 **SHALLOW** (optional)

**What to Learn** (Concept only):
- JSON Schema defines expected structure
- Validates response against schema
- Ensures all required fields exist with correct types

**Example Schema**:
```json
{
  "type": "object",
  "properties": {
    "user_id": {"type": "integer"},
    "username": {"type": "string"},
    "email": {"type": "string"}
  },
  "required": ["user_id", "username"]
}
```

**What to Skip**:
- ❌ Writing complex schemas
- ❌ Schema generation tools

---

## Part 6: Pytest Fundamentals (1 hour for theory)

### Topic 6.1: Pytest Basics (30 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:

**Test Structure**:
```python
def test_something():
    # Arrange: Setup
    data = {...}
    
    # Act: Execute
    response = api.post('/endpoint', json=data)
    
    # Assert: Verify
    assert response.status_code == 200
```

**Test Naming**:
- `test_<action>_<expected_result>`
- `test_login_with_valid_credentials`
- `test_login_with_invalid_password_returns_401`

**Assertions**:
```python
assert response.status_code == 200
assert 'key' in data
assert data['value'] == expected
```

**What to Skip**:
- ❌ Advanced pytest features (learn with framework)

---

### Topic 6.2: Test Markers (30 mins)
**Depth**: 🟡 **MEDIUM**

**What to Learn**:

**Purpose**:
- Categorize tests
- Run specific test groups
- Organize test suites

**Common Markers**:
```python
@pytest.mark.smoke      # Critical path, fast
@pytest.mark.sanity     # Key features
@pytest.mark.regression # Full suite
@pytest.mark.negative   # Negative tests
```

**Running with Markers**:
```bash
pytest -m smoke         # Run only smoke tests
pytest -m "not slow"    # Exclude slow tests
```

**What to Skip**:
- ❌ Custom marker configuration (learn with framework)

---

## Part 7: Requests Library (1 hour for theory)

### Topic 7.1: Requests Basics (30 mins)
**Depth**: 🟡 **MEDIUM** (Practice will be with framework)

**What to Learn**:

**Making Requests**:
```python
import requests

# GET request
response = requests.get('https://api.example.com/users')

# POST request
response = requests.post(
    'https://api.example.com/auth',
    json={'username': 'user', 'password': 'pass'}
)

# Headers
headers = {'Authorization': 'Bearer token'}
response = requests.get(url, headers=headers)
```

**Response Object**:
```python
response.status_code  # 200, 404, etc.
response.text         # Raw text
response.json()       # Parsed JSON
response.headers      # Response headers
response.elapsed      # Response time
```

**What to Skip**:
- ❌ Advanced requests features (learn with framework)

---

### Topic 7.2: Session & Error Handling (30 mins)
**Depth**: 🟢 **SHALLOW** (Your framework handles this)

**What to Learn** (Concepts):

**Session** (reuses connection):
```python
session = requests.Session()
session.get(url)  # Connection reused
```

**Error Handling**:
```python
try:
    response = requests.get(url, timeout=30)
    response.raise_for_status()  # Raises exception for 4xx/5xx
except requests.exceptions.Timeout:
    # Handle timeout
except requests.exceptions.ConnectionError:
    # Handle connection error
```

**What to Skip**:
- ❌ Custom adapters, retries (your framework implements this)

---

## ✅ Summary: What You'll Know After 15 Hours

### HTTP Fundamentals
- ✅ HTTP methods (GET, POST, PUT, PATCH, DELETE)
- ✅ Status codes (200, 201, 400, 401, 403, 404, 500)
- ✅ Headers (Content-Type, Authorization, Accept)

### REST APIs
- ✅ REST principles (stateless, resource-based)
- ✅ JSON format and parsing
- ✅ REST vs SOAP (high-level)

### Authentication
- ✅ JWT tokens (structure, expiry, usage)
- ✅ Bearer token authentication
- ✅ 401 vs 403 difference

### API Testing
- ✅ Positive testing (happy path)
- ✅ Negative testing (10+ categories)
- ✅ Boundary testing (min, max, edge cases)
- ✅ Idempotency
- ✅ Test chaining

### Test Data & Validation
- ✅ Static vs dynamic test data
- ✅ Response validation techniques

### Pytest & Requests
- ✅ Test structure and naming
- ✅ Test markers (smoke, sanity, regression)
- ✅ Basic requests usage

---

## 📖 Study Resources (Recommended)

### Quick References
- HTTP Status Codes: https://httpstatuses.com/
- REST API Tutorial: https://restfulapi.net/
- JWT.io: https://jwt.io/ (decode tokens)
- Reqres.in: https://reqres.in/ (practice API)

### For Practice
- Use Postman or requests library to practice
- Test https://reqres.in/ endpoints
- Decode JWT tokens at jwt.io

---

## 🎯 After 15 Hours → Move to Framework

Once theory is complete, you'll:
1. Understand your framework code (easier now!)
2. See how theory applies in practice
3. Explain design decisions with confidence

**Next Document**: Framework Learning Plan (25 hours)

---

## 💡 Learning Tips

1. **Don't memorize** - understand concepts
2. **Focus on DEEP topics** - interviewers ask these
3. **Skip what's marked SKIP** - waste of time
4. **Take notes** - in your own words
5. **Practice explaining** - teach to imaginary interviewer

**You got this!** 💪


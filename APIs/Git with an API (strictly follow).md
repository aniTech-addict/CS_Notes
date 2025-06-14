### **Best Practices for API Keys in Python Projects (esp. with Git):**

#### 1. **Create a `.env` file (never commit this!)**

This is where your **real secrets** live:

.env (file_name)
`API_KEY=your_real_api_key_goes_here`

---

#### 2. **Create a `.env.example` file (safe to commit)**

This acts like a _template_ for others to fill in:

.env

`API_KEY=your_api_key_here`

---

#### 3. **Add `.env` to your `.gitignore`**

To keep your real keys out of version control:

`# .gitignore 
	.env`

---

#### 4. **Load `.env` in your script using `python-dotenv`**

Install it if you haven’t:

`pip install python-dotenv`

Then use it like this:

python
```python
from dotenv import load_dotenv
import os  load_dotenv()  # loads from .env  API_KEY = os.getenv("API_KEY")  print(API_KEY)  # Use it in your requests
```

---
#### 🔒 Why this matters:

- Keeps **your API key safe** from leaks.
    
- Makes **collaboration easier**.
    
- Lets you have **different keys** for dev, prod, test.


## Error Handling

```python
except requests.exceptions.HTTPError as http_err:

        print(f"HTTP error occurred for city '{city_name}': {http_err} - Status code: {http_err.response.status_code}")

    except requests.exceptions.RequestException as req_err:  
    # For other network issues (DNS failure, connection refused, timeout)

        print(f"Network error occurred for city '{city_name}': {req_err}")

    except ValueError as json_err:  # If response.json() fails (e.g. response is not valid JSON)

        print(f"JSON parsing error for city '{city_name}': {json_err}")

    except Exception as e:  # For any other unexpected exceptions

        print(f"An unexpected error occurred for city '{city_name}': {e}")

    return None # indicate failure
```
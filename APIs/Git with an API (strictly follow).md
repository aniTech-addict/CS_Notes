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

`# .gitignore .env`

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
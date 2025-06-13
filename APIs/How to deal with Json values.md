
When you get a JSON response from an API, the return value that data is often already a Python dictionary if the `requests` library's `.json()` method was used.

``` python 
python_dict = response.json()  #returns a python dict is repose is valid json
```




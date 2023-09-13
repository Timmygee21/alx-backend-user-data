# 0x03. User authentication service  

- Table of Contents  
- Declare API Routes  
- Working with Cookies  
- Retrieving Form Data  
- Returning HTTP Status Codes  

#Declare API Routes  
In a Flask web application, you can create API routes to handle different URL endpoints and HTTP methods. Here's how to do it:

1. Import Flask: Start by importing the `Flask` class from the `flask` module.

`from flask import Flask`

2. Create an Application Instance: Initialize a Flask application instance.

`app = Flask(__name__)`

3. Define Route Handlers: Define functions to handle specific API endpoints using decorators provided by Flask.

```
@app.route('/api/v1/hello', methods=['GET'])
def hello():
    return 'Hello, World!'
```

4. Accessing URL Parameters: Capture dynamic values from URLs using placeholders.

```
@app.route('/api/v1/user/<username>', methods=['GET'])
def get_user(username):
    return f'Retrieving info for user: {username}'
```

5. HTTP Methods and Multiple Routes: Specify multiple HTTP methods and route handlers for the same URL.

```
@app.route('/api/v1/item/<int:item_id>', methods=['GET', 'PUT', 'DELETE'])
def item_details(item_id):
    # Handle GET, PUT, and DELETE methods
```

6. Running the Application: Start the Flask application.

```
if __name__ == '__main__':
    app.run()
```

## Working with Cookies  
Flask allows you to work with cookies to store user-specific information or session data.

1. Retrieving Cookies: Access cookies using the `request.cookies` dictionary.

`username = request.cookies.get('username')`

2. Setting Cookies: Set cookies using the `make_response` function and `set_cookie` method.

```
from flask import make_response

response = make_response('Cookie set!')
response.set_cookie('username', 'example_user')
return response
```

### Retrieving Form Data  
Retrieve form data from POST requests using the `request` object.

1. Handle POST Requests: Create a route that handles POST requests and retrieve form data.

```
@app.route('/submit', methods=['POST'])
def submit_form():
    username = request.form.get('username')
    password = request.form.get('password')
    return f'Received username: {username}, password: {password}'
```

### Returning HTTP Status Codes  
Return appropriate HTTP status codes to indicate request outcomes.

1. Return Status Codes: Return different status codes using the `return` statement along with `jsonify`.

```
from flask import jsonify

@app.route('/success')
def success():
    return jsonify({"message": "Request was successful"}), 200
```


Customize messages and codes as needed.

# 0x01. Basic authentication  

## Authentication, Base64 Encoding, and Basic Authentication Explained  
This repository provides a brief overview of key concepts related to authentication, Base64 encoding, and Basic Authentication. Understanding these concepts is essential when working with APIs and securing communication between clients and servers.

## Table of Contents  
- Authentication  
- Base64 Encoding  
- Encoding a String in Base64  
- Basic Authentication  
- Sending the Authorization Header  

## Authentication  
Authentication is the process of verifying the identity of a user, system, or application. It ensures that the entity requesting access to a resource is indeed who it claims to be. In the context of web services and APIs, authentication mechanisms are used to ensure that only authorized users or systems can access specific resources.

## Base64 Encoding  
Base64 is a binary-to-text encoding scheme that converts binary data into a string of ASCII characters. It's commonly used to encode binary data like images, audio files, or binary data in authentication mechanisms. This encoding is necessary when you need to include binary data within formats that only support text representation, such as JSON or XML.

## Encoding a String in Base64  
To encode a string in Base64, follow these steps:

1. Take the input string and break it down into individual bytes.  
2. Convert each byte into its binary representation.  
3. Concatenate all the binary representations to form a single binary string.  
4. Split the binary string into groups of 6 bits each (Base64 uses groups of 6 bits).  
5. Convert each group of 6 bits into its decimal equivalent.  
6. Map the decimal values to the Base64 character set (usually A-Z, a-z, 0-9, '+' and '/').  

Example in Python:

```
import base64

input_string = "Hello, Base64!"
encoded_bytes = base64.b64encode(input_string.encode("utf-8"))
encoded_string = encoded_bytes.decode("utf-8")

print("Encoded string:", encoded_string)
```

## Basic Authentication  
Basic Authentication is a simple authentication mechanism. It involves sending a username and password with each request to access a protected resource. However, due to the insecure nature of sending plaintext passwords, Basic Authentication should always be used over a secure connection like HTTPS.

## Sending the Authorization Header  
To send the Authorization header for Basic Authentication in an HTTP request, create a string in the format "username:password" and encode it using Base64. Include the resulting Base64-encoded string in the `Authorization` header of the request.

Example using Python's `requests` library:

```
import requests
import base64

url = "https://api.example.com/resource"
username = "your_username"
password = "your_password"

# Encode username and password in Base64
credentials = base64.b64encode(f"{username}:{password}".encode("utf-8")).decode("utf-8")

headers = {
    "Authorization": f"Basic {credentials}"
}

response = requests.get(url, headers=headers)
print(response.status_code)
```

Remember, while Basic Authentication is easy to implement, it's not the most secure method. Consider using more secure authentication methods, especially in production applications.

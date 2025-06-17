# Server-side Vulnerabilities

## Path traversal
Path traversal (also known as directory traversal) vulnerabilities enable an attacker to interact with arbitrary files on the server, giving them access to sensitive data. If they can also write to these files, they can potentially modify application data or behavior, ultimately taking full control of the server.

- Reading arbitrary files via path traversal

## Access control
Access controls are designed to prevent users from interacting with data or functionality for which they don't have the relevant permissions. Due to the obvious security impact, broken access controls are critical bugs in their own right. They often also provide access to more attack surface, which could contain additional vulnerabilities.

- Vertical privilege escalation
- Unprotected functionality
- Parameter-based access control methods
- Horizontal privilege escalation
- Horizontal to vertical privilege escalation

## Authentication
Authentication is the process of checking that a user really is who they claim to be. For example, a login form where you enter your username and password is one form of authentication mechanism. Flawed authentication mechanisms may allow an attacker to guess valid sets of credentials by automating thousands of login attempts using specialist tools like Burp Intruder.

- Brute-force attacks
- Brute-forcing usernames
- Brute-forcing passwords
- Username enumeration
- Bypassing two-factor authentication


## Server-side request forgery (SSRF)
SSRF vulnerabilities enable an attacker to trigger malicious server-to-server requests to unintended URLs. As the server issuing the request is likely to have a strong trust relationship with other systems on the network, the attacker can potentially abuse this behavior to access data, functionality, and services that are not meant to be exposed to external users.

- SSRF attacks against the server
- SSRF attacks against other back-end systems

## File upload vulnerabilities
Any functionality that enables users to upload files to the server's filesystem are inherently dangerous. Failing to enforce proper restrictions on the files that users are allowed to upload can potentially enable an attacker to run arbitrary system commands, giving them full control over the server.

- Exploiting unrestricted file uploads to deploy a web shell
- Exploiting flawed validation of file uploads
- Flawed file type validation
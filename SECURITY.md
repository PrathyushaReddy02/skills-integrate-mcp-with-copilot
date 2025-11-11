# Security Policy

This repository follows a small, practical security policy to help contributors and maintainers keep the project safe.

## Reporting a Vulnerability

- If you discover a security vulnerability, please report it privately to the repository owner via email: security@EXAMPLE.com (replace with a real contact).
- Do not open an issue with exploit details. Public disclosure may put users at risk.

## Supported Response

- We will acknowledge receipt within 2 business days and provide a timeline for a fix.
- Critical vulnerabilities will be prioritized and patched as soon as possible.

## Handling Secrets

- Never commit secrets, credentials, API keys, or private certificates to the repository.
- Use environment variables for configuration and keep a `.env.example` (this repository includes one) to show required keys.
- If a secret is accidentally committed, rotate the secret immediately and notify repository maintainers.

## Secure Coding Guidance (quick checklist)

- Use parameterized queries / ORM for database access to prevent SQL injection.
- Hash passwords with a strong algorithm (bcrypt) and never store plaintext passwords.
- Validate and sanitize all user inputs.
- Restrict file uploads by MIME type and size; sanitize filenames before saving.
- Use HTTPS in production and secure cookies/sessions.

## Contact

If you need to reach the maintainers for a security issue, use: security@EXAMPLE.com
# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in this project, please email us instead of using the issue tracker. For security issues, please contact the maintainers directly rather than opening a public issue.

## Security Best Practices

This project follows industry-standard security practices to protect student and teacher data:

### 1. Password Security ✅
- All passwords are hashed using **bcrypt** via `passlib` before storage
- Plaintext passwords are **never** stored or logged
- Passwords meet minimum complexity requirements

### 2. Secrets Management ✅
- **Never** commit sensitive information to version control:
  - Database credentials
  - API keys
  - Authentication tokens
  - Teacher passwords

- All secrets must be stored in environment variables
- Use `.env` files locally (see `.env.example`)
- Configure environment variables in production deployment platform

### 3. Input Validation ✅
- Email inputs are validated to prevent injection attacks
- Query parameters are sanitized to prevent SQL injection
- File uploads (when implemented) will validate MIME types and prevent directory traversal

### 4. Database Security ✅
- SQLAlchemy ORM is used to prevent SQL injection
- Parameterized queries for all database operations
- Input validation on all user-provided data

### 5. Environment Configuration ✅
- Load configuration from environment variables using `python-dotenv`
- Use separate configs for development, testing, and production
- Example configuration file provided in `.env.example`

## Security Checklist

Before deploying to production:

- [ ] All secrets are in environment variables, not hardcoded
- [ ] `.env` file is added to `.gitignore` (already configured)
- [ ] Passwords are hashed using `passlib` + `bcrypt`
- [ ] All user inputs are validated
- [ ] HTTPS is enabled in production
- [ ] CORS is configured appropriately
- [ ] Database credentials are secure
- [ ] Sensitive logs are redacted
- [ ] Security headers are configured (Content-Security-Policy, etc.)
- [ ] Dependencies are kept up to date

## Dependencies

Security-related packages used:
- **passlib**: Secure password hashing
- **python-dotenv**: Environment variable management
- **FastAPI**: Built-in security features (CORS, validation)
- **SQLAlchemy**: ORM for secure database operations

Keep all dependencies updated:
```bash
pip install --upgrade -r requirements.txt
```

## Future Enhancements

- [ ] Add CSRF protection
- [ ] Implement rate limiting
- [ ] Add request signing for sensitive operations
- [ ] Encrypt sensitive data at rest
- [ ] Add audit logging
- [ ] Implement secrets rotation policy
- [ ] Add security testing to CI/CD pipeline

## References

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [FastAPI Security](https://fastapi.tiangolo.com/tutorial/security/)
- [passlib Documentation](https://passlib.readthedocs.io/)

# spring-boot-keycloak-sample3

[![Java CI with Maven](https://github.com/hendisantika/spring-boot-keycloak-sample3/actions/workflows/maven.yml/badge.svg)](https://github.com/hendisantika/spring-boot-keycloak-sample3/actions/workflows/maven.yml)
![Java](https://img.shields.io/badge/Java-25-orange?logo=openjdk)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.1.x-6DB33F?logo=springboot)
![Keycloak](https://img.shields.io/badge/Keycloak-26-4D4D4D?logo=keycloak)
[![Dependabot](https://img.shields.io/badge/Dependabot-enabled-025E8C?logo=dependabot)](.github/dependabot.yml)

Sample Spring Boot **OAuth2 Resource Server** secured by **Keycloak** (JWT + role-based access control).

### Tech Stack

| Component         | Version                         |
|-------------------|---------------------------------|
| Java (JDK)        | 25 (Temurin recommended)        |
| Spring Boot       | 4.1.x                           |
| Spring Security   | OAuth2 Resource Server (JWT)    |
| Build tool        | Maven Wrapper (`./mvnw`)        |
| Keycloak          | 26.x (via Docker Compose)       |
| Lombok            | managed by Spring Boot          |

> **Note (JDK 23+):** `javac` no longer runs annotation processors implicitly, so Lombok and
> `spring-boot-configuration-processor` are registered explicitly in `maven-compiler-plugin`
> → `annotationProcessorPaths` inside `pom.xml`.

### What is Keycloak

Keycloak is an open-source identity and access management solution developed by Red Hat. It provides a centralized
platform for managing user authentication, authorization, and other security features across multiple applications and
services.
Keycloak simplifies the process of securing applications by handling common security tasks such as user authentication,
user management, and authorization, so developers can focus on building their application functionality.

### Key Features of Keycloak:

1. Single Sign-On (SSO):
   Keycloak supports SSO, allowing users to log in once and gain access to multiple applications without needing to log
   in again. This is useful for organizations with multiple applications that need a consistent authentication
   mechanism.
2. Identity Brokering and Social Login:
   Keycloak can integrate with external identity providers, such as social login platforms (e.g., Google, Facebook,
   GitHub) and enterprise identity providers (e.g., LDAP, SAML, OpenID Connect).
3. User Federation:
   Keycloak allows integration with existing user directories such as LDAP or Active Directory. This means that Keycloak
   can act as a bridge between an application and an existing user store.
4. OAuth2, OpenID Connect, and SAML 2.0 Support:
   Keycloak supports industry-standard protocols for authentication and authorization like OAuth2, OpenID Connect (
   OIDC), and SAML 2.0, making it easier to integrate with a wide range of applications and services.
5. User Management:
   Keycloak provides a comprehensive user management interface, where admins can manage user accounts, roles, groups,
   and permissions. Users can also self-register, change passwords, and manage account details.
6. Role-Based Access Control (RBAC):
   Keycloak enables role-based access control, where different users or user groups can be assigned specific roles,
   which determine the level of access they have to the system.
7. Multi-Factor Authentication (MFA):
   Keycloak supports multi-factor authentication, allowing for stronger security by requiring users to provide
   additional verification methods such as OTP (one-time password) in addition to their password.
8. Password Policies:
   Keycloak supports customizable password policies, including rules like password expiration, complexity, and length.
9. Session Management:
   Keycloak handles session management, including login sessions, logout, session timeouts, and token management.
10. Extensible and Customizable:
    Keycloak is highly customizable. It allows you to write your own extensions for authentication mechanisms, user
    management features, and custom login forms.

### How Keycloak Works:

1. Authentication Flow:
   When a user tries to access a protected resource, they are redirected to Keycloak for authentication. Keycloak
   handles the login, generates a token for the user, and then redirects them back to the application with this token.
   The application can then use the token to identify and authorize the user.
2. Identity Providers:
   Keycloak can act as an identity broker, allowing users to log in via external identity providers such as Google,
   Facebook, or any OAuth2, OpenID Connect, or SAML 2.0-based provider.
3. Token-Based Security:
   After authenticating a user, Keycloak issues tokens such as Access Tokens and ID Tokens (in the case of OpenID
   Connect). These tokens contain information about the user and their roles and can be used by applications to
   authorize access to resources.
4. Admin Console:
   Keycloak comes with an easy-to-use admin console that allows administrators to configure the system, manage users,
   roles, and permissions, and monitor user sessions.
5. Customizable Login Pages:
   You can customize Keycloak’s default login page to match your application’s branding or to add additional features.

### Common Use Cases:

	1.	Single Sign-On (SSO) for web applications within an organization.
	2.	Identity Federation, integrating with external identity providers (e.g., LDAP, Google, etc.).
	3.	Multi-Factor Authentication (MFA) to enhance security for sensitive applications.
	4.	API Security using OAuth2 and OpenID Connect to protect APIs with token-based authentication.
	5.	User Management and Authentication for microservices architectures, where managing users and security in a centralized manner is important.

### Integration with Applications:

	•	Keycloak can be integrated with applications using standard security protocols such as OAuth2, OpenID Connect, and SAML 2.0. Many modern frameworks and languages have libraries to simplify this integration.
	•	Popular frameworks like Spring Boot, Node.js, Angular, and React have libraries that make Keycloak integration easier.

### Example Applications of Keycloak:

	•	Securing REST APIs: Keycloak can issue JWT tokens that can be used to secure REST APIs.
	•	Microservices Security: In a microservices architecture, Keycloak can centralize authentication and authorization for all services.
	•	Enterprise Identity Management: Keycloak provides a central identity management system for large organizations with many users and systems.

### Architecture:

	•	Realms: A realm in Keycloak represents a tenant. You can have multiple realms in one Keycloak instance, each managing its own users, clients, roles, etc.
	•	Clients: Clients are applications that require Keycloak to authenticate users and manage security (e.g., web applications, mobile apps, REST APIs).
	•	Users: End-users who need access to the system.
	•	Roles: Define permissions that users have within the system.
	•	Groups: Used to group users together for easier role and permission management.

### Prerequisites

- JDK 25 (e.g. [Eclipse Temurin 25](https://adoptium.net/))
- Docker & Docker Compose
- Postman (optional, for testing the API)

Verify your JDK:

```shell
java -version   # should print version "25..."
```

### Things to do list:

1. Clone this repository: `git clone https://github.com/hendisantika/spring-boot-keycloak-sample3.git`
2. Navigate to the folder: `cd spring-boot-keycloak-sample3`
3. Run keycloak compose: `docker compose up -d`
4. Open Keycloak admin console at http://localhost:7080 (`admin` / `admin`)
5. Import keycloak realm file `PowerRanger.json`
6. Build & run the tests: `./mvnw clean verify`
7. Run the application: `./mvnw spring-boot:run` (app runs on http://localhost:8080)
8. Open Postman App
9. Import Postman Collection file `Spring Boot Keycloak Sample 3.postman_collection.json`

### API Endpoints

| Method | Endpoint              | Access                     |
|--------|-----------------------|----------------------------|
| GET    | `/api/hello`          | Public                     |
| GET    | `/api/admin`          | Role `admin`               |
| GET    | `/api/user`           | Role `user`                |
| GET    | `/api/admin-and-user` | Role `admin` or `user`     |

Roles are read from the `resource_access.green_ranger.roles` claim of the JWT issued by realm `PowerRanger`.

Example:

```shell
TOKEN=$(curl -s -X POST http://localhost:7080/realms/PowerRanger/protocol/openid-connect/token \
  -d grant_type=password -d client_id=green_ranger -d client_secret=<client-secret> \
  -d username=<username> -d password=<password> | jq -r .access_token)

curl -H "Authorization: Bearer $TOKEN" http://localhost:8080/api/admin
```

### Continuous Integration

GitHub Actions workflow [`.github/workflows/maven.yml`](.github/workflows/maven.yml):

- Runs on push / pull request to `main` and manually (`workflow_dispatch`)
- Sets up **Temurin JDK 25** with Maven cache and runs `./mvnw -B -ntp verify`
- Uploads Surefire test reports and the built jar as workflow artifacts
- Least-privilege `permissions` and `concurrency` (cancels outdated runs)

### Dependency Updates (Dependabot)

[`.github/dependabot.yml`](.github/dependabot.yml) keeps dependencies up to date:

| Ecosystem        | Schedule (Asia/Jakarta) | Notes                                                        |
|------------------|-------------------------|--------------------------------------------------------------|
| `maven`          | daily 05:00             | Spring updates grouped, other minor/patch updates grouped    |
| `github-actions` | daily 05:00             | All actions grouped in a single PR                           |
| `docker-compose` | weekly (Monday) 05:00   | Keycloak, PostgreSQL & pgAdmin images                        |

### Conclusion:

Keycloak simplifies security for applications by providing a centralized authentication and authorization system.
Its flexibility, open standards support, and extensibility make it a great choice for enterprises and developers who
want to add security to their applications without building their own security infrastructure from scratch.

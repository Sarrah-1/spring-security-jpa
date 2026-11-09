# TP 11 – Authentification JDBC / JPA (Spring Security)

Projet Spring Boot 3.3 / Java 17 : authentification par base MySQL (JPA), `UserDetailsService`
personnalisé et mots de passe hachés avec BCrypt.

## Prérequis
- Java 17+
- Maven 3.9+
- MySQL en marche sur `localhost:3306` (utilisateur `root`, mot de passe vide – à adapter dans
  `src/main/resources/application.properties`)

## Base de données
La base est créée automatiquement (`createDatabaseIfNotExist=true`). Pour la créer à la main :

```sql
CREATE DATABASE security_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

## Lancement
```bash
mvn spring-boot:run
```
Puis ouvrir http://localhost:8080/login

## Comptes créés au démarrage (`DatabaseInitializer`)
| Utilisateur | Mot de passe | Rôles               | Accès                                  |
|-------------|--------------|---------------------|----------------------------------------|
| admin       | 1234         | ROLE_ADMIN, ROLE_USER | `/admin/dashboard`, `/user/dashboard` |
| user        | 1111         | ROLE_USER           | `/user/dashboard`                      |

## Vérifications dans MySQL
```sql
USE security_db;
SHOW TABLES;                 -- user, role, user_roles
SELECT username, password FROM user;   -- mots de passe en $2a$... (BCrypt)
```

## Structure
```
src/main/java/ma/fstg/security
├── SpringSecurityJpaApplication.java
├── entities/        Role, User
├── repositories/    RoleRepository, UserRepository
├── services/        CustomUserDetailsService
├── config/          SecurityConfig, DatabaseInitializer
└── controllers/     AuthController (login, home, register, dashboards)
```

## Notes
- L'initialiseur ne recrée pas les comptes s'ils existent déjà (pas de doublons au redémarrage).
- La page `/register` crée un compte avec le rôle `ROLE_USER`.
- La déconnexion se fait par POST (protection CSRF activée par défaut).

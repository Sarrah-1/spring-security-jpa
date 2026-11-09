# TP 11 – Authentification JDBC / JPA (Spring Security)

## Comptes créés au démarrage (`DatabaseInitializer`)
| Utilisateur | Mot de passe | Rôles               | Accès                                  |
|-------------|--------------|---------------------|----------------------------------------|
| admin       | 1234         | ROLE_ADMIN, ROLE_USER | `/admin/dashboard`, `/user/dashboard` |
| user        | 1111         | ROLE_USER           | `/user/dashboard`                      |


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

## Screen

<img width="878" height="328" alt="image" src="https://github.com/user-attachments/assets/11a2c373-3dc0-4de5-ad55-dda972588947" />

<img width="257" height="257" alt="image" src="https://github.com/user-attachments/assets/f68a7803-8a78-4cd7-851a-a125e8ac4aad" />

<img width="357" height="200" alt="image" src="https://github.com/user-attachments/assets/ff094ca3-dbe1-4b04-950f-b7f6d484f02e" />

<img width="369" height="176" alt="image" src="https://github.com/user-attachments/assets/ac08d65c-78b3-4493-b20f-6ca36e618a63" />

<img width="405" height="177" alt="image" src="https://github.com/user-attachments/assets/a710001b-82fd-4dd6-86b8-5ce75115e002" />

<img width="410" height="160" alt="image" src="https://github.com/user-attachments/assets/2ec4e24e-4897-4a38-8f72-8cb269000a60" />

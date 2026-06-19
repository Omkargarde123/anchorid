# AnchorID — Decentralized Identity Recovery Platform

A provider-independent identity layer that links multiple authentication methods to **one permanent identity** — so users never lose account access even if a single auth provider (like Google) goes down.

---

## 💡 Problem It Solves

Most apps tie your identity to a single provider (Google, Facebook, etc.). If that provider has an outage, gets compromised, or you lose access to it — you lose your account. **AnchorID decouples identity from any single provider** by linking multiple auth methods to one permanent, recoverable identity.

---

## ✨ Features

- 🔗 **Multi-provider linking** — Google OAuth, Email OTP, Phone OTP, and AnchorID native credentials all map to one identity
- 🔄 **Fallback recovery workflows** — If one auth method fails, fall back to another to regain access
- 🧑‍💻 **Multi-session handling** — Manage multiple active sessions per identity
- 🛡 **No single point of failure** — Eliminates dependency on any one authentication provider

---

## 🏗 Architecture

```
                    ┌─────────────────────────────┐
                    │        Client (Browser)       │
                    └───────────────┬───────────────┘
                                    │
                          REST API (Express.js)
                                    │
              ┌─────────────────────┼─────────────────────┐
              ▼                     ▼                      ▼
     ┌────────────────┐   ┌────────────────┐    ┌────────────────────┐
     │  Google OAuth   │   │   Email OTP     │    │     Phone OTP        │
     │    Provider     │   │   Verification   │    │   Verification       │
     └────────┬────────┘   └────────┬────────┘    └──────────┬──────────┘
              │                     │                        │
              └─────────────────────┼────────────────────────┘
                                    ▼
                    ┌───────────────────────────────┐
                    │      Identity Resolver Layer    │
                    │  (Maps any auth method → one    │
                    │   permanent AnchorID identity)  │
                    └───────────────┬─────────────────┘
                                    ▼
                    ┌───────────────────────────────┐
                    │      PostgreSQL / MySQL DB      │
                    │  Users · Linked Auth Methods ·  │
                    │  Sessions · Recovery Tokens      │
                    └───────────────────────────────┘
```

**Flow:**
1. User signs in via any linked method (Google OAuth, Email OTP, Phone OTP, or native credentials)
2. Express.js API authenticates the request and passes it to the Identity Resolver
3. Resolver maps the auth method to the user's permanent AnchorID identity in the database
4. Session is created; if a provider is unavailable, the user can fall back to another linked method

---

## 🛠 Tech Stack

| Component | Technology |
|---|---|
| Backend | Node.js, Express.js |
| Database | PostgreSQL / MySQL |
| Auth | Google OAuth, Email OTP, Phone OTP, Native Credentials |
| API Style | RESTful APIs |

---

## 🚀 How to Run

```bash
git clone https://github.com/Omkargarde123/anchorid.git
cd anchorid
npm install

# Set up environment variables
cp .env.example .env
# Fill in DB credentials, Google OAuth client ID/secret, OTP service keys

# Run database migrations
npm run migrate

# Start the server
npm run dev
```

### Environment Variables Needed
```
DATABASE_URL=postgres://user:password@localhost:5432/anchorid
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
OTP_SERVICE_API_KEY=
JWT_SECRET=
```

---

## 📂 Project Structure

```
anchorid/
├── src/
│   ├── routes/          # API route handlers
│   ├── controllers/     # Business logic
│   ├── models/          # DB models/schema
│   ├── middleware/       # Auth middleware
│   └── services/        # OAuth/OTP integration services
├── migrations/          # DB migration files
├── .env.example
├── .gitignore
└── README.md
```

---

## 🚧 Current Status

This project is under active development. Current state of each auth method:

| Auth Method | Status |
|---|---|
| Google OAuth | ✅ Working |
| Email OTP | 🟡 In progress |
| Phone OTP | 🟡 In progress |
| AnchorID native credentials | ✅ Working |
| Fallback recovery workflow | 🟡 In progress |

---

## 🔭 Roadmap

- [ ] Complete Email OTP integration
- [ ] Complete Phone OTP integration
- [ ] Finish fallback recovery flow end-to-end
- [ ] Add rate limiting on OTP requests
- [ ] Add unit + integration tests
- [ ] Add admin dashboard for identity management

---

## 📌 What I Learned

Building AnchorID pushed me to think about identity systems beyond a single login provider — designing a schema that maps multiple auth methods to one canonical identity, handling token/session lifecycle securely, and building recovery flows that stay reliable even when one provider goes down.

---

## 👤 Author

**Onkar Garde**
[GitHub](https://github.com/Omkargarde123) · [LinkedIn](https://linkedin.com/in/onkar-garde-775364331)

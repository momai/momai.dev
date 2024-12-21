# momai.dev

A personal homepage built with Traefik for reverse proxying and secure integration with OAuth and OIDC providers, Google + Auth0. This project serves as a gateway to personal services and projects, focusing on simplicity, security, and scalability.

## Features
- Reverse proxy and load balancing using Traefik.
- OAuth/OIDC authentication for secure access.
- Modular and extensible Docker Compose setup.

## Getting Started
Clone the repository, configure your `.env` file with the required parameters, and start the services using Docker Compose.

```bash
git clone https://github.com/momai/momai.dev.git
cd momai.dev
cp .env.sample .env
docker-compose up -d
```
## OAuth/OIDC Configuration
Create an API and an application. Connect a custom domain and set up auth.example.dev as a CNAME.

### 1. Auth0 Settings
Configure the following settings in your Auth0 dashboard https://manage.auth0.com/:

- **Allowed Callback URLs:**  
  `https://auth-forward.example.dev/oauth2/callback`
  `https://auth.example.dev/oauth2/callback`
- **Allowed Logout URLs:**  
  `https://example.dev`
  `https://auth.example.dev`
- **Allowed Web Origins:**  
  `https://example.dev`
  `https://auth.example.dev`

- **Client Type:**  
  Client Secret (Post)

- **Connected API:**  

- **API Identifier:**  
  ``https://auth.example.dev/`

- **Allow Skipping User Consent:**  
  `True`

- **Permissions:**  
  - `read:openid`
  - `read:email`
  - `read:profile`

### 2. Google Cloud API Configuration
In the [Google Cloud Console](https://console.cloud.google.com/apis/credentials), configure the following:

1. **Create Client ID for Web Application.**
2. Add the following URLs to **Authorized JavaScript Origins**:
   - `https://${OAUTH2_PROXY_OIDC_ISSUER_URL#https://}` (`https://dev-bla-bla-bla.auth0.com` - auth0 domain)
   - `https://auth.example.dev`
3. Add the following URLs to **Authorized Redirect URIs**:
   - `https://${OAUTH2_PROXY_OIDC_ISSUER_URL}/login/callback` (auth0 domain)
   - `https://auth.example.dev/login/callback`

### 3. Secrets and Keys
- **Cookie Secret:** Generate a secure key using the following command:  
  ```bash
  openssl rand -base64 32
```

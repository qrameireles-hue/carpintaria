# Carpentry Site — Vintage + Store + PayPal (PHP 5.6)

## Run
```bash
cp src/.env.example src/.env
# Edite `src/.env` (senhas e PayPal)
docker compose up -d --build
# open http://localhost:8080
# Adminer: http://localhost:8081  (server: db | user: carpuser | pass: change_app | db: carpentry)
```

## Páginas
- `/` — Home vintage (arquitetura inglesa)
- `/request.php` — Solicitar serviço (medidas + fotos)
- `/chat.php` — Contato estilo chat
- `/store.php` — Loja com produtos/serviços
- `/cart.php` — Carrinho
- `/checkout.php` — Pagamento PayPal (criação e captura server-side)
- `/admin.php` — Painel (senha: `ADMIN_PASS` no `.env`)

## Segurança
- CSRF, PDO prepared, uploads validados, headers de segurança, CSP permitindo apenas PayPal, containers não-root, `allow_url_fopen=Off`.
- PayPal via cURL TLS 1.2, **server-verified** (`/api/checkout/create-order.php` e `/api/checkout/capture-order.php`).

## PayPal
- Defina em `src/.env`: `PAYPAL_ENV` (`sandbox` ou `live`), `PAYPAL_CLIENT_ID`, `PAYPAL_SECRET`.
- Sandbox: crie contas de teste no PayPal Developer e use o Client ID/Secret do app.

## Imagens
- Substitua `src/public/assets/eng*.jpg`, `texture.jpg` e `prod*.jpg` por imagens reais.

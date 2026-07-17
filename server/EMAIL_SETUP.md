EMAIL (SMTP) SETUP for TASKIFY

This file explains how to configure SMTP so OTP and other emails are delivered instead of being logged in dev mode.

1) Create `.env` in the `server` folder

You can copy `server/.env.example` and fill the values:

PowerShell (from project root):

```powershell
Set-Location 'e:\TASKIFY-main\TASKIFY-main\server'
Copy-Item .env.example .env
notepad .env # edit values: SMTP_USER, SMTP_PASS, JWT_SECRET, MONGO_URI
```

Or create directly with content (example for Gmail App Password):

```powershell
Set-Location 'e:\TASKIFY-main\TASKIFY-main\server'
@"
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_SECURE=false
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-app-password
CLIENT_URL=http://localhost:5173
JWT_SECRET=change_this_to_a_secret
MONGO_URI=mongodb://localhost:27017/taskify
NODE_ENV=development
PORT=3000
"@ > .env
```

Gmail-specific notes:
- Enable 2-Step Verification on your Google account.
- Create an App Password (Mail) and use that as `SMTP_PASS`.
- Using your regular Google password will likely be blocked.

Mailtrap (test inbox) example:

```text
SMTP_HOST=smtp.mailtrap.io
SMTP_PORT=2525
SMTP_SECURE=false
SMTP_USER=MAILTRAP_USER
SMTP_PASS=MAILTRAP_PASS
```

2) Restart the server

If you run the server with npm scripts from repo root:

```powershell
# from repo root
npm run dev
# or if you run server directly
node server/server.js
```

3) Verify logs and test endpoint

- If SMTP is NOT configured you'll see this warning when the app starts or when sending email:
  "⚠️ SMTP credentials not configured. Email sending will be simulated."

- On success sending an OTP you'll see a log like:
  "✅ OTP email sent to user@example.com"

Quick test: request an OTP for your email (replace port if different)

```bash
curl -X POST http://localhost:3000/api/user/send-otp \
  -H "Content-Type: application/json" \
  -d '{"email":"your-email@gmail.com","name":"Your Name","role":"client"}'
```

If the response is `OTP sent to your email. Please check your inbox.` then check your inbox or the Mailtrap inbox.

4) Troubleshooting

- If nodemailer errors appear in the console, copy the error and verify `SMTP_USER`/`SMTP_PASS` are correct and the host/port/secure setting matches your provider.
- For Gmail use `smtp.gmail.com` port `587` with `SMTP_SECURE=false` (STARTTLS) or port `465` with `SMTP_SECURE=true` (SSL).
- Confirm `NODE_ENV` value: production won't log stack traces.


If you'd like, I can also:
- Add Mailtrap fallback detection in code to automatically use Mailtrap when a `MAILTRAP` env is present.
- Add a short `server/README.md` and link these instructions.

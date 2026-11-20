MOBIPERKS — MANUAL M-PESA MEMBERSHIP WEBSITE

PAYMENT SETTINGS
- Membership: KSh 50 one-time.
- Method: M-PESA Send Money (manual; no STK push).
- Recipient number: 0738506826.
- Customer submits the transaction code shown in their M-PESA confirmation SMS.
- Every submission stays PENDING_REVIEW until the operator checks the actual M-PESA account/statement and approves it.
- Never request an M-PESA PIN. Customers must confirm the recipient name displayed by Safaricom before sending.

WHAT IS INCLUDED
- Responsive public website (index.html).
- Node.js backend for registration, login, referral codes and payment submissions.
- Passwords hashed using scrypt.
- Private operator payment-review page at /admin.html.
- Persistent JSON data file when deployed with the included Render disk configuration.
- Health endpoint at /health.

LOCAL TEST
1. Install Node.js 20 or newer.
2. Extract this folder and open a terminal inside it.
3. Set ADMIN_REVIEW_KEY to a long random secret (never place it in frontend files).
4. Set DATA_FILE to a writable path if desired; otherwise data.json is stored beside server.js.
5. Run: npm start
6. Open http://localhost:3000
7. Operator page: http://localhost:3000/admin.html

OPERATOR PAYMENT REVIEW
1. Open /admin.html over HTTPS.
2. Enter the server's ADMIN_REVIEW_KEY.
3. Load pending submissions.
4. Compare transaction code, exact KSh 50 amount, date/time and sender details against the actual M-PESA record for 0738506826.
5. Only then click Approve. This activates the member account.

DEPLOYMENT
- A Render deployment blueprint is included in render.yaml.
- Create/sign into a Render account, choose New > Blueprint, and connect/upload this project through a Git repository. Review the paid Starter service and persistent disk costs shown by Render before creating it.
- Render generates the ADMIN_REVIEW_KEY environment variable. Copy it securely from the service environment settings; do not put it in this ZIP or share it in chat.
- After deployment, Render provides a public *.onrender.com URL. A custom domain can be connected later from the hosting dashboard.
- Test registration, login, a test payment submission, admin review, approval and data persistence before sharing the link publicly.

IMPORTANT LIMITATIONS / LAUNCH CHECKLIST
- This is manual Send Money only. It does not trigger STK Push, read SMS, or automatically verify payments.
- The website cannot be publicly reachable until deployed to hosting. This package does not create a live URL by itself.
- Render hosting and persistent disk are paid resources; check current pricing before deployment.
- Before accepting real customers, publish operator/business identity, support contact, privacy notice, refund/cancellation policy, and the specific content/benefits members receive. Do not imply earnings are guaranteed.
- The JSON-file database is suitable only for a small initial service; use a managed database and security review before scaling.

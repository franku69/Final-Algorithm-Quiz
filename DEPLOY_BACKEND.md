# Backend deployment notes

The GitHub Pages frontend is static. The backend manages rooms, identities, answer synchronization, timing, grading, reconnection, and score exports.

## Required private environment variables

- `PACKET_BANK_KEY` — the new key in the separate `Packet_Quest_Topic5_BANK_KEY_PRIVATE.txt` file; decrypts `backend/questions.enc` in memory.
- `PACKET_TEACHER_KEY` — keep the existing teacher login key when updating. For a new installation, choose a private value of at least 12 characters.

Never put either value in GitHub. Set `PACKET_BANK_KEY` in the backend host before or during the deployment of the updated `questions.enc`; the service will not start if code, ciphertext, and key do not match.

## Replacing an existing question bank

1. While the current backend is running, export any old scores or full records you need.
2. Delete all old rooms in the teacher dashboard. The backend refuses to load a different bank while old room rows remain in its database.
3. Deploy the updated repository and set `PACKET_BANK_KEY` from the private file. Expect a brief service interruption during the transition.
4. Confirm `/healthz` reports `live: true`, `questionCount: 40`, and bank ID `cs111-topic5-algorithms-40-final-v1`.
5. Reopen `/teacher/`, test a room, and confirm the 40-question quiz works before class.

## Other environment variables

- `PACKET_DATA_DIR` — persistent data directory. The included Render blueprint uses `/var/data`.
- `PACKET_ALLOW_PAGES_ORIGINS=1` — allows HTTPS GitHub Pages/Pages-compatible frontend origins.
- `PACKET_ALLOWED_ORIGINS` — optional comma-separated exact HTTPS origins if you want to restrict CORS more tightly.
- `PORT` — normally supplied by the hosting service.

## Start command

```text
python backend/server.py --host 0.0.0.0 --port $PORT
```

## Health check

```text
GET /healthz
```

A matching health response reports the 40-question Topic 5 bank and `live: true`.

## Data

The service stores active rooms, attempts, teacher sessions, submissions, and receipts in SQLite. For a cloud deployment, use persistent storage. Export scores after each section even when persistent storage is enabled.

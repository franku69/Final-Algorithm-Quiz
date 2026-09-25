# Packet Quest — CS111 Topic 5: Algorithms

This repository runs the live individual quiz for **CS111 Topic 5: Algorithms**.

## Student experience

The teacher shares one GitHub Pages room link. Each student opens it on a phone or computer, joins the room, answers 40 shuffled multiple-choice questions, and submits. The live server records and grades the attempt.

## Teacher dashboard

`/teacher/` shows students joining, connection state, saved-answer progress, current question position, provisional and final scores, and submission time. The answer key is available only after teacher authentication.

## Architecture

- `docs/` — public GitHub Pages quiz and teacher dashboard. It contains no answer key or teacher secret.
- `backend/` — live API server. The 40-question bank is stored as encrypted ciphertext in `questions.enc`.
- `render.yaml` — cloud deployment blueprint with persistent data storage.
- `.github/workflows/pages.yml` — validates the site files; GitHub Pages publishes `/docs` from the configured branch.

GitHub Pages is static, so the separate live backend handles rooms, student records, answer synchronization, timers, and grading.

## Quiz content

- 40 questions, one point each
- CS111 Topic 5 topics: algorithm basics, Polya problem solving, iteration, recursion, binary search, correctness, efficiency, verification, and flowcharts
- Six original question figures extracted directly from the supplied PDF, served locally as image assets
- Question and answer-choice order shuffled independently for each attempt

## Private setup

The encrypted bank requires `PACKET_BANK_KEY`. The separate private file `Packet_Quest_Topic5_BANK_KEY_PRIVATE.txt` contains that value. Keep it out of GitHub and configure it only in the backend hosting environment or the local private `.env` file. Keep your existing `PACKET_TEACHER_KEY` unchanged when updating the bank.

Before deploying this replacement bank, export any existing class records you need and delete the old rooms in the teacher dashboard. The backend prevents a bank change while rooms from the previous bank remain in its database. See `QUICK_START.md` and `DEPLOY_BACKEND.md`.

## Before class

Create a test room and complete one attempt from a phone on mobile data. Confirm the student appears in the teacher dashboard and the final score is recorded before starting a graded class.

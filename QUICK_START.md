# Quick start — update and run the Topic 5 quiz

This update replaces the old question bank with 40 CS111 Topic 5 Algorithms questions. Keep the bank key private and complete the room-record migration before the backend switches to the new bank.

## 1. Prepare the existing backend records

Before deploying the new bank, open the current teacher dashboard and export any old scores or full records you need. Then delete every old room in the dashboard. The backend blocks startup with a changed bank while old room records remain in its database.

## 2. Update the repository

Copy the contents of this archive into the existing GitHub repository, preserving its root structure, and commit/push the updated files. Do not add the separate `Packet_Quest_Topic5_BANK_KEY_PRIVATE.txt` file to GitHub.

The Pages workflow validates the app. GitHub Pages serves the static `docs/` directory from **Settings → Pages → Deploy from a branch → main → /docs**.

## 3. Update the backend secret

Set `PACKET_BANK_KEY` in your backend host to the value from the separate private key file. Keep your existing `PACKET_TEACHER_KEY` value unchanged. The backend may be briefly unavailable while the new code, encrypted bank, and bank key are deployed together.

For a new backend, also set a private `PACKET_TEACHER_KEY` of at least 12 characters. Never commit either key. Keep `PACKET_ALLOW_PAGES_ORIGINS=1`; use persistent storage for `PACKET_DATA_DIR`.

The Render blueprint in `render.yaml` mounts persistent storage at `/var/data`. Check your provider's pricing before using a paid resource.

## 4. Pair the teacher dashboard

1. Open the GitHub Pages `/teacher/` page.
2. Enter the live backend HTTPS URL if prompted, then choose **TEST & CONNECT BACKEND**.
3. Sign in using the existing private teacher key.
4. Create a test room and confirm the dashboard reports 40 questions.

The backend URL is remembered in your browser. It is public; the teacher key is private.

## 5. Test and run class

1. Copy the test room link and open it on a phone using mobile data.
2. Join, start the room, answer several questions, and confirm progress updates in the teacher dashboard.
3. Submit and confirm the final score appears.
4. Delete the test room.
5. Create the real room, share its one GitHub Pages link, and keep the backend online through the quiz.
6. Export the score CSV after class.

The student link automatically includes the room and backend address. Students do not need to install software or receive either private key.

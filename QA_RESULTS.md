# QA Results — CS111 Topic 5 Algorithms build

Build: `7.2.0-stable` · bank ID `cs111-topic5-algorithms-40-final-v1`

## Verification for this update

- The private key decrypts `backend/questions.enc` to a valid 40-question bank.
- The bank has 40 unique question IDs, four options per question, one valid answer ID per item, and all six referenced diagrams.
- Question and answer key IDs match the supplied PDF's 40-item key.
- Backend validation requires the new 40-question bank and rejects a mismatched count.
- The student and teacher dashboards use the 40-question total; teacher progress percentages scale to 40.
- All six original figures are extracted directly from pages 3–6 of the supplied PDF and mapped as local JPEG/PNG assets; the quiz has no custom replacement diagrams.
- The server startup no longer prints the private teacher key to its logs.
- JavaScript syntax and Python compile checks passed.
- Live local HTTP checks passed for health status, GitHub Pages CORS, and serving each supplied PDF figure as a local image.
- A local backend-store flow joined a student, saved and submitted a complete 40/40 attempt, and returned no answer key to the student payload.
- The repository archive contains encrypted question data only; the private decryption key is delivered separately.
- The desktop quiz navigator stays available while scrolling, and the student layout collapses cleanly for narrow screens.
- All six PDF-derived figures keep their original files, scale to the available question width, and can expand to their original resolution inside the quiz tab for close inspection.
- The teacher roster keeps its desktop table and becomes labeled student cards on tablet and phone widths, with no sideways scrolling.
- Student and teacher JavaScript syntax checks passed. Only the student/teacher UI files and their cache references changed; backend endpoints, encrypted questions, deployment files, and source figures are unchanged.

## Before using it for a graded class

A real phone test against the newly deployed GitHub Pages URL and backend is still required. The hosting provider's deployment, uptime, and persistent storage were not exercised by this package check.

## Update requirement

Export any old class records you need and delete all previous rooms before deploying the new bank. The backend deliberately blocks a bank change while previous room records remain in its database.

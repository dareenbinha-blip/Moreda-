# Fixing the Render `/static` startup error

**Cause:** Render checks for `/opt/render/project/src/static` because your Python
app mounts it, but the GitHub deployment didn't contain that directory.

## Quickest repair in GitHub

1. Open your private `moreda-erp` GitHub repository.
2. Confirm `main.py` is at the top level (or the selected Render Root Directory).
3. Confirm a `static` folder beside `main.py` contains `index.html`, `styles.css`, `app.js`.
4. If not, extract the fixed download on your PC. Upload all three into a GitHub
   `static/` folder and commit. GitHub web UI: **Add file → Upload files** (you
   can drag the folder or upload files while viewing the `static` directory).
5. Alternative: update `main.py` and upload `frontend_bundle.zip` into the **same
   directory** as `main.py`. This version restores the frontend automatically.
6. On Render, open the `moreda-erp` Web Service → **Manual Deploy → Deploy latest commit**.
7. Once Live, open the service URL. Verify `/healthz` and the sign-in page.

**Don't upload the ZIP as the only file in GitHub.** Extract it first.
Do not delete your PostgreSQL database or rotate the admin account to fix a
missing static folder. The problem concerns only deployable frontend assets.

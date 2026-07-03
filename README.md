# Holistic Fire Safety — website

Static site: no build step, no dependencies. Every page is plain HTML; shared styles in css/style.css.

## Deploy (first preview)
1. Go to https://app.netlify.com/drop
2. Drag this whole folder in — the site goes live on a temporary URL in seconds.

## Deploy (proper setup, for the chat-to-update workflow)
1. Create a GitHub repository and upload these files.
2. In Netlify: "Add new site" → "Import an existing project" → pick the repo.
3. Build command: none. Publish directory: / (root).
4. Connect Claude (Claude Code or the GitHub integration) to the repo — from then on,
   updates happen by chatting: "add a case study", "change the phone number", etc.

## Structure
- index.html — homepage
- services/ — one page per service (7) + index
- case-studies/ — one page per project (6) + index
- about.html, testimonials.html, contact.html
- The contact form uses Netlify Forms (works automatically once deployed on Netlify).

## To do before going live
- Confirm phone / email / address on contact.html (marked [TO CONFIRM])
- Add real photography and the logo file
- Point holisticfire.com at Netlify (10-minute DNS change — keep Squarespace until then)

# Arboreal Sales Training Simulator

AI-powered practice tool for leasing agents. Agents chat with realistic AI prospects who have specific needs, objections, and property concerns. After the conversation, they get a coaching scorecard evaluated against Arboreal's training frameworks (LAER, Feel-Felt-Found, Boomerang, Teach-Tailor-Take Control, S.E.E., L.E.A.D.).

## What's Inside

- **15 prospect profiles** with unique jobs, budgets, priorities, cooking habits, pets, and apartment history
- **9 real Arboreal properties** with accurate details (sqft, rent, parking, kitchen, objections, strengths)
- **4 scenario types**: Needs Discovery, Objection Handling, Property Presentation, Closing Techniques
- **AI coaching** that scores against specific frameworks with quotes and alternative phrasing
- Every session is unique — random prospect + random property = 135+ combinations

## Deploy to Render (Free)

### Step 1: Create a Render account
Go to **render.com** and sign up (free).

### Step 2: Create a new Web Service
- Click **New** → **Web Service**
- Choose **Upload a project** (or connect GitHub if you've pushed this to a repo)
- Upload this folder

### Step 3: Configure the service
- **Name**: `arboreal-training` (or whatever you want)
- **Runtime**: Python
- **Build Command**: `pip install -r requirements.txt`
- **Start Command**: `gunicorn app:app`

### Step 4: Add your API key
- Go to **Environment** tab
- Add environment variable:
  - **Key**: `ANTHROPIC_API_KEY`
  - **Value**: your API key from console.anthropic.com

### Step 5: Deploy
Click **Deploy**. In 2-3 minutes you'll get a URL like `https://arboreal-training.onrender.com` that your team can access.

## Run Locally (Alternative)

```bash
# Install dependencies
pip install -r requirements.txt

# Set your API key
export ANTHROPIC_API_KEY="sk-ant-..."

# Run the app
python app.py

# Open http://localhost:5000
```

## Cost

Each practice conversation costs approximately $0.01-0.05 in API usage depending on length. The coaching analysis adds about $0.02-0.04. Your team could run hundreds of sessions for a few dollars.

## Files

- `app.py` — Flask server with all property data, prospect profiles, and API logic
- `templates/index.html` — Full UI (single file, no build step needed)
- `requirements.txt` — Python dependencies
- `Procfile` — Tells Render how to start the app

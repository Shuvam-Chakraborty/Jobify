# Jobify 🚀

A full-stack job portal application built with Streamlit that connects job seekers with recruiters — featuring real-time job search, resume management, and an end-to-end hiring workflow.

---

## Features

### For Job Seekers
- 🔍 **Smart Job Search** — Search local listings and pull thousands of external jobs from LinkedIn, Indeed, and Glassdoor via the JSearch API
- 🧠 **Skill Match Scoring** — Jobs are ranked based on how well your skills match the requirements
- 📄 **Resume Upload & Tracking** — Upload PDF/DOC resumes and track your application status (Pending / Accepted / Rejected)
- 👤 **Profile Builder** — Add your skills, experience level, and links (GitHub, LinkedIn)

### For Recruiters
- 📝 **Job Posting** — Create listings with categories, required skills, and job details
- 📊 **Live Dashboard** — Monitor total jobs, active listings, view counts, and applications in real time
- 📥 **Applicant Management** — View applicant profiles, download resumes, and update hiring status

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Streamlit + Custom CSS |
| Database | MongoDB (Atlas or Local) |
| File Storage | MongoDB GridFS |
| Authentication | bcrypt |
| External Jobs | JSearch API (RapidAPI) |
| Language | Python 3.8+ |

---

## Project Structure

```
jobify/
├── auth/
│   ├── __init__.py
│   └── auth.py              # Signup, login, bcrypt password hashing
├── database/
│   ├── __init__.py
│   ├── connection.py        # MongoDB connection setup
│   └── models.py            # Collection schemas and queries
├── pages/
│   ├── __init__.py
│   ├── profile.py           # Job seeker profile page
│   ├── recruiter_dashboard.py
│   └── user_dashboard.py
├── utils/
│   ├── __init__.py
│   ├── file_handler.py      # Resume upload/download via GridFS
│   ├── job_api.py           # JSearch RapidAPI integration
│   └── search_helper.py     # Skill matching, search term generation
├── app.py                   # Entry point
├── config.py                # Environment variable handling
├── requirements.txt
└── .env.example
```

---

## Getting Started

### Prerequisites

- Python 3.8+
- A [MongoDB](https://www.mongodb.com/atlas) instance (local or Atlas)
- A [RapidAPI](https://rapidapi.com/letscrape-6bRBa3QguO5/api/jsearch) key for JSearch

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/jobify.git
   cd jobify
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```
   Then edit `.env` with your credentials:
   ```env
   MONGODB_URI=mongodb+srv://<user>:<password>@cluster.mongodb.net/jobify
   RAPIDAPI_KEY=your_rapidapi_key_here
   ```

4. **Run the app**
   ```bash
   streamlit run app.py
   ```

---

## Configuration

| Variable | Description |
|---|---|
| `MONGODB_URI` | Connection string for your MongoDB instance |
| `RAPIDAPI_KEY` | API key for JSearch (external job listings) |

> **Cloud Deployment:** `config.py` checks for Streamlit Secrets first, then falls back to `.env`. For Streamlit Cloud, set your secrets under **App Settings → Secrets**.

---

## Constraints & Limits

- **Resume file size:** Max 5 MB
- **Allowed file types:** `.pdf`, `.doc`, `.docx`
- **Supported job categories:** Software Engineering, AI/ML, Design, Data Science, and more

---

## How It Works

```
User logs in
    │
    ├── Job Seeker
    │       ├── Build profile (skills, experience)
    │       ├── Search jobs → local DB + JSearch API
    │       ├── Results ranked by Skill Match Score
    │       └── Apply → upload resume → track status
    │
    └── Recruiter
            ├── Post job listings
            ├── View dashboard metrics
            └── Manage applicants → download resumes → Accept / Reject
```

---

## License

This project is open source. Feel free to fork, extend, and build on it.

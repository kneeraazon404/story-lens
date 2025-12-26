# StoryLens

**Turn your favorite memories into timeless narratives.**

StoryLens is a privacy-first, AI-powered application that transforms user-uploaded photos into personalized narrative stories. It uses **OpenAI's GPT-4o Vision** API to analyze images and generate empathetic, context-aware stories based on user-provided metadata.

## Key Features

* **Privacy First**: No long-term storage of user images. Photos are processed and strictly deleted immediately after story generation.
* **Vision AI**: Leveraging GPT-4o Vision for deep understanding of visual context, emotions, and atmosphere.
* **Lean MVP**: A single, streamlined web flow—upload, contextualize, and read.
* **Fast Response**: Optimized for low latency using the latest Chat Completions API.

## Project Structure

```bash
story-lens/
├── app/
│   ├── main.py              # Application entry point (Flask)
│   ├── services/
│   │   └── vision_service.py # Core Vision AI logic
│   ├── utils/
│   │   └── file_handler.py   # Secure file handling & cleanup
│   └── templates/
│       └── index.html        # Frontend MVP interface
├── redundants/               # Archived legacy code
├── requirements.txt          # Python dependencies
├── run.py                    # Dev server runner
├── wsgi.py                   # Production entry point
├── Dockerfile                # Container definition
└── README.md                 # Documentation
```

## Setup & Installation

1. **Clone the repository**:

    ```bash
    git clone <your-repo-url>
    cd story-lens
    ```

2. **Create a virtual environment**:

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3. **Install dependencies**:

    ```bash
    pip install -r requirements.txt
    ```

4. **Configure Environment**:
    Create a `.env` file in the root directory:

    ```bash
    cp .env.example .env
    ```

    Populate it with your keys:

    ```env
    OPENAI_API_KEY=your_openai_api_key
    ```

5. **Run Development Server**:

    ```bash
    python run.py
    ```

    Access the app at `http://127.0.0.1:5000`.

## Deployment

### Option A: WSGI Server (Gunicorn)

For production on a standard server:

1. Install Gunicorn (included in requirements):

    ```bash
    pip install gunicorn
    ```

2. Run the application:

    ```bash
    gunicorn --bind 0.0.0.0:8000 wsgi:app
    ```

    Or use the config in `wsgi.py`.

### Option B: Docker

1. Build the image:

    ```bash
    docker build -t story-lens .
    ```

2. Run the container:

    ```bash
    docker run -p 8000:8000 --env-file .env story-lens
    ```

## Tech Stack

* **Backend**: Python, Flask
* **AI**: OpenAI GPT-4o (Vision + Chat Completions)
* **Frontend**: HTML5, CSS3 (Privacy-First UI)
* **Infrastructure**: Stateless, Ephemeral Storage

---
*Note: Legacy services from previous iterations (Tripetto integration, MidJourney generation) have been archived in the `redundants/` directory.*

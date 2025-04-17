# Brand Compliance Auditor

This project is a Brand Compliance Auditor that ensures adherence to brand guidelines for both text and visual assets. It uses the OpenAI API, a Python/FastAPI backend, and a React.js frontend.

## Features

- Text compliance checks against brand guidelines
- Logo detection and positioning validation
- Color palette compliance
- Asynchronous task processing with Celery
- User authentication and role-based access control

## Project Structure

```
backend/
├── app.py               # FastAPI entrypoint
├── compliance/          # core logic modules
│   ├── text_checker.py
│   ├── image_checker.py
│   ├── models.py        # Pydantic schemas
├── tasks/               # Celery jobs
├── db/                  # database models (SQLAlchemy)
├── settings.py          # env + OpenAI keys
└── requirements.txt
```

## Setup

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/brand-compliance-auditor.git
   ```

2. Navigate to the backend directory:
   ```
   cd backend
   ```

3. Install the required packages:
   ```
   pip install -r requirements.txt
   ```

4. Set up the environment variables in a `.env` file:
   ```
   OPENAI_API_KEY=your_openai_api_key
   DATABASE_URL=your_database_url
   REDIS_URL=your_redis_url
   ```

5. Run
### Python Version

Ensure you have Python 3.8 or higher installed. You can check your Python version with the following command:

```bash
python --version
```
 the FastAPI application:
 
#### Server Configuration

The FastAPI application runs on Uvicorn, an ASGI server. You can start the server with the following command:

```bash
uvicorn app:app --reload
```

This command starts the server in development mode with auto-reload enabled. For production deployment, you can use a more robust server configuration with Gunicorn and Uvicorn workers:

```bash
gunicorn -k uvicorn.workers.UvicornWorker app:app
```

Adjust the number of workers and other parameters as needed for your production environment.

#### Celery and Redis Configuration

To process asynchronous tasks, you'll need to run a Celery worker and configure Redis as the message broker. Start the Celery worker with the following command:

```bash
celery -A tasks worker --loglevel=info
```

Ensure Redis is running and accessible at the URL specified in your `.env` file. You can start Redis using Docker:

```bash
docker run -d -p 6379:6379 redis
```

   ```
   uvicorn app:app --reload
   ```

## Usage

- Upload text and visual assets for compliance checks.
- View compliance reports with detailed explanations.
- Manage brand guidelines and rules.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

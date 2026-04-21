# AI Powered Quiz Application

Full-stack quiz application with a React frontend and Spring Boot backend.

## Features

- Student login and registration
- Subject-based quiz browsing
- Quiz attempt flow with score, timer, answer review, and feedback
- Performance dashboard with average score, best score, and quiz history
- AI Coach tab that explains how personalized quiz generation can work
- Admin quiz creation with subject selection
- Backend API with H2 database and Flyway migrations

## Project Structure

- `quiz-app/` - React frontend
- `quiz-server/` - Spring Boot backend

## Run Frontend

```bash
cd quiz-app
npm install
npm start
```

Frontend runs at `http://localhost:3000`.

## Run Backend

```bash
cd quiz-server
mvn spring-boot:run
```

Backend runs at `http://localhost:8080`.

## AI Setup

Copy `.env.example` to `.env` and add your OpenAI API key:

```env
OPENAI_API_KEY=your_api_key_here
OPENAI_MODEL=gpt-4.1-mini
```

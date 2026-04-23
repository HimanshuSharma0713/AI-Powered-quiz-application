# AI-Powered Quiz Application for Subject-Based Learning and Performance Feedback

**Author:** Your Name  
**Department:** Your Department / Institution  
**Course:** CA2 Project Submission  
**Date:** April 2026

## Abstract

Digital learning platforms are increasingly used to support self-paced assessment, instant feedback, and personalized academic improvement. This paper presents the design and implementation of an AI-powered quiz application that allows students to attempt subject-based quizzes, review performance, and receive feedback after completion. The system is implemented as a full-stack web application using React for the frontend and Spring Boot for the backend. It supports student authentication, quiz selection by subject, quiz attempt tracking, score calculation, performance analytics, and an AI Coach interface that explains how artificial intelligence can help generate future quizzes according to student performance and subject preference. The backend stores users, quizzes, questions, and quiz results in an H2 database managed through Flyway migrations. The application also includes a server-side AI feedback endpoint designed to integrate with an OpenAI API key when available, while still providing fallback feedback when an API key is not configured. The project demonstrates how web technologies and AI-assisted learning concepts can be combined to build a practical educational tool for continuous assessment.

**Keywords:** AI-assisted learning, quiz application, React, Spring Boot, performance analytics, subject-based learning, educational technology.

## I. Introduction

Online assessment systems are useful for students because they provide immediate practice and feedback. Traditional quiz systems usually show only a final score, which is helpful but limited. Students often need additional guidance, such as which subjects to revise, how their performance changes over time, and what type of quiz they should attempt next.

The project described in this paper addresses this need by implementing a web-based quiz application with subject selection, performance tracking, and AI-ready feedback features. The application allows students to select quizzes by subject, attempt questions, review answers, and view a performance tab containing average score, best score, strong performances, and attempt history. It also includes an AI Coach tab that explains how AI can later generate personalized quizzes based on the student's selected subject and past performance.

The main objective of the project is to create a working educational platform that combines implementation, documentation, version control, and professional presentation. The system is designed for CA2 evaluation requirements, including project implementation, GitHub repository maintenance, LinkedIn portfolio demonstration, and an IEEE-style project report.

## II. Problem Statement

Many students use quizzes for revision, but basic quiz applications often lack personalization. A student may complete several quizzes but still not know which subject requires more practice or how performance has changed over time. Additionally, creating new quizzes manually can be time-consuming for instructors and administrators.

The problem can be summarized as follows:

- Students need a simple platform to attempt quizzes by subject.
- Students need performance tracking after each quiz attempt.
- Administrators need a way to create quizzes with subject categorization.
- The system should be ready for AI-assisted quiz generation and feedback.
- The project should be easy to document, run locally, and publish on GitHub.

## III. Objectives

The objectives of this project are:

- To implement a full-stack quiz platform using React and Spring Boot.
- To allow users to register, log in, and attempt quizzes.
- To provide subject-based quiz filtering for students.
- To store quiz attempts and update performance metrics.
- To provide a Performance tab for score history and analytics.
- To create an AI Coach tab that explains personalized AI quiz generation.
- To add a backend AI feedback endpoint that can work with an API key in the future.
- To prepare the project for GitHub submission with README and documentation.

## IV. Literature and Technology Background

Web-based learning systems are commonly built using a separation between client-side user interfaces and backend services. React is widely used for building interactive frontend applications because it supports component-based UI development and state management. Spring Boot is frequently used for backend APIs because it simplifies Java web application setup and provides support for REST controllers, dependency injection, and database integration.

For data persistence, lightweight databases such as H2 are useful during development because they require minimal setup. Flyway is used to manage database schema changes through migrations, making the project more maintainable. AI services can be connected through backend APIs so that sensitive API keys are not exposed in the browser.

This project combines these technologies to create a practical educational application. Unlike a simple static quiz page, the system stores results, calculates performance, supports subject filtering, and prepares the structure for AI-assisted quiz creation.

## V. System Architecture

The application follows a client-server architecture.

### A. Frontend Layer

The frontend is built using React. It handles:

- Login and registration screens.
- Student dashboard.
- Subject-based quiz filtering.
- Quiz attempt flow.
- Result screen and answer review.
- Performance tab.
- AI Coach tab.
- Admin quiz creation interface.

The frontend communicates with the backend using HTTP requests.

### B. Backend Layer

The backend is built using Spring Boot. It provides REST APIs for:

- Authentication.
- Quiz listing and quiz details.
- Quiz creation and management.
- Saving quiz results.
- Fetching user performance history.
- AI feedback generation.

### C. Database Layer

The system uses an H2 database. Flyway migrations create and update tables such as:

- `users`
- `quizzes`
- `questions`
- `quiz_results`

Additional migrations add subject support and seed more quizzes.

### D. AI Layer

The AI layer is implemented as a backend service. It is designed to call the OpenAI Responses API when an API key is configured. If no key is present, the service returns fallback feedback. This design keeps secrets on the server side and prevents exposing API keys in frontend code.

## VI. Methodology

The project was developed using an incremental approach:

1. Basic React quiz interface was created.
2. Spring Boot backend was added for persistent quiz data.
3. Authentication and database tables were implemented.
4. Quiz results were stored in the backend.
5. Performance tracking was added to the dashboard.
6. Subject selection and filtering were added.
7. AI feedback and AI Coach features were integrated.
8. GitHub-safe documentation files were prepared.

This approach allowed the project to grow from a basic quiz interface into a more complete educational application.

## VII. Implementation Details

### A. Authentication

The authentication flow allows users to log in or register. The backend verifies username and password using the `users` table. After successful login, the frontend stores the current user in state and local storage.

### B. Quiz Management

Quizzes are stored in the `quizzes` table. Each quiz includes:

- title
- description
- subject
- creator
- active status

Questions are stored separately in the `questions` table and linked to quizzes using `quiz_id`.

### C. Subject Selection

Subject selection was added so students can filter quizzes based on learning area. The dashboard includes a subject dropdown. Administrators can assign a subject when creating a quiz.

Examples of subjects include:

- General Knowledge
- Mathematics
- Science
- Geography
- Computer Science
- History
- Language Arts

### D. Quiz Attempt Flow

When a student starts a quiz, the frontend fetches full quiz details from the backend. The student answers questions one by one. After the final question, the application calculates the score, saves the attempt, generates feedback, and displays the result screen.

### E. Performance Tab

The Performance tab shows:

- average score
- best score
- number of strong performances
- attempts recorded
- quiz history

The frontend uses a dedicated `quizHistory` state so that performance metrics update immediately after each attempt. This improves user experience because students can see updated progress without needing to reload manually.

### F. AI Coach Tab

The AI Coach tab works even without an API key. It explains how AI can help create quizzes based on:

- selected subject
- average score
- previous quiz attempts
- weak areas

The tab acts as a preview of future AI-based personalization. When an API key is added, this concept can be extended to generate real quizzes automatically.

### G. AI Feedback Endpoint

The backend includes an AI feedback endpoint. It receives quiz results and answer details from the frontend. If an API key is configured, the backend can request AI-generated feedback. If no key is available, the system returns a fallback message.

This design has two advantages:

- The frontend does not expose API keys.
- The application still works without paid AI access.

## VIII. Testing and Results

The application was tested locally using:

- React development server on port `3000`.
- Spring Boot backend on port `8080`.
- H2 database for persistence.
- API checks for quizzes and results.

The following functional outcomes were verified:

- Users can log in.
- Quizzes can be displayed from the backend.
- Students can select quizzes by subject.
- Quiz attempts can be completed.
- Scores are calculated correctly.
- Performance data updates after quiz completion.
- Additional quizzes are loaded through migrations.
- AI feedback endpoint returns a response even without an API key.

## IX. GitHub Repository and Version Control

For CA2 submission, the project repository should include:

- Complete source code.
- Root README file.
- Frontend and backend folders.
- `.gitignore` file.
- `.env.example` file.
- Basic setup instructions.
- Commit history showing incremental development.

The repository should not include:

- real `.env` file
- `node_modules`
- `.tools`
- database files
- log files
- build outputs

The `.gitignore` file was prepared to exclude these generated or sensitive files.

## X. LinkedIn Portfolio Demonstration

For LinkedIn presentation, the project can be showcased as a student-built full-stack educational platform. The demonstration should include:

- short video or screenshots
- project objective
- technologies used
- features implemented
- learning outcomes
- GitHub repository link

Suggested skills to mention:

- React
- Spring Boot
- REST API
- H2 Database
- Flyway
- AI integration
- Full-stack development
- Educational technology

## XI. Limitations

The current version has some limitations:

- Passwords are stored in a simple format and should be hashed in a production system.
- AI-generated quiz creation is represented in the AI Coach tab but not fully automated yet.
- The frontend is currently implemented mainly in one large React file.
- The database is suitable for local development but not production deployment.
- Advanced analytics such as charts and subject-wise progress graphs can be added later.

## XII. Future Scope

Future improvements may include:

- Real AI-generated quizzes based on weak subjects.
- Subject-wise performance charts.
- Difficulty levels for quizzes.
- Teacher dashboard.
- Secure password hashing.
- Role-based access control.
- Deployment on cloud platforms.
- Mobile-responsive improvements.
- Exportable performance reports.

## XIII. Conclusion

This project successfully implements a full-stack AI-ready quiz application for subject-based learning and performance tracking. The system allows students to attempt quizzes, view results, track performance, and understand how AI can support personalized quiz creation. The use of React, Spring Boot, H2, and Flyway provides a practical and maintainable architecture for academic demonstration. The project also supports CA2 requirements by including implementation, GitHub-ready documentation, and LinkedIn portfolio material. Overall, the application demonstrates how modern web development and AI-assisted learning concepts can be combined to support student revision and continuous assessment.

## References

[1] React Documentation, "React: The library for web and native user interfaces."  
[2] Spring, "Spring Boot Reference Documentation."  
[3] H2 Database Engine, "H2 Database Documentation."  
[4] Flyway, "Database Migrations Made Easy."  
[5] OpenAI, "OpenAI API Documentation."  
[6] IEEE, "IEEE Conference Template Guidelines."

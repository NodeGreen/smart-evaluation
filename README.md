# Smart Evaluation

[![Master's Thesis](https://img.shields.io/badge/Project-Master%27s%20Thesis%202023-blue)](https://github.com/NodeGreen/smart-evaluation)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Status: Archived](https://img.shields.io/badge/Status-Archived-inactive)]()

A web-based platform for creating and delivering **skill-oriented admission tests** with real coding and SQL questions. Built as a Master's thesis prototype, this system automatically evaluates student responses using innovative evaluation algorithms.

## Overview

Smart Evaluation was designed to solve a specific problem: traditional admission tests don't assess practical skills effectively. This prototype demonstrates a solution where instructors can create tests with actual code questions (like LeetCode) and SQL queries with an internal database validation system — all evaluated automatically.

**Key Innovation**: The system evaluates not just multiple-choice answers, but real working code and SQL queries against test cases and database snapshots.

## Architecture

The application consists of **two independent web frontends** and **two dedicated backends**:

| Component | Purpose | Users |
|-----------|---------|-------|
| **Candidate App** | Take tests with unique access codes | Students/Candidates |
| **Administration App** | Create and manage tests, questions, topics, courses | Instructors/Staff |
| **Server Candidate** | Evaluate code and SQL submissions in real-time | Backend service |
| **Server Administration** | Manage users, courses, tests, questions | Backend service |

## Core Features

### 🎯 Skill-Oriented Questions

Three question types with intelligent evaluation:

1. **Quiz** - Traditional multiple-choice with partial credit system
2. **Code** - Write real C++ code evaluated against test cases
   - Automatically compiles submissions
   - Runs against predefined test suites
   - Provides partial credit based on passing tests
   - Detects compilation errors and assertion failures

3. **SQL** - Write database queries evaluated on snapshots
   - Internal JavaScript-based database with schema snapshots
   - Tests query correctness by comparing results
   - Supports configuration for:
     - Column relevance checking
     - Row order importance
     - Result set multiplicity validation

### 👥 Dual-Role System

**Instructor Dashboard**:
- Create and organize questions by topics
- Build tests from question pools
- Configure evaluation criteria (e.g., "order matters in SQL results")
- Manage courses and user roles

**Candidate Interface**:
- Access tests with one-time codes
- Submit code in real-time IDE
- Write and execute SQL queries
- Receive immediate feedback on evaluation

### 🔐 Role-Based Access Control

Support for multiple user roles: Administrator, Evaluator, Staff, with granular permission management

## Technologies

| Layer | Technology |
|-------|-----------|
| **Frontend** | Vue.js 2.x, Nuxt.js |
| **Backend** | Node.js, Express.js |
| **Database** | MongoDB |
| **UI Components** | Vuetify |
| **Code Evaluation** | C++ compiler integration |
| **SQL Evaluation** | JavaScript-based DB engine |

## Project Status

⚠️ **This is a 2023 thesis prototype** — preserved as a historical archive and proof of concept. The codebase is functional but hasn't been maintained since completion.

### Known State

✅ **What Works**:
- Core architecture and separation of concerns
- Automatic code evaluation system with test cases
- SQL query validation with database snapshots
- Multi-user role system
- Successfully demonstrated during thesis presentation

🔧 **What Needs Attention**:
- Dependencies may be outdated
- Code would benefit from refactoring and modernization
- Probably contains "1000 of bugs"
- Requires dependency updates before production use

## How It Works

### Test Creation Flow

1. **Instructor** logs into Administration app
2. **Creates questions** (Quiz, Code, or SQL type)
3. **Configures evaluation criteria**:
   - For Code: provides reference solution + test cases
   - For SQL: provides reference query + database snapshots
4. **Builds tests** from question pool
5. **Generates unique candidate codes**

### Test Taking Flow

1. **Candidate** visits application with unique code
2. **Loads test** and sees all questions
3. **For Code questions**:
   - Writes C++ code in editor
   - Submits for evaluation
   - Receives pass/fail on each test case
4. **For SQL questions**:
   - Writes SQL query
   - System executes against snapshot database
   - Compares results with reference query
5. **Receives final score** after completion

### Evaluation System

#### Code Evaluation (`questionEvaluator.js`)

```javascript
// Compiles code + test harness
// Executes compiled binary
// Parses output for:
//   - Compilation errors
//   - Assertion failures
//   - Successful test passes
// Awards partial credit per passing test
```

#### SQL Evaluation

```javascript
// Executes candidate query on snapshot DB
// Executes reference query on same snapshot
// Compares result sets with configurable rules:
//   - Column order relevance
//   - Row order relevance
//   - Duplicate handling
// Awards full/partial/zero credit
```

## Why This Project Matters

This thesis addressed a real gap in skill assessment. Most online test platforms use multiple-choice formats, which don't validate practical abilities. Smart Evaluation demonstrates that you *can*:

✅ Safely evaluate student code submissions in a web environment  
✅ Build a practical SQL validator with snapshot databases  
✅ Create a scalable multi-user platform for skill assessment  
✅ Provide immediate feedback on technical skills

## Future Improvements (Maybe)

- [ ] Code cleanup
- [ ] Update dependencies to modern versions
- [ ] Add support for more programming languages

## Contributing

This is an archived thesis project, but if you're interested in the concepts:

1. Feel free to fork and experiment
2. Build upon the ideas for your own projects
3. Contribute improvements via pull requests
4. Use as a reference for similar systems

Please update dependencies before any production use.

## License

MIT License © 2023

## About This Project

I created Smart Evaluation as my Master's thesis project in 2023. It represents months of research, architecture planning, and development to solve a real problem: how to automatically evaluate practical skills in admission tests.

While the code is archived and hasn't been touched since completion, the architectural patterns and evaluation algorithms demonstrate practical solutions worth preserving as reference material for similar assessment systems.

---

**Note**: This repository is maintained as a historical record of my thesis work. The codebase is functional but rusty — if you're interested in reviving it or building upon these concepts, feel free to fork and experiment. It's a great learning resource and starting point.

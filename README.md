# LMC Project 2

**Topic -** Dev Guide For “Rita” Project - <https://github.com/Andrew920528/rita-cfc-2024>

**Intro/Context** - This project contains a set of documents to serve as guidelines working on the project "Rita." Edison and I work on the project “Rita” in a team of 5. Rita is a full stack application that uses React.js for frontend, Flask backend, and AWS for our database. As the project grows and the tasks of each teammate become more and more involved, we need a dev guide to ensure the team is following consistent and best practices for the scalability of the project.

**Medium** - Google doc and Markdown

**Goal** - A collection of documents that help a teammate to be on track with all parts of the project.
<img width="841" alt="system architecture" src="https://github.com/user-attachments/assets/4cf864e5-c108-41bc-b057-aa7ebedf5acc" />

The above is the system architecture of our current app. This guide will start from mentioning the team's convention, to cover the setup and testing procedure of the three main aspect of the app - frontend, backend, and the database. After reading the three documents, the reader should be able to start making changes to the code base.

**Audience** - Teammate working on the project (programmer with >1 of dev experience), or new teammate that wanted to contribute to the project. The instructor of this course is our secondary audience.

**Prereqs/Requirements** -
You are expected to have basic knowledge of the following tech stacks
- Management
  - [github](https://github.com/), [git](https://git-scm.com/), [Markdown](https://www.markdownguide.org/)
- Frontend
  - [npm](https://www.npmjs.com/), [Typescript/Tsx](https://www.typescriptlang.org/), [React](https://react.dev/)
- Backend
  - [conda](https://anaconda.org/anaconda/conda), [Python](https://www.python.org/), [Flask](https://flask.palletsprojects.com/en/stable/), [Amazon RDS](https://aws.amazon.com/rds/?p=ft\&c=db\&z=3), [LangChain](https://www.langchain.com/)

**Safety Information** - When following the guidelines, be aware that sensitive information such as API keys and passwords should not be shared to others. It is recommended to use `.env` file for handling such info. Also check for safety notices (deprecation warning, etc.) when downloading any packages. 

**Scope** -
- Doc 0 \[README.md]: Project 2 context, goal, and other required information for secondary audiences
- Doc 1 \[Project_setup.md]: Project set-up Instructions
  - Prerequisites
  - How to start the backend (install packages, setup conda env, run server)
  - How to start the frontend
- Doc 2 \[Best_practice.md]: Best practices
  - git usage
    - branching
    - pr & commit
    - merging
  - naming conventions
- Doc 3 \[Testing.md]: Testing
  - Reporting issues
  - Frontend
    - using inspector
    - using react dev tool
    - Test frontend independently
  - Backend
    - Rita backend guide
    - Linking AWS db and open it up in mySQL
    - Where to find our API documentation
  - AI
    - Using notebooks for modularized testing
    - Where to observe logs, and how to toggle ‘verbose’ flag
    - Using flags for frontend-less testing

**References:**
- _Conda | anaconda.org_. (n.d.). <https://anaconda.org/anaconda/conda>
- _Git_. (n.d.). <https://git-scm.com/>
- _GitHub · Build and ship software on a single, collaborative platform_. (2025). GitHub. https\://github.com/
- _JavaScript with syntax for types._ (n.d.). https\://www\.typescriptlang.org/
- _LangChain_. (n.d.). https\://www\.langchain.com/
- _Managed SQL Database - Amazon Relational Database Service (RDS) - AWS_. (n.d.). Amazon Web Services, Inc. https\://aws.amazon.com/rds/?p=ft\&c=db\&z=3
- _Markdown Guide_. (n.d.). https\://www\.markdownguide.org/
- _npm | Home_. (n.d.). https\://www\.npmjs.com/
- _React_. (n.d.). https\://react.dev/
- _Welcome to Flask — Flask Documentation (3.1.x)_. (n.d.). https\://flask.palletsprojects.com/en/stable/
- _Welcome to Python.org_. (2025, February 18). Python.org. https\://www\.python.org/

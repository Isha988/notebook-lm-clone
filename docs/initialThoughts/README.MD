This docs has been written by the author of the project to share the initial thoughts and plans for the MVP and future scopes of the project.
The whole folder is hand written by the author and should not be modified by any AI agent.
The real implementation can be different from the things written in this folder because it's initial ideas, in course of the development decision will be made based on goals, tech and best solution possible to solve an objective.

## Initial Features Planned
Check [MVP MD file](./mvp.md) to see the features planned for the first cut of the project.

## Base Tech and Architecture
1. For this project We are going ahead with a monorepo setup for frontend and backend, this monorepo has be managed by pnpm workspaces.
2. Frontend is a Next.js project written in TS, which uses scadcn for UI, and planning to use React Query and Zustand for server and client global state management respectively, choosing zustand becuase I don't have much to store in global state so choosing a light weight library is better.
3. Backend is a Express sever written in TS, it will use zod for request data validation. It will support Rest API and SSE based on the nature of the feature. 
4. Database: Using MongoDb for the notebooks, users, sources and chat data, for the vectors gonna used QDrant DB. Choosing QDrant DB over MongoDB vector search bcoz QDrant is a vector first DB and it will also give an opportunity to use Docker in my application.
5.  RAG: For RAG gonna used LangChain for things like source data parsing handling, VectorDB Operations, OpenAI Embedding creations and OpenAI chats. And a queue in the ingestion steps of source for async processing.
6.  I am not using any AI UI library on frontend because I wanna try handling SSE on my own once then In next project can try AI libraries on FE on too, on BE I already have little taste of it. 
7.  Authentication: For auth gonna used google login and session based cookies. 

## Screen wise architecture plan:
1. [Login Screen](./loginScreen.md): It comes up when user isn't logged in and shows google login option.
2. [Dashboard Screen](./dashboardScreen.md): It shows the list of notebooks user has and in case no notebooks a cta to create one.  
3. [Notebook Screen](./notebookScreen.md): It is the detailed view of notebook with sources, chat interface and chat history.    
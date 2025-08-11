# 📝 Postmortem Report: Local Development Issue

**Author:** Raj Singh  
**Role:** DevOps Engineer  
**Date:** 2025-08-07  

---

## 🚨 Incident Summary
While running the app locally, I followed the documentation and executed `flask run` in the `/backend` folder.  
An error occurred due to an issue with the `JWS_SECRET_KEY`.

---

## 🎯 Impact
- The frontend could not connect to the backend.
- Logging in failed with an "incorrect password" error, preventing access to the application.

---

## 🔍 Root Cause
- The `JWS_SECRET_KEY` used was incorrect. I had copied the example key from the documentation instead of setting a unique value.

---

## 🛠️ Resolution
- Created a `.env` file and configured a valid `JWS_SECRET_KEY`.

---

## ✅ Result
- The frontend successfully connected to the backend.
- Login functionality was restored and working as expected.

---

# 📝 Postmortem Report: Frontend Containerization Issue

**Author:** Raj Singh  
**Role:** DevOps Engineer  
**Date:** 2025-08-07  

---

## 🚨 Incident Summary
While building the Docker image for the React frontend, a build error occurred: `/app/build not found`.  
This happened because of a misunderstanding of Docker multi-stage builds. The React app creates a `/dist` folder after running `npm run build`, but the Dockerfile was set to copy `/app/build` instead of `/app/dist`.

---

## 🎯 Impact
- 🚫 The build failed because the second stage of the Dockerfile could not find the `/app/build` folder.
- 🛑 The frontend image was not created, blocking deployment.

---

## 🔍 Root Cause
- ✏️ The Dockerfile had the wrong path:
    ```dockerfile
    COPY --from=builder /app/build /usr/share/nginx/html
    ```
- The correct folder is `/app/dist`, not `/app/build`.

---

## 🛠️ Resolution
- 📝 Updated the Dockerfile to use the correct path:
    ```dockerfile
    COPY --from=builder /app/dist /usr/share/nginx/html
    ```
- ✅ Rebuilt the image successfully.

---

## 📈 Result
- The frontend Docker image was built without errors.
- The application was deployed and working as expected.

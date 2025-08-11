



## 
### Clone the Repository

```
$ git clone https://github.com/WhereareyouRaj/todo-app-flask-reactjs.git

$ cd todo-app-flask-reactjs

```

## Folder Structure





## Frontend 

### Requirements:
     - Make sure that nodejs is installed on your system.  
     - Backend must be running.

### Steps: 

1. Move to the `frontend/' folder and run the following command to install the neccessary:

```shell
# This will install what you need for the frontend.

$ npm install 
```

2. Then you will need to run the following command to start running the Frontend:

```shell
$ npm run dev

# You will see something like this:
VITE v5.4.11  ready in 349 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
```

3. That's all for the Frontend, if you haven't run the Backend yet, continue with the next section (Backend)


## Backend

 - Make sure that Python is installed on your system.

```shell
# If it doesn't work this way try "python3", this will depend on how you installed Python on your computer
$ python -m venv venv
```

2. Now activate the development environment and install the necessary requirements found in the `requirements.txt` file:

```shell
# This is how it is done in Linux, in Windows it is as follows "venv\Scripts\activate"
$ . venv/bin/activate
# Now install the necessary requirements using "pip" or "pip3",
# this will depend on how you installed Python on your computer
(venv) $ pip install -r requirements.txt
```

3. Create an .env file and add an environment variable for JWT creation:

```shell
# This is an example
JWT_SECRET_KEY="c7d57142e46f169ce9dbeb8d96603e46"
```

4. Now you can start running the server:

```shell
(venv) $ flask run

# You will see something like this:
* Serving Flask app 'application.py'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://127.0.0.1:5000
Press CTRL+C to quit
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 140-954-082
```

## Containerization:
**[Frontend]** 
- After testing the application by running locally, I containerized the application.
- I used the concept of Multi-stage Dockerfile.
- Clearly defined each steps. 
- Check this **[Dockerfile](./frontend/Dockerfile)**

**[Backend]**
- 
# Rita App - Project Setup

## 1. Frontend (GUI)

If this is your first time running the GUI or a teammate has installed a new package, run the following at root directory:

```sh
npm run gui:wake-up

```

Otherwise, to start the gui, run the following at root directory:

```sh
npm run gui:dev
```

For testing purposes, the app supports running without a backend. To start the GUI independently:

```sh
npm run gui:indep
```

This will open the GUI in your browser. These are custom scripts to simplify the process, but you can also manually run:

```sh
cd gui
npm install
npm start
```

### Note on `npm install`

When installing a new npm package, always `cd gui` first. Installing packages modifies `package.json` and `package-lock.json`, and we don’t want unnecessary changes in the root directory.

## 2. Backend (Server)

Since the project requires many packages, we strongly recommend you to use conda to manage our environment. Make sure you have anaconda [installed](https://docs.anaconda.com/free/anaconda/install/index.html).

If this is the first time you set up the environment, at root directory, run

```sh
conda env create -f server/environment.yml
```

This installs the essential dependencies. However, due to inconsistencies in Conda’s versioning, some packages may be missing. Install them manually using:

```sh
pip install <package>
# or
conda install <package>
```

### Running the backend

Flask is required and included in environment.yml, but if needed, install it manually:

```sh
pip install flask
```

To start the backend, run this at the root directory:

```sh
npm server:dev
```

Or manually,

```sh
cd server
flask run
```

This starts the API on port 5000. You can test it by visiting http://127.0.0.1:5000/hello.

The npm commands are just shortcuts—check `package.json` at the root directory to see what they do.

### Conda basics

If you're not familiar with Conda, learn these basic commands:

- conda activate <env> – Activate an environment
- conda deactivate – Deactivate the current environment
- conda list – List installed packages
- conda install <package> – Install a package

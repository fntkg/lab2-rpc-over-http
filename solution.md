# Lab 2 - Ingeniería web

> Germán Garcés - 757024

This file aims to give necessary information to configure Github actions to build automatically the project on a `push` action and to deploy both server and client.

## Configure Github actions to build *work* branch

Steps followed can be found [here](https://docs.github.com/en/actions/quickstart).

### Creating a workflow to build a branch

It is not necessary to create a `.github/workflows` directory since it is already created in the forked repository.

You just need to **create a new branch** from the bottom of the page.

> Use `work` as asked in the lab.

Committing the workflow file to a branch in your repository triggers the push event and runs your workflow.

![](https://i.imgur.com/fkwLPUm.png)

### Viewing your workflow results

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click Actions.
![](https://i.imgur.com/AZO0mxp.png)
3. In the left sidebar, click the workflow `CI`.
![](https://i.imgur.com/BLyVJml.png)
4. From the list of workflow runs, click the name of the run you want to see.
![](https://i.imgur.com/66KqIYk.png)

## Deploy server and cliente

**Warning**: The client will not run if the server is not deployed so the first step will always be to deploy the server.

### Fixing the server

There is a `TODO` in file `lab2-rpc-over-http/blob/work/server/src/main/kotlin/translator/Server.kt`

It has to be changed to:

```kotlin=
TranslationResponse().apply {
    translation = "Traduceme!"
}
```

### Deploying the server

1. Build the server:

```bash
./gradlew :server:build
```

2. Start the server:

```bash
./gradlew :server:bootRun
```

The server is now exposed on port `8080`.

### Deploying the cliente

1. Build the client

```bash
./gradlew :client:build
```

2. Start the client

```bash
./gradlew :client:bootRun
```

![](https://i.imgur.com/YA3AFRO.png)

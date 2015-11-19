# How to create lesson and exercise

## Creating a lesson

Creating a lesson is easy – just go to **[My Lessons](https://ru.hexlet.io/teacher/lessons)** page and click on **[Add new lesson](https://ru.hexlet.io/teacher/lessons/new)** button. There you can add theory, write transcription for the video (optional), create quiz questions and select an exercise. If it is your first lesson, then most probably you have no exercises to select yet. The next section explains how to create you first exercise.

Read more about [Conceptual specifications for lessons](conceptual-specifications.md) and [Technical specifications for lessons.﻿](technical-specifications.md)

## Creating an exercise

Exercise includes:

* Description of the task (what is the challenge for the student, what needs to be done in order to complete the exercise)
* Definition of the development environment (e.g. what programming languages, frameworks, servers are required to complete the exercise)
* Tests (to automatically assess student's solution)
* Solution (will not be shown to students)

In order to include an exercise to a lesson follow these steps:

1. Download Hexlet Exercise Kit
2. Create an exercise locally
3. Test your exercise
4. Push it to Bitbucket (private repository)
5. Login to Hexlet via Bitbucket
6. Go to **[My Exercises](http://hexlet.io/account/exercises)**, add new exercise repository url and click "Build". Hexlet builds a Docker container with the environment you have defined. When it is built, you can include this exercise into any lesson.

Let's go over each step in more detail.

### 1. Set up the Hexlet Exercise Kit

To create and test lessons on your computer all you need is [Docker](http://docker.io). If you're a Linux user, [just install](https://docs.docker.com/installation/#installation) Docker and move on to part **[2. Create an exercise](#2-create-an-exercise)**

If you're on Windows or Mac OS X, we recommend using [boot2docker](http://boot2docker.io/).

#### 1.1 Install VirtualBox, boot2docker and Git

VirtualBox is a free virtual machine from Oracle. Download and install a version for your operating system. Please, refer to the [official documentation](https://www.virtualbox.org/wiki/End-user_documentation) if needed.

[boot2docker](http://boot2docker.io/) is a lightweight Linux distribution based on Tiny Core Linux made specifically to run Docker containers. It runs completely from RAM, weighs ~27MB and boots in ~5s. Go to [boot2docker.io](http://boot2docker.io/) and install the version for your operating system.

In case you don't have [Git](http://git-scm.com/) installed already, go ahead and [download](http://git-scm.com/downloads) and install it too.

#### 1.2 Get hexlet-exercise-kit

Go to your home directory and clone `hexlet-exercise-X` repository, where X == your chosen language. Here are the available languages:

```
hexlet-exercise-php
hexlet-exercise-javascript 
hexlet-exercise-java 
hexlet-exercise-ruby 
hexlet-exercise-python
```

boot2docker shares the home directory with the VM, so you MUST have the hexlet-exercise-kit in your home directory.

    git clone git@github.com:Hexlet/hexlet-exercise-php.git
    cd hexlet-exercise-kit

#### 1.3 Docker Machine

On OS X or Windows, use [Docker Toolbox](https://docs.docker.com/v1.8/installation/mac/).

### 2. Create an exercise

Create and test your exercise inside `hexlet-exercise-kit/exercises/MY_EXERCISE` folder. Here is an example of a Hexlet exercise – [https://github.com/Hexlet/example_exercise](https://github.com/Hexlet/example_exercise). You have to follow the same folder and file structure.

#### README.md

README.md file contains description of the task written in markdown syntax. This text will be shown to a student when s/he starts the exercise.

#### Dockerfile

Hexlet will build a Docker image for your exercise, so you need a `Dockerfile`. It should be inherited from our base image (see first line [here](https://github.com/Hexlet/example_exercise/blob/master/Dockerfile)). Include any steps needed for your environment. Please, refer to [Docker documentation](https://docs.docker.com/reference/builder/). Also, take a look at [Best practices for writing Dockerfiles](https://docs.docker.com/articles/dockerfile_best-practices/).

Install additional software with [apt-install](https://github.com/Hexlet/hexlet-exercise-kit/blob/master/base_image/scripts/apt-install) script. It will automatically set the correct flags for apt-get and clean stuff before leaving. See [example](https://github.com/Hexlet/example_exercise/blob/master/Dockerfile).

#### Ignorefile

Include files and folders you want to hide from students ([see example](https://github.com/Hexlet/example_exercise/blob/master/Ignorefile)).

*Why? Exercise should include the solution, but of course you want to hide that solution from the student. You can mark parts of a file with BEGIN and END in order to hide those parts, but if you want to hide the whole file, as if it doesn't exist, then put the path to that file into Ignorefile.*

#### services.conf

Sometimes you need to have some services running in your exercise (e.g., Redis server or database server). Define the configuration file for supervisord (
[see example](https://github.com/Hexlet/example_exercise/blob/master/services.conf)). Refer to [Docker documentation](https://docs.docker.com/articles/using_supervisord/) for more info.

#### Makefile

Just leave it as in [example](https://github.com/Hexlet/example_exercise/blob/master/Makefile).

#### exercise/

This is the folder students see. Include the full solution here and mark the parts you want to hide (because you don't want students to see the full solution, right?) with BEGIN and END comments, like in [this example](https://github.com/Hexlet/example_exercise/blob/master/exercise/read_solution.py). Comment out BEGIN and END in any language you use. You can have multiple BEGIN-END blocks in a single file. Students will not see the code between those marks.

Sometimes you want to hide the whole file. In the example exercise we hide 'write_solution.py' file. This can be done with Ignorefile as described above.

#### exercise/Makefile
There is only one convention: Makefile should has one rule – "test" ([see example](https://github.com/Hexlet/example_exercise/blob/master/exercise/Makefile)). It describes how a solution is tested.

Since your exercise must include the full solution, your tests should pass upon submitting the exercise. Hexlet will check if your tests pass with your solution, as well as if tests fail after solution is hidden (after processing the BEGIN-END blocks and Ignorefile).

It is up to you what and how to test.

####

### 3. Test your exercise

In order to make sure your exercise builds and runs, test it like so:

```
make build
make start
make test
```

This will build the image (the same way Hexlet will build it in the cloud), start container and run tests. If you want to restart the container, just run 'make start' again.

### 4. Push your exercise to Bitbucket

Right now we support [Bitbucket](https://bitbucket.org/) primarily because you can create private repositories for free. Create one and push your exercise into master branch.

**IMPORTANT**: due to [Docker Registry bug](https://github.com/docker/docker-registry/issues/901), repo names with more than 30 characters are rejected. So, make sure your repo name is 30 characters or less.

### 5. Login to Hexlet via Bitbucket

[Login to Hexlet](http://hexlet.io/session/new) using your Bitbucket account and grant the permissions it asks for.

### 6. Add new exercise repository url and build

﻿Go to *[My Exercises](http://hexlet.io/account/exercises)*, click *[Add new exercise](https://hexlet.io/account/exercises/new)* button, put the title for your exercsie and the BitBucket repository address (e.g. `git@bitbucket.org:hexlet-exercises/javascript_closures_exercise.git`). Hit "Create exercise" button.

At this point you will be redirected to "My exercises" page and you will see your exercise in the list. It's state will be "not built", which means it is not ready for lessons yet. Click on the edit button and then click "Build". This will take some time: Hexlet build a Docker image for you. On the build page you will see the log and errors, if any.

When it's done, you'll see the status changed to "built":

![Build screen](assets/lesson-build-screen.png)

At this point you can add this exercise to any lesson you've created or will create.

## Updating exercise

When you need to update your exercise (e.g. add something new or fix bugs), just push the changes to your Bitbucket repository. Hexlet will detect new commits and rebuild the image automatically.

However, if you have started an exercise on the website (as students), then you will have to reset progress and start it again after an update to be able to see the changes.

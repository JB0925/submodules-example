## Submodules
Submodules are a way for you to be able to have separate git repositories for several different projects, but track them in one "parent" project. The information below will discuss how this can be accomplished.

## Getting Started
First, ensure that both your "parent" directory and **each "child" directory** have their own separate repositories on GitHub. Locally,
you move any child projects into the "parent" project ( or make copies of them ). Note that this does not **have** to be done, but may be easier for the sake of organization.
**Important**: Each child project should have its own git history locally on your machine as well, created by running `git init` in each one and adding and commmiting as needed.
The parent project should also have its own git history, also created via running `git init` in it.

## How This Example Was Created
- Run `mkdir -p submodules-example/{project1,project2,project3} && cd submodules-example`
### Setting Up Each Child Project
- `cd` into `project{1..3}` add some trivial code in each, and run `git init`. 
- Add and commit this new file in each of `project{1..3}`
- Get the SSH url from GitHub for each child project and run `git remote add origin git@github.com...` in each child project.
- In each child project, run `git push -u origin master`.
- Optional: You can go to GitHub to verify that the content was pushed if it will give you peace of mind.
### Setting Up The Parent Project
- `cd` back to the `submodules-example` parent project.
- Run `git init && git remote add origin git@github.com...`, where the `git@github.com...` comes from the SSH url of the parent project on GitHub.
### Creating The Submodules
- In the parent project, run, `git submodule add git@github.com/YourUsername/projectName.git /path/on/your/machine/to/your/project`, where the `git@github` url comes from the SSH url of the child project you are adding.
- Do this for all child projects that you want to add to the parent project.
- **NOTE**: To find this SSH url, click on the green **Code** button in each repository on GitHub. Make sure it is on SSH ( it is by default ) and click "copy."
- Finally, run `git add . && git commit -m "Adding submodules" && git push -u origin master`. Note that the commit message can be anything you want.
- Now, when you go to the parent project on GitHub each of the child projects will be linked inside of it.
## What If I Want To Clone This In The Future?
- Run `git clone --recurse-submodules git@github.com/YourUsername/YourParentProject.git`. Please refer to the note above to learn where to get this url from.
## What If I Need To Make Updates To One Of The Child Projects?
- Make your update in the child project.
- In the child project directory, add, commit, and push the changes to the child repository on GitHub.
- `cd` to the parent project and run `git add /path/to/project/you/just/changed && git commit -m "Updating submodules after change to child project." && git push`


# pre-commit Tutorial

[pre-commit](https://pre-commit.com/) is a convenient gatekeeper package that helps you commit high-quality code. It works by running code linters & formatters against the code you commit to make sure that it looks just right.

![](./pre-commit_workflow.svg)


## Installation
To install pre-commit, you have a few options:

```bash
pip install pre-commit
```
or
```bash
conda install -c conda-forge pre-commit
```
>for all installation options, follow this link: https://pre-commit.com/#installation

## Create the pre-commit config
The pre-commit configuration file is where you specify which formatters, linters, and stylers (known as hooks) that pre-commit will use to check your code. [Here is a link with the list of supported hooks.](https://pre-commit.com/hooks.html)

pre-commit looks for a `.pre-commit-config.yaml` file in the root directory of your Git repo. An example pre-commit config file can be found in this repo. ([example](./pre-commit-config.yaml))

## Register pre-commit with Git
To register pre-commit with Git, run the following:
This can be done by running the following:
```bash
pre-commit install
```
Now, when you commit, pre-commit will run.


## Q & A
### Q: I'm am getting a **CalledProcessError**. What should I do?
**A:** While working to get pre-commit on a teammate's machine, I ran into a **CalledProcessError**. Luckily, I was able to get around it with the answer to this post on [Stack Overflow](https://stackoverflow.com/questions/65192345/calledprocesserror-with-git-pre-commit-hook) by simply pinning my version of `virtualenv` to 20.0.33.
Just run the following:
```bash
pip install virtualenv==20.0.33
```


### Q: My pre-commit rules failed! What do I do?
**A:** As I mentioned before, pre-commit integrates into your git workflow. This integration requires a slight adjustment to your workflow. When you type `git commit`, pre-commit jumps in and runs linters & formatters to help you fix your code.
>This is not where you should be running your unit tests.

 Usually, your will fail pre-commit on the first attempt. THIS IS A GOOD THING! 😀

So how do you deal with it?

pre-commit will do its best to stop you from making a Git commit that doesn't pass inspection. Though pre-commit can be bypassed altogether using `git commit --no-verify`, we want to


Here is how to handle it:

- **Code formatter:** Code formatters automatically check and change your code. When a formatter (e.g. [black](https://github.com/psf/black), [nbstripout](https://github.com/kynan/nbstripout), etc.) runs, it will automatically change your file. All you need to do is Git add these files again and reattempt to commit.

- **Code linter:** Code linters automatically check your code and then tell you what is wrong with it. When a linter (e.g. [flake8](https://flake8.pycqa.org/en/latest/), [pylint](http://pylint.pycqa.org/en/latest/), etc.) runs, it will not reformat the code. Instead, it will print out a list of things to fix. Update your files, Git add them again, and reattempt to commit.


### Q: I have conflicting code formatters! What do I do?
**A:** Sometimes, you may run into an issue where one formatter (like isort) wants your code to look one way and another (like black) wants it to look another way. While this doesn't always happen, it can occur, leading to an infinite loop.

When you find your code bouncing endlessly between formatters, here is what to do:
- Make sure that no other issues are being reported by pre-commit
- run the following:
```bash
# This will skip the pre-commit verification altogether
git commit --no-verify
```

# Learn More
Hopefully this helped you get up and running using pre-commit. For more information about pre-commit, I highly recommend watching [this great video series on pre-commit](https://calmcode.io/pre-commit/the-problem.html) by Vincent Warmerdam on https://calmcode.io.

Happy coding!

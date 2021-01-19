# pre-commit Tutorial

## What is pre-commit?
[pre-commit](https://pre-commit.com/) is awesome package that allows you to feel more confident about the code you are committing by running linters & formatters against it when you go to commit.

One of the great things about pre-commit is that it integrates into your Git workflow. Don't worry about forgetting to use it – when you commit, it will just work.

## Installation
Mac & Linux:
```bash
pip install pre-commit
```

Windows:
```bash
curl https://pre-commit.com/install-local.py | python -
```

## pre-commit Install
Now that Pre-Commit is installed on your machine, run the following:
```bash
pre-commit install
```
This will register pre-commit (located in the .pre-commit-config.yaml file) as a Git hook. Now, whenever you commit, pre-commit will run.

## Q & A
As I mentioned before, pre-commit integrates into your Git commit workflow. This integration requires a bit of getting used to.

### Q: What do I do when one of my pre-commit rules fail?
**A:** pre-commit runs code linters & formatters to help you fix your code. This means that when you attempt to commit your code, you will most likely fail pre-commit on the first attempt. THIS IS A GOOD THING! 😀

Here is what to do:

- **Code formatter:** Code formatters automatically check and change your code. When a formatter (e.g. black, nbstripout, etc.) runs, it will automatically reformat the file. Git add these files again and reattempt to commit.
- **Code linter:** Code linters automatically check your code and then tell you what is wrong with it. When a linter (e.g. flake8, pylint) runs, it will not reformat the code. Instead, it will give you a list of things to fix. Update your files, re-add them the staging area (git add), and reattempt to commit.


### Q: I have conflicting code formatters! What do I do?
**A:** Sometimes, you may run into an issue where one formatter (like isort) wants your code to look one way and another (like black) wants it to look another way. While this doesn't always happen, it can occur, leading to an infinite loop.

When you find your code bouncing endlessly between formatters, here is what to do:
- Make sure that no other issues are being reported by pre-commit
- run the following:
```bash
# This will skip the pre-commit verification altogether
git commit --no-verify
```

Happy coding!

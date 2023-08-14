# LEFT-HOOK

- It is a utility which uses the pre-existing hooks of git to perform tasks before or after a git operation.
- There are many hooks in git which you can use with the left-hook utility, you can find all the scripts of hook which are available for git in the .git/hooks folder.
- To make changes for the operation which git perform after calling a hook you can define in the lefthook.yml file

# Configuration

- To configure the left-hook for performing operation for git hooks, you write in the yml file, which will create configuration for the script which eventually runs when you perform the git operation, for example- you want to perform check for commit-msg when commiting, you can create a custom script or use a tool like commitlint for checking the commit msg, you can configure it in the left-hook yml.

  ```
  commit-msg:
    commands:
      'lint commit message':
        run: yarn run commitlint --edit {1}
  ```

- There are mainly 2 types how you can perform a script run when performing a git opertaion.
  1. Using command for running a program which you is installed system-wide, like yarn or git, but when you run them in a directory they have a local scope.
  2. Using scripts, which is creating your own custom scripts, for performing a task after hook is called, you add this script in your project in .lefthook folder, you have this script under the hook you will call this script for. for example
     - You created a script "my-script.sh" for running post-commit, then you will add that script in `.lefthook/post-commit/my-script.sh`
     ````yml
     post-commit:
         scripts:
             'my-script.sh':
                 runner: bash
             'any.go':
                 runner: go run
         ```
     ````
- There are many other configuration you can do with left-hook, which you can see on this [page.](https://github.com/evilmartians/lefthook/blob/master/docs/configuration.md)

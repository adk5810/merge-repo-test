# merge-repo-test

Steps to merge repos
Merging below repos to merge-repo-test https://github.com/adk5810/merge-repo-test.git
a. web     https://github.com/adk5810/mslearn-tailspin-spacegame-web.git
b. web-deploy      https://github.com/adk5810/mslearn-tailspin-spacegame-web-deploy.git
c. web-models      https://github.com/adk5810/mslearn-tailspin-spacegame-web-models.git

Step 1:
Add remotes to new repo
git remote add web https://github.com/adk5810/mslearn-tailspin-spacegame-web.git
git remote add web-deploy https://github.com/adk5810/mslearn-tailspin-spacegame-web-deploy.git
git remote add web-models https://github.com/adk5810/mslearn-tailspin-spacegame-web-models.git

Step 2:
Fetch the tags for all repos
git fetch web --tags
git fetch web-deploy --tags
git fetch web-models --tags

Step 3:
Create new branches from remote mains of all 3 repos
main-web
git checkout -b main-web remotes/web/main
main-web-deploy
git checkout -b main-web-deploy remotes/web-deploy/main
main-web-models 
git checkout -b main-web-models remotes/web-models/main

[![Build Status](https://dev.azure.com/adi5810/TalentNext%20Project%202/_apis/build/status/mslearn-tailspin-spacegame-web?branchName=main)](https://dev.azure.com/adi5810/TalentNext%20Project%202/_build/latest?definitionId=22&branchName=main)

# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## For maintainers: Updating feature branches

This repository uses feature branches to associate code with specific modules on Microsoft Learn. Any changes you make to the default branch will likely need to be propagated to each feature branch in this repo. A common example is when we need to update Node packages in `package.json`.

Here's one way to update the remote feature branches when you make a change to the default branch. Note that this process deletes all local branches except for `main`.

```bash
# Synchronize with the remote main branch
git checkout main
git pull origin main
# Delete all local branches except for main
git branch | grep -ve "main" | xargs git branch -D
# List all remote branches except for main
branches=$(git branch -r 2> /dev/null | grep -ve "main" | cut -d "/" -f 2)
# Synchronize each branch with main and push the result
while IFS= read -r branch; do
    # Fetch and switch to feature branch
    git fetch origin $branch
    git checkout $branch
    # Ensure local environment is free of extra files
    git clean -xdf
    # Merge down main
    git merge --no-ff main
    # Break out if merge failed
    if [ $? -ne 0 ]; then
        break
    fi
    # Push update
    git push origin $branch
done <<< "$branches"
# Switch back to main
git checkout main
```

# Legal Notices

Microsoft and any contributors grant you a license to the Microsoft documentation and other content
in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the
[LICENSE-CODE](LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.

Privacy information can be found at https://privacy.microsoft.com/en-us/

Microsoft and any contributors reserve all other rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.

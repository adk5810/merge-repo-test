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

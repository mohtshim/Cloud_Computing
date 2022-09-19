### Host your resume in github
To host your resume in the github first we need to make the repository.
To make the repository you can follow this [guide](https://docs.github.com/en/get-started/quickstart/create-a-repo).

Now you need to make the clone of that repository in your local machine. We assume that you have your git command installed. Open your command prompt and write this 
command
```
git clone https://github.com/username/repositoryname
```

Now add the resume in that repository and write the following command
```
git add "resume_name"
```
After your resume is added you need to staged the resume using commit command
```
git commit -m "Your massage here"
```
After that push the changed in your remote repository
```
git push origin branch_name
```
You can check the status of the repository using the following command 
```
git status
```

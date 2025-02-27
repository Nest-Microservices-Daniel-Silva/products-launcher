## Dev
1. Clone the repository
2. Create a .env based on .env.template
3. Run the command `git submodule update --init --recursive` to rebuild submodules
4. Run the command `docker compose up --build`

### Steps to create Git Submodules
1. Create a new repository on GitHub
2. Clone the repository to your local machine
3. Add the submodule, where `repository_url` is the URL of the repository and `directory_name` is the folder name where you want to store the submodule (it must not already exist in the project)
```bash
git submodule add <repository_url> <directory_name>
```
4. Add changes to the repository (git add, git commit, git push)
   Example:
```bash
git add .
git commit -m "Add submodule"
git push
```
5. Initialize and update Submodules, when someone clones the repository for the first time, they must run the following command to initialize and update the submodules
```bash
git submodule update --init --recursive
```
6. To update submodule references
```bash
git submodule update --remote
```

## Important
If you're working in a repository that has submodules, **first update and push** in the submodule and **then** in the main repository.
If done in reverse order, submodule references in the main repository will be lost and you'll have to resolve conflicts.

## Production
1. Clone repository
2. Create a .env based on .env.template
3. Run the command to build the images
```bash
docker compose -f docker-compose.prod.yml build
```
4. Run the command to start the containers
```bash
docker compose -f docker-compose.prod.yml up
```

from github import Github

# GitHub credentials
username = "your_username"
token = "your_token"
repository_name = "your_repository_name"

# Connect to the repository
g = Github(username, token)
repo = g.get_user().get_repo(repository_name)

# To-Do list file
file_path = "todo.md"

# Tasks to add
tasks = ["Task 1", "Task 2", "Task 3"]

# Fetch existing content
contents = repo.get_contents(file_path)
existing_content = contents.decoded_content.decode("utf-8")

# Update the to-do list
for task in tasks:
    task_line = f"- [ ] {task}\n"
    if task_line not in existing_content:
        existing_content += task_line

# Commit changes
repo.update_file(
    path=file_path,
    message="Update to-do list",
    content=existing_content,
    sha=contents.sha,
)

print("To-do list updated successfully.")

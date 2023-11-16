from github import Github
username = "your_username"
token = "your_token"
repository_name = "your_repository_name"

g = Github(username, token)
repo = g.get_user().get_repo(repository_name)
file_path = "todo.md"

tasks = ["Task 1", "Task 2", "Task 3"]
contents = repo.get_contents(file_path)
existing_content = contents.decoded_content.decode("utf-8")


for task in tasks:
    task_line = f"- [ ] {task}\n"
    if task_line not in existing_content:
        existing_content += task_line


repo.update_file(
    path=file_path,
    message="Update to-do list",
    content=existing_content,
    sha=contents.sha,
)

print("To-do list updated successfully.") 

# Team: Project and Code Source

Use a Team project to connect source control and define the code revision used by analysis.

## Create the project

1. Open **Team Projects**.
2. Choose **New project**.
3. Set the project name and Project Owner.
4. Set the default branch.
5. Save the project.

## Add a code source

1. Open the project code source settings.
2. Create an SCM profile for GitHub, GitLab, or Bitbucket.
3. Choose bearer token, basic auth, or SSH key.
4. Create the Code Source.
5. Test the connection.
6. Select a branch, tag, commit, PR/MR, local Git source, or patch-only source.

![Team project and code source](../assets/team/team-project-and-code-source.png)

### Result

The project lists a tested code source and a selectable revision for baseline or iteration work.

### Common issue

If the connection succeeds but no revision is listed, check the repository permissions and the selected default branch.

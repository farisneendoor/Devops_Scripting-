# GitHub Repository Access Manager

A lightweight Bash script that automates GitHub repository administration using the GitHub REST API — retrieve contributor and collaborator information programmatically to manage user access across projects, without needing to click through the GitHub UI.

## Features

- 🔍 List all collaborators on a repository with **read (pull) access**
- 🔐 Authenticates securely via a GitHub Personal Access Token (PAT)
- ⚙️ Works with both personal repositories and organization-owned repositories
- 🧩 Built entirely with `bash`, `curl`, and `jq` — no additional dependencies

## Prerequisites

Make sure the following are installed on your machine:

```bash
sudo apt update
sudo apt install -y curl jq git
```

Verify installation:
```bash
curl --version
jq --version
```

You'll also need a **GitHub Personal Access Token** with `repo` scope:
1. Go to **GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)**
2. Click **Generate new token**
3. Select the `repo` scope
4. Copy the token immediately — GitHub only shows it once

## Setup

Clone this repository:
```bash
git clone https://github.com/farisneendoor/Devops_Scripting-.git
cd Devops_Scripting-
```

Set your GitHub credentials as environment variables:
```bash
export username="your-github-username"
export token="your-personal-access-token"
```

Make the script executable:
```bash
chmod +x list-users.sh
```

## Usage

```bash
./list-users.sh <repo_owner> <repo_name>
```

**Example — personal repository:**
```bash
./list-users.sh farisneendoor Devops_Scripting-
```

**Example — organization-owned repository:**
```bash
./list-users.sh my-org-name backend-service
```

### Sample Output
```
Listing users with read access to farisneendoor/Devops_Scripting-...
Users with read access to farisneendoor/Devops_Scripting-:
farisneendoor
```

If no collaborators have read access, the script will output:
```
No users with read access found for <owner>/<repo>.
```

## How It Works

The script sends an authenticated `GET` request to the GitHub API's `collaborators` endpoint:
```
GET https://api.github.com/repos/{owner}/{repo}/collaborators
```

The JSON response is parsed with `jq`, filtering for collaborators whose `permissions.pull` field is `true` — meaning they have at least read access to the repository.

## Notes & Limitations

- The authenticated user must have **admin access** to the target repository to view its collaborator list via this endpoint.
- For organization repositories, your token must belong to an account that is a **member of that organization**.
- GitHub API rate limits apply: **5,000 requests/hour** for authenticated requests.
- Never commit your Personal Access Token to version control. Use environment variables (as shown above) or a `.env` file excluded via `.gitignore`.

## Roadmap

- [ ] Add collaborator (`push`, `admin`, `maintain`, `triage` permission levels)
- [ ] Remove collaborator access
- [ ] Bulk audit access across multiple repositories
- [ ] Scheduled reporting via cron

## License

This project is open for personal and educational use.

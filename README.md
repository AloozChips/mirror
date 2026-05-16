# File Mirroring Workflows

Automated file mirroring across cloud storage providers using GitHub Actions — no servers required.

## Supported Workflows

| Source | Destination | Status |
|--------|-------------|--------|
| Pixeldrain | Cloudflare R2 | Available |
| Pixeldrain | SourceForge | Available |

More mirror targets and providers are planned for future releases.

---

## Features

- Manual workflow triggers via GitHub Actions UI
- Folder/path support for organized uploads
- Built for large file transfers
- Credentials stored securely via GitHub Secrets
- Telegram notifications on success and failure
- MD5 & SHA256 checksum generation per mirrored file
- Straightforward to extend with additional providers

---

## Setup

Before running any workflow, add the required secrets to your repository:

```
Repository → Settings → Secrets and variables → Actions
```

Each workflow has its own set of required secrets. See the [Workflows](#workflows) section below.

---

## Workflows

### Pixeldrain → Cloudflare R2

Mirrors a file from Pixeldrain to a Cloudflare R2 bucket.

**Required Secrets**

| Secret | Description |
|--------|-------------|
| `R2_ACCESS_KEY_ID` | Cloudflare R2 Access Key ID |
| `R2_SECRET_ACCESS_KEY` | Cloudflare R2 Secret Access Key |
| `R2_ENDPOINT` | Cloudflare R2 Endpoint URL |
| `TG_BOT_TOKEN` | Telegram Bot Token |
| `TG_CHAT_ID` | Telegram Chat ID |

**Workflow Inputs**

| Input | Required | Description |
|-------|----------|-------------|
| `pd_url` | Yes | Pixeldrain file URL |
| `r2_bucket` | Yes | Target R2 bucket name |
| `r2_folder` | No | Destination folder path |

> Public downloads from Cloudflare R2 should use the `r2.dev` public URL.

---

### Pixeldrain → SourceForge

Mirrors a file from Pixeldrain to a SourceForge project via SSH.

**Required Secrets**

| Secret | Description |
|--------|-------------|
| `SF_SSH_KEY` | SourceForge SSH Private Key |
| `TG_BOT_TOKEN` | Telegram Bot Token |
| `TG_CHAT_ID` | Telegram Chat ID |

**Workflow Inputs**

| Input | Required | Description |
|-------|----------|-------------|
| `pd_url` | Yes | Pixeldrain file URL |
| `sf_user` | Yes | SourceForge username |
| `sf_project` | Yes | SourceForge project name |
| `sf_folder` | No | Destination folder path |

> SourceForge uploads require SSH access to be configured on your account.

---

## Usage

1. Go to the **Actions** tab in your repository
2. Select the workflow you want to run
3. Click **Run workflow**
4. Fill in the required inputs and confirm

---

## Contributing

Contributions are welcome. Feel free to open issues or submit pull requests to improve or extend the workflows.

## License

This project is licensed under the [MIT License](LICENSE).

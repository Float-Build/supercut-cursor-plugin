<p align="center">
  <img src="assets/logo.png" alt="Supercut" width="96" height="96">
</p>

# Supercut for Cursor

Connect [Supercut](https://supercut.ai) to Cursor. Supercut is a platform for recording and sharing videos with AI-powered editing. This plugin lists Supercut's remote MCP server in the Cursor Marketplace so Cursor's agent can search your recordings, read transcripts, pull frames, review comments and analytics, manage playlists, and download raw captures.

The MCP server lives at `https://mcp.supercut.ai/mcp`. This repository only contains the marketplace manifest, logo and documentation. It does not contain the server.

## Install

1. Open Cursor and go to the Marketplace.
2. Search for **Supercut** and click **Install**.
3. When Cursor prompts you to authenticate, sign in with your existing Supercut account.

That's it. No API keys or tokens to copy. Authentication is OAuth: Supercut's authorization server supports dynamic client registration, so Cursor registers itself and walks you through the normal Supercut sign-in flow.

You can also add the server by hand. In Cursor's MCP settings, add:

```json
{
  "mcpServers": {
    "supercut": {
      "url": "https://mcp.supercut.ai/mcp"
    }
  }
}
```

## Example prompts

- Find the recording where I walked through the new billing flow and summarize the key decisions.
- Which of my recordings from the last month got the most views, and what's their engagement rate?
- Summarize the comments and reactions on my latest recording and tell me what needs a follow-up.

## What the agent can do

Once connected, Cursor's agent can work with your Supercut recordings directly:

- **Find and read recordings.** Search by meaning or keyword, list owned, watched or shared recordings, get metadata, pull the transcript, or grab a frame at a timestamp.
- **Review engagement.** Read comments, timeline reactions, viewer form responses, and viewership analytics such as visits, plays and engagement rate.
- **Organize playlists.** List playlists and their recordings, and add a recording to an existing playlist.
- **Download media.** Get download URLs for the rendered video or the raw screen and camera captures.
- **Access raw assets.** Fetch the original recording's microphone and system audio, word-level aligned transcript, and mouse and keyboard activity captures.

Adding a recording to a playlist is the only action that changes data. Everything else is read-only. Download and raw-asset tools return short-lived signed URLs rather than file contents.

The exact tool list and each tool's description come from the server itself and show up in Cursor's MCP settings after you connect. They may grow over time without changes to this repository. For details on what each capability returns, see the [API docs](https://api.supercut.ai/v1/docs), which the MCP server mirrors.

## Permissions and access

The agent only sees what your Supercut account can see. Workspace rules apply as usual: analytics, downloads and raw assets each require the corresponding access on the recording or workspace, and the tools return an error when you lack it.

## Repository layout

```
.cursor-plugin/plugin.json   Marketplace manifest
mcp.json                     MCP server definition
assets/logo.svg              Plugin logo (PNG alongside for the README)
LICENSE                      MIT
SECURITY.md                  Vulnerability reporting
```

## Support

- [Help center](https://help.supercut.ai)
- [API documentation](https://api.supercut.ai/v1/docs)
- Email: hello@supercut.ai
- X / Twitter: [@supercut_video](https://x.com/supercut_video)

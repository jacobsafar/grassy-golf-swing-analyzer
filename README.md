# Golf Swing Analyzer by Grassy

AI golf swing analysis for Claude. Upload a swing video and Grassy measures it with 3D body tracking: posture, hip and chest turn, sway and slide, head movement, early extension and more, each with its measurement uncertainty and a same-view tour-player reference. Claude then coaches you from those measurements: one priority tied to your miss, a drill, and a check for your next swing. You can also compare your swing with tour players Grassy has measured, or with another swing you upload, such as your own best one.

## What's included

- **Connector:** Grassy's remote MCP server at `https://mcp.grassy.golf/mcp`, with tools to start an analysis, get results, list your swings and compare swings.
- **Skill:** `golf-swing-coach`, which teaches Claude how to run an analysis, give filming tips and coach from the results without overclaiming.

## Requirements

- A Grassy account. You sign in with your phone number at grassy.golf the first time you connect.
- Swing analysis is part of Grassy plans. Every account includes 2 free analyses through Claude. See https://www.grassy.golf/plans.

## What it sends and stores

- **Your swing video:** uploaded by you on a grassy.golf page to Grassy's storage, never through the chat. Grassy analyzes it to produce body-movement measurements.
- **Stored under your Grassy account:** the video, the measurements and key frames. You can delete them in Grassy.
- **Shared with Claude:** the analysis results (measurements, coaching reference text and up to 4 key frames) are returned to Claude in your conversation.
- **Kept by Grassy for the connection:** hashed sign-in tokens and a usage count. No ads, and no data sold.

The plugin itself runs no local code. It only declares the remote connector and the coaching skill.

Privacy: https://www.grassy.golf/privacy · Terms: https://www.grassy.golf/terms · Support: support@grassy.golf

## Example prompts

- "Analyze my golf swing."
- "Why do I keep slicing my driver?"
- "Compare my swing to Jon Rahm's."
- "Give me one drill for my early extension."

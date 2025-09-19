# YouTube Gatekeeper v0.1.0 (Stable)

**YouTube 守門員** is a Tampermonkey userscript designed to enhance your YouTube experience by allowing you to block or whitelist channels, filter videos by duration, and manage content with a user-friendly tabbed interface. This stable release (`v0.1.0`) introduces the core functionality with optimized performance.

## Features
- **Channel Management**: Block or whitelist YouTube channels with dedicated buttons next to video items.
- **Keyword Filtering**: Block videos based on specific keywords in their titles.
- **Video Duration Filter**: Hide videos shorter than a user-defined duration (default: 30 seconds).
- **Whitelist Mode**: Optionally display only whitelisted channels.
- **Export/Import**: Save and load your blocked/whitelisted channels and keywords as JSON files.
- **Responsive UI**: A modern, tabbed management interface for easy configuration.

## Changelog
- **Button Display Optimization**: Expanded DOM selectors to support more YouTube page structures, including `yt-lockup-view-model` and `ytd-rich-item-renderer` variants.
- **Channel Identification Fallback**: Uses channel name as a fallback identifier when `channelId` is unavailable for blocking/whitelisting.
- **UI Improvements**: Enhanced version information display in the management UI.

## Installation
1. Install a userscript manager like [Tampermonkey](https://www.tampermonkey.net/).
2. Download the script from the [release assets](#) or install directly via [GreasyFork](https://greasyfork.org/scripts/547729).
3. The script runs automatically on YouTube (`https://www.youtube.com/*`).

## Usage
- Click the **內容管理** (Content Management) button in the YouTube masthead to open the management UI.
- Use the tabs to manage blocked/whitelisted channels, keywords, or view version info.
- Block or whitelist channels directly from video items using the **封鎖** (Block) or **白名單** (Whitelist) buttons.

## License
This script is licensed under the [MIT License](LICENSE).

## Feedback
Report issues or suggest improvements on the [GitHub Issues page](https://github.com/[YourUsername]/YouTube-Gatekeeper/issues).

---
**Author**: MayoHu  
**Download**: [YouTube 守門員 穩定版-0.1-optimized.user.js](https://update.greasyfork.org/scripts/547729/YouTube%20%E5%AE%88%E9%96%80%E5%93%A1.user.js)  
**Support**: For updates, check [GreasyFork](https://greasyfork.org/scripts/547729) or the [GitHub repository](https://github.com/[YourUsername]/YouTube-Gatekeeper).

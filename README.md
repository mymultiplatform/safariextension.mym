# safariextension.mym
BLOCK WEBSITE PATHS like YouTube shorts




Safari Extension: Block YouTube Shorts
This document provides instructions on how to create a Safari Web Extension to block specific URL
paths such as 'https://www.youtube.com/shorts/'. This project leverages the Safari Web Extensions
API and WebExtensions framework.
1. Set Up Development Environment
1. Install Xcode from the Mac App Store.
2. Enable Safari Developer Tools:
- Open Safari.
- Go to Safari > Preferences > Advanced.
- Enable 'Show Develop menu in menu bar'.
2. Create a Safari Web Extension Project
1. Open Xcode.
2. Create a new project: File > New > Project.
3. Select 'Safari Web Extension' and configure the bundle identifier.
3. Define Blocking Logic in JavaScript
Add the following logic in a 'background.js' script to listen for network requests and block paths
containing '/shorts/':
browser.webRequest.onBeforeRequest.addListener(
  function (details) {
    if (details.url.includes('/shorts/')) {
      console.log('Blocking:', details.url);
      return { cancel: true };
}
},

{ urls: ['*://*.youtube.com/*'] },
  ['blocking']
);
4. Set Up manifest.json
Add the following 'manifest.json' file to describe your extension's permissions and functionality:
{
'manifest_version': 2,
'name': 'Block YouTube Shorts',
'version': '1.0',
'description': 'Blocks access to YouTube Shorts',
'permissions': [
  'webRequest',
  'webRequestBlocking',
'tabs',
  '*://*.youtube.com/*'
],
'background': {
  'scripts': ['background.js']
}
}
5. Test Your Extension
1. Build and run your extension in Xcode.
2. Safari will launch with your extension loaded for testing.
6. Enable and Debug the Extension
1. Open Safari and go to Safari > Preferences > Extensions.

2. Enable your extension.
3. Use the Develop menu to debug and check logs.
Resources
- Safari Web Extensions Guide:
https://developer.apple.com/documentation/safariservices/safari_web_extensions/
- WebExtensions API Documentation:
https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions
- Xcode Documentation: https://developer.apple.com/xcode/

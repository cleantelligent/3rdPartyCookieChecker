## 3rd Party Cookie Checker

### Purpose
This repository is hosted on GitHub Pages in order to check whether 3rd party cookies are enabled.

### Instructions
Here is the client-side HTML required to check if 3rd party cookies are enabled or disabled:

```markdown
<iframe src="https://cleantelligent.github.io/3rdPartyCookieChecker/3rdPartyCookieChecker.html" style="display:none"></iframe>
```

Here is the client-side JavaScript used to add an event listener:

```markdown
var receiveMessage = function (e) {
  if (e.data === 'CT-3rdPartyCookiesDisabled') {
    // $('div#thirdPartyCookiesDisabled').show();
  }
};
window.addEventListener("message", receiveMessage, false);
```

### How it works
3rdPartyCookieChecker.html creates the cookie named ctCookie and sets its value to true. It then redirects to 3rdPartyCookieVerifier.html, which checks if the cookie has been set. Since we are including 3rdPartyCookieChecker.html via an iframe on the client side, cleantelligent.github.io is considered a 3rd party. We then add an event listener to wait for 3rdPartyCookieVerifier.html to post a message letting the client know if 3rd party cookies are enabled or disabled. It may be wise to set a timeout when waiting for the message to be posted, just in case there is some sort of network error.

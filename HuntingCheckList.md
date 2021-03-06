**Sessions**

- Make a user with every role and check if he can directly access pages he should not be able to
- Take away a role and check if the user can still do the actions before logging out
- Look at the session token, does it change? If not, they might be useable for session fixation
- Delete a logged in user and check if he can still do actions before logging out

--------

**Stored XSS**

*Tips*
- For every input field
	- Try to get ```<a href=#>test</a>``` an entity in
	- Try to get an obfuscated entity in
	- If it catches on anything, go deeper

*video's*
- https://www.youtube.com/watch?v=uHy1x1NkwRU

--------
	
**Reflected XSS**

*Tips*
- Check the error pages (404,403,..) sometimes they contain reflected values
	- Trigger a 403 by trying to get the .htaccess file
- Try every reflected parameter

*video's*
- https://www.youtube.com/watch?v=wuyAY3vvd9s
- https://www.youtube.com/watch?v=GsyOuQBG2yM
- https://www.youtube.com/watch?v=5L_14F-uNGk
- https://www.youtube.com/watch?v=N3HfF6_3k94

--------

**DOM XSS**

*Tips*
- Would not recommend manually looking for DOM XSS
- Burp suite PRO scanner can find DOM XSS
- Tool: https://github.com/dpnishant/ra2-dom-xss-scanner

*video's*
- https://www.youtube.com/watch?v=gBqzzhgHoYg
- https://www.youtube.com/watch?v=WclmtS8Ftc4

--------

**XSS filter evasion tips**

*Tips*
- < and > can be replace with html entities &lt; and &gt;
- You can try an XSS polyglot
	- ```javascript:/*--></title></style></textarea></script></xmp><svg/onload='+/"/+/onmouseover=1/+/[*/[]/+alert(1)//'>```
	- https://gist.github.com/michenriksen/d729cd67736d750b3551876bbedbe626
	
	
--------

**CSRF**

*Tips*
- Check if there is a CSRF token
- Check if the token changes
- Check if the server still accepts the token if you give it a random token

*video's*
- https://www.youtube.com/watch?v=ImqLlFMQrwQ

--------

**Cookie**

*Tips*
- Httponly flag?
- Secure flag?
- Is the domain of the cookie checked? 
	- If not You can write a cookie to a subpath and it will append that to the request
- Is cookie reflected in URL GET parameter?

--------

**IDOR**

*Tips*
- Try directly going to objects that you have no right to that are on the same level of authentication as the user
- Try directly going to objects that you have no right to that are on a higher level of authentication as the user
- Try directly going to objects that you have no right to that are from a different client in the system

*video's*
- https://www.youtube.com/watch?v=hZ0xSRswN8M
- https://www.youtube.com/watch?v=mjrGOuFc1Kw
- https://www.youtube.com/watch?v=5vYhTik8_yU
- https://www.youtube.com/watch?v=HQUxXE1oaIE

--------

**SSTI**

*Tips*
- Try to inject }}{{7*7}}
- Try to inject }}[[7*7]]

*video's*
- https://www.youtube.com/watch?v=iQ6FuL-DgX8
- https://www.youtube.com/watch?v=i8cvh0u-VXE

--------

**XXE**

*Tips*
- For every XML input you see, try XXE

*video's*
- https://www.youtube.com/watch?v=AQUHzyzZXeA
- https://www.youtube.com/watch?v=unS3xGZj8xk
- https://www.youtube.com/watch?v=EwsW2WfUTmQ

--------

**Chaining XSS**

*Tips*
- Maybe use XSS to steal non httpOnly cookie?
- Maybe use XSS to overwrite cookie on different path?
- Maybe use session that never changes togheter with xss to steal cookie for eternal account takeover (+ severity)
- Maybe use XSS to steal info displayed on the page (GDPR issue - PILL data)

*Videos*
- https://www.youtube.com/watch?v=5vYhTik8_yU
- https://www.youtube.com/watch?v=unS3xGZj8xk

--------

**Chaining CSRF**

*Tips*
- Maybe use a CSRF to make someone insert XSS on their own page?

--------

**Chaining IDOR**

*Tips*
- Sometimes, programs use UUID's (1213804129abc80823213214) and you find an IDOR on it. It will be low impact because you can't easily guess this id. maybe you can find an endpoint that displays all the UUID's? 

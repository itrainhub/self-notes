
## CSRF (跨站点脚本攻击)

防止 CSRF 的几种方式

1. Using a secret cookie
  Remember that all cookies, even the secret ones, will be submitted with every request. All authentication tokens will be submitted regardless of whether or not the end-user was tricked into submitting the request. Furthermore, session identifiers are simply used by the application container to associate the request with a specific session object. The session identifier does not verify that the end-user intended to submit the request.

2. Only accepting POST requests
  Applications can be developed to only accept POST requests for the execution of business logic. The misconception is that since the attacker cannot construct a malicious link, a CSRF attack cannot be executed. Unfortunately, this logic is incorrect. There are numerous methods in which an attacker can trick a victim into submitting a forged POST request, such as a simple form hosted in an attacker's Website with hidden values. This form can be triggered automatically by JavaScript or can be triggered by the victim who thinks the form will do something else.

  A number of flawed ideas for defending against CSRF attacks have been developed over time. Here are a few that we recommend you avoid.

3. Multi-Step Transactions
  Multi-Step transactions are not an adequate prevention of CSRF. As long as an attacker can predict or deduce each step of the completed transaction, then CSRF is possible.

4. URL Rewriting
  This might be seen as a useful CSRF prevention technique as the attacker cannot guess the victim's session ID. However, the user’s session ID is exposed in the URL. We don't recommend fixing one security flaw by introducing another.

5. HTTPS

6. token
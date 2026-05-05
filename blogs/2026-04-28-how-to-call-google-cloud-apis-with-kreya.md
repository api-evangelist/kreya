---
title: "How to call Google Cloud APIs with Kreya"
url: "https://kreya.app/blog/how-to-call-google-cloud-apis/"
date: "Tue, 28 Apr 2026 00:00:00 GMT"
author: ""
feed_url: "https://kreya.app/blog/rss.xml"
---
<p>In this post, we'll show you how to use Kreya to automate the Google Cloud authentication flow,
allowing you to call Google Cloud Platform services effortlessly.</p>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="setting-up-authentication-in-kreya">Setting up authentication in Kreya<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#setting-up-authentication-in-kreya" title="Direct link to Setting up authentication in Kreya">​</a></h2>
<p>One of the major benefits of Kreya is that authentication is built into the core of the app.
Instead of manually adding <code>Authorization: Bearer ...</code> headers to every request,
you define a Google Cloud authentication configuration once and reuse it throughout your project.</p>
<p>Navigate in Kreya to the <strong>Project</strong> menu and select <strong>Authentications</strong> (or use the shortcut <kbd>Ctrl</kbd><span>+</span><kbd>⇧</kbd><span>+</span><kbd>a</kbd>).</p>
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="google-cloud-authentication-types">Google Cloud authentication types<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#google-cloud-authentication-types" title="Direct link to Google Cloud authentication types">​</a></h3>
<p>Kreya supports different ways to authenticate against Google Cloud,
depending on whether you are acting as a system (Service Account) or a developer (User).</p>
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="service-account-authentication">Service Account Authentication<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#service-account-authentication" title="Direct link to Service Account Authentication">​</a></h3>
<p>When you need to test with a specific set of permissions or simulate a backend-to-backend call, using a <strong>Service Account</strong> is the way to go.</p>
<p>If you don't have a service account yet, you can go to the <a href="https://console.cloud.google.com/" rel="noopener noreferrer" target="_blank">Google Cloud Console</a>, and navigate to <strong>IAM &amp; Admin &gt; Service Accounts</strong> (a project is required).<br />
<!-- -->You can use an existing service account (which already has the necessary permissions), or create a new one.</p>
<img alt="Google Cloud service accounts overview" src="https://kreya.app/blogposts/calling-google-apis/gcloud-iam-service-accounts-1.png" />
<p>If you create a new one, make sure it has the necessary roles to send API requests to the service you want to test.</p>
<img alt="Google Cloud service account roles" src="https://kreya.app/blogposts/calling-google-apis/gcloud-iam-service-accounts-2.png" />
<p>To view the "login key" of a service account, click on the service account, then go to the <strong>Keys</strong> tab.<br />
<!-- -->To create a new key click <strong>Add key</strong> and select key type <strong>JSON</strong>.</p>
<p>After generating the key, the JSON file will automatically be downloaded to your computer (this is the only copy!).</p>
<img alt="Google Cloud service account key and key auto-download" src="https://kreya.app/blogposts/calling-google-apis/gcloud-iam-service-accounts-4.png" />
<p>Move this JSON file to a secure location and note the path, as you'll need it to configure the Kreya authentication:</p>
<table><thead><tr><th>Property</th><th>Value</th></tr></thead><tbody><tr><td><strong>Type</strong></td><td>Google Service Account</td></tr><tr><td><strong>Key file (json)</strong></td><td><code>PATH_TO_KEY_JSON_FILE</code></td></tr><tr><td><strong>Scope</strong></td><td><a href="https://developers.google.com/identity/protocols/oauth2/scopes?hl=de" rel="noopener noreferrer" target="_blank">See https://developers.google.com/identity/protocols/oauth2/scopes</a></td></tr></tbody></table>
<p>It should look similar to this:</p>
<img alt="Kreya Google Service Account config" src="https://kreya.app/blogposts/calling-google-apis/kreya-gcloud-service-account.png" />
<div class="theme-admonition theme-admonition-note admonition_xJq3 alert alert--secondary"><div class="admonitionHeading_Gvgb"><span class="admonitionIcon_Rf37"><svg viewBox="0 0 14 16" xmlns="http://www.w3.org/2000/svg"><path d="M6.3 5.69a.942.942 0 0 1-.28-.7c0-.28.09-.52.28-.7.19-.18.42-.28.7-.28.28 0 .52.09.7.28.18.19.28.42.28.7 0 .28-.09.52-.28.7a1 1 0 0 1-.7.3c-.28 0-.52-.11-.7-.3zM8 7.99c-.02-.25-.11-.48-.31-.69-.2-.19-.42-.3-.69-.31H6c-.27.02-.48.13-.69.31-.2.2-.3.44-.31.69h1v3c.02.27.11.5.31.69.2.2.42.31.69.31h1c.27 0 .48-.11.69-.31.2-.19.3-.42.31-.69H8V7.98v.01zM7 2.3c-3.14 0-5.7 2.54-5.7 5.68 0 3.14 2.56 5.7 5.7 5.7s5.7-2.55 5.7-5.7c0-3.15-2.56-5.69-5.7-5.69v.01zM7 .98c3.86 0 7 3.14 7 7s-3.14 7-7 7-7-3.12-7-7 3.14-7 7-7z" fill-rule="evenodd"></path></svg></span>note</div><div class="admonitionContent_BuS1"><p>You can use environment variables like <code>{{ env.gcp.keyPath }}</code> to point to your JSON key.
This keeps your project configuration portable and prevents you from hardcoding absolute paths that might differ between team members.</p></div></div>
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="user-authentication-oauth2--openid-connect">User Authentication (OAuth2 / OpenID-Connect)<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#user-authentication-oauth2--openid-connect" title="Direct link to User Authentication (OAuth2 / OpenID-Connect)">​</a></h3>
<p>If you want to login with a specific user (which has permissions to access the API), you can use the Kreya authentication type
<code>OAuth2 / OpenID-Connect</code>.</p>
<p>You need to setup a <strong>OAuth 2.0 Client ID</strong> credential in the Google Cloud Console.<br />
<!-- -->If you don't have one yet, navigate to <strong>API &amp; Services &gt; Credentials</strong> and create one.</p>
<img alt="Google Cloud credentials overview" src="https://kreya.app/blogposts/calling-google-apis/gcloud-oauth-1.png" />
<p>You can find the <strong>Client ID</strong> and <strong>Client secret</strong> in the credential details.</p>
<div class="theme-admonition theme-admonition-note admonition_xJq3 alert alert--secondary"><div class="admonitionHeading_Gvgb"><span class="admonitionIcon_Rf37"><svg viewBox="0 0 14 16" xmlns="http://www.w3.org/2000/svg"><path d="M6.3 5.69a.942.942 0 0 1-.28-.7c0-.28.09-.52.28-.7.19-.18.42-.28.7-.28.28 0 .52.09.7.28.18.19.28.42.28.7 0 .28-.09.52-.28.7a1 1 0 0 1-.7.3c-.28 0-.52-.11-.7-.3zM8 7.99c-.02-.25-.11-.48-.31-.69-.2-.19-.42-.3-.69-.31H6c-.27.02-.48.13-.69.31-.2.2-.3.44-.31.69h1v3c.02.27.11.5.31.69.2.2.42.31.69.31h1c.27 0 .48-.11.69-.31.2-.19.3-.42.31-.69H8V7.98v.01zM7 2.3c-3.14 0-5.7 2.54-5.7 5.68 0 3.14 2.56 5.7 5.7 5.7s5.7-2.55 5.7-5.7c0-3.15-2.56-5.69-5.7-5.69v.01zM7 .98c3.86 0 7 3.14 7 7s-3.14 7-7 7-7-3.12-7-7 3.14-7 7-7z" fill-rule="evenodd"></path></svg></span>note</div><div class="admonitionContent_BuS1"><p>The <strong>Client secret</strong> has to be copied during the credential or secret creation.</p></div></div>
<img alt="Google Cloud Client ID details" src="https://kreya.app/blogposts/calling-google-apis/gcloud-oauth-2.png" />
<p>The user which signs in, also needs to have the necessary roles to access the API.<br />
<!-- -->This can be verified in the <strong>IAM &amp; Admin &gt; IAM</strong>
section of the Google Cloud Console.</p>
<img alt="Google Cloud User permissions" src="https://kreya.app/blogposts/calling-google-apis/gcloud-iam-test-user-2.png" />
<p>If everything is setup correctly, you can use the following configuration in Kreya to authenticate with Google Cloud:</p>
<table><thead><tr><th>Property</th><th>Value</th></tr></thead><tbody><tr><td><strong>Type</strong></td><td>OAuth2 / OpenID-Connect</td></tr><tr><td><strong>Grant type</strong></td><td>Authorization code</td></tr><tr><td><strong>Issuer</strong></td><td><a href="https://accounts.google.com/" rel="noopener noreferrer" target="_blank">https://accounts.google.com</a></td></tr><tr><td><strong>Client Authorize Method</strong></td><td>Basic</td></tr><tr><td><strong>Client-ID</strong></td><td><code>#GOOGLE_OAUTH_CLIENT_ID</code> (can be found in the Google Auth Platform client info)</td></tr><tr><td><strong>Client-Secret</strong></td><td><code>#GOOGLE_OAUTH_CLIENT_SECRET</code> (can be found in the Google Auth Platform client info)</td></tr><tr><td><strong>Use native browser</strong></td><td>Check (optional)</td></tr><tr><td><strong>Scope</strong></td><td><a href="https://developers.google.com/identity/protocols/oauth2/scopes?hl=de" rel="noopener noreferrer" target="_blank">See https://developers.google.com/identity/protocols/oauth2/scopes</a></td></tr><tr><td><strong>Token-Type to authorize on APIs</strong></td><td>Access-Token</td></tr></tbody></table>
<p>It should look similar to this:</p>
<img alt="Kreya Googe OAuth 2.0 config" src="https://kreya.app/blogposts/calling-google-apis/kreya-gcloud-user.png" />
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="invoking-the-request">Invoking the request<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#invoking-the-request" title="Direct link to Invoking the request">​</a></h3>
<p>To use your new Google Cloud authentication configuration, go to the <strong>Auth</strong> tab of your request and select the configuration.</p>
<img alt="Kreya Auth Configuration selection" src="https://kreya.app/blogposts/calling-google-apis/kreya-auth-update-1.png" />
<p>To explicitly fetch a token, click the <strong>Update</strong> Button.<br />
<!-- -->Kreya handles the background communication with Google's authentication servers. If the retrieval is successful, you'll see the token and its expiry date.</p>
<img alt="Kreya Auth refresh" src="https://kreya.app/blogposts/calling-google-apis/kreya-auth-update-2.png" />
<p>Depending on your authentication configuration, it will directly fetch the token or open your browser, where you can login with an authorized user.</p>
<p>If the retrieval is successful, Kreya displays the JWT and its expiry date directly in the UI. You don't need to re-authenticate for every request,
Kreya caches the token and automatically includes it in the request.</p>
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="examples">Examples<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#examples" title="Direct link to Examples">​</a></h3>
<p>In this section, we'll call different Google Cloud APIs using Kreya with the authentication configuration we set up in the previous sections.</p>
<p>As an improvement, we have moved several Google Cloud values to the Kreya environment variables,
so that we can reuse them across multiple requests and easily switch between different Google Cloud projects.</p>
<img alt="Kreya Auth refresh" src="https://kreya.app/blogposts/calling-google-apis/env-1.png" />
<img alt="Kreya Auth refresh" src="https://kreya.app/blogposts/calling-google-apis/env-2.png" />
<h4 class="anchor anchorWithStickyNavbar_LWe7" id="google-cloud-compute-engine-api">Google Cloud Compute Engine API<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#google-cloud-compute-engine-api" title="Direct link to Google Cloud Compute Engine API">​</a></h4>
<p>Lists all Google Cloud Compute Engine instances of the project.</p>
<p>Endpoint:<br />
<code>https://compute.googleapis.com/compute/v1/projects/{{env.gcp.projectId}}/zones/{{env.gcp.zone}}/instances</code></p>
<img alt="Kreya Auth refresh" src="https://kreya.app/blogposts/calling-google-apis/gcloud-example-1.png" />
<h4 class="anchor anchorWithStickyNavbar_LWe7" id="google-cloud-run-api">Google Cloud Run API<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#google-cloud-run-api" title="Direct link to Google Cloud Run API">​</a></h4>
<p>Lists all Google Cloud Run services of the project.</p>
<p>Endpoint:<br />
<code>https://run.googleapis.com/apis/serving.knative.dev/v1/namespaces/{{env.gcp.projectId}}/services</code></p>
<img alt="Kreya Auth refresh" src="https://kreya.app/blogposts/calling-google-apis/gcloud-example-2.png" />
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="pro-tip-set-the-auth-per-directory-settings">Pro tip: Set the auth per directory settings<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#pro-tip-set-the-auth-per-directory-settings" title="Direct link to Pro tip: Set the auth per directory settings">​</a></h3>
<p>Instead of manually assigning the authentication configuration to every single request, you can use <strong>Directory settings</strong>.</p>
<p>By setting the authentication at the directory level, all requests within that directory and its subdirectories will automatically inherit those credentials.</p>
<img alt="Kreya Auth per Directory Settings" src="https://kreya.app/blogposts/calling-google-apis/directory-settings.png" />
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="conclusion">Conclusion<a class="hash-link" href="https://kreya.app/blog/how-to-call-google-cloud-apis/#conclusion" title="Direct link to Conclusion">​</a></h2>
<p>Testing Google Cloud APIs doesn't have to be a manual burden involving the terminal and copy-pasting long strings.<br />
<!-- -->By using Kreya's native Google Cloud and OAuth support, you can automate token retrieval and focus on building your services.</p>
<p>Whether you're querying the Cloud Storage API or testing Google Cloud Platform backend calls,
Kreya's automated token management makes your development workflow significantly smoother.</p>
<p><strong>Ready to try it out?</strong> <a href="https://kreya.app/downloads/" rel="noopener noreferrer" target="_blank">Download Kreya</a> today and start testing your Google Cloud services the easy way.</p>

---
title: "Kreya 1.19 and 1.19.1 - What's New"
url: "https://kreya.app/blog/kreya-1.19-whats-new/"
date: "Wed, 25 Feb 2026 00:00:00 GMT"
author: ""
feed_url: "https://kreya.app/blog/rss.xml"
---
<p>Kreya 1.19 is here, and in the meantime we have already released 1.19.1. Together they bring GraphQL, OAuth 2.0 Device Flow, and a set of polish improvements across the CLI and UI.</p>
<div class="blog-cover"><svg height="209" width="400" xmlns="http://www.w3.org/2000/svg"></svg><noscript><img alt="Kreya 1.19 thumbnail" height="209" src="/assets/ideal-img/kreya-1-19.2e48be9.400.png" width="400" /></noscript></div>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="graphql-support">GraphQL support<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#graphql-support" title="Direct link to GraphQL support">​</a></h2>
<p>GraphQL operations allow you to execute queries, mutations, and subscriptions against a GraphQL API.
Add a new operation by clicking the <svg class="svg-inline--fa fa-plus" viewBox="0 0 448 512" xmlns="http://www.w3.org/2000/svg"><path d="M256 80c0-17.7-14.3-32-32-32s-32 14.3-32 32l0 144L48 224c-17.7 0-32 14.3-32 32s14.3 32 32 32l144 0 0 144c0 17.7 14.3 32 32 32s32-14.3 32-32l0-144 144 0c17.7 0 32-14.3 32-32s-14.3-32-32-32l-144 0 0-144z" fill="currentColor"></path></svg> icon. Next, choose a descriptive name for your operation and hit enter.</p>
<img alt="An animation showcasing creating a GraphQL operation" class="mx-auto" src="https://kreya.app/whats-new/1.19/create_graphql_operation.gif" />
<p>You can also enter variables for your query in the "Variables" tab in JSON format.
These variables can be used in your query with the <code>$</code> prefix (e.g. <code>$bookId</code>).</p>
<div><svg height="221" width="400" xmlns="http://www.w3.org/2000/svg"></svg><noscript><img alt="GraphQL operation variables" height="221" src="/assets/ideal-img/graphql_variables.588b29c.400.png" width="400" /></noscript></div>
<p>If you don't have a GraphQL API yet, you can experiment with some GraphQL operations in our example project, which you can pull from <a href="https://github.com/riok/Kreya" rel="noopener noreferrer" target="_blank">GitHub</a>.</p>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="oauth-20-device-flow">OAuth 2.0 Device Flow<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#oauth-20-device-flow" title="Direct link to OAuth 2.0 Device Flow">​</a></h2>
<p>We have added support for the <a href="https://oauth.net/2/device-flow/" rel="noopener noreferrer" target="_blank">OAuth 2.0 Device Authorization Grant</a> (formerly known as the Device Flow) that enables devices with no browser or limited input capability to obtain an access token.
To use this, create a new authentication in <code>Project &gt; Authentication</code> and select the Grant type <code>Device code</code>.</p>
<div><svg height="250" width="400" xmlns="http://www.w3.org/2000/svg"></svg><noscript><img alt="Device Flow auth configuration" height="250" src="/assets/ideal-img/device_flow.3661e56.400.png" width="400" /></noscript></div>
<p>You can then choose this new authentication for an operation. Pressing the <code>Update</code> button will start the Device Flow.</p>
<img alt="An animation showcasing using the new device flow auth" class="mx-auto" src="https://kreya.app/whats-new/1.19/device_flow.gif" />
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="ui-improvements">UI improvements<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#ui-improvements" title="Direct link to UI improvements">​</a></h2>
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="recent-projects-are-searchable">Recent projects are searchable<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#recent-projects-are-searchable" title="Direct link to Recent projects are searchable">​</a></h3>
<p>You can now search for recent projects in the launch window.
Start typing the name of the project you are looking for, and a list of matching projects will appear.</p>
<img alt="An animation showcasing searching for recent projects" class="mx-auto" src="https://kreya.app/whats-new/1.19/recent_projects_searchable.gif" />
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="create-a-new-project">Create a new project<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#create-a-new-project" title="Direct link to Create a new project">​</a></h3>
<p>You can now create a new project directly from the application menu.
Select <code>Kreya &gt; New project...</code> and enter the necessary project information.</p>
<img alt="An animation showcasing creating a new project" class="mx-auto" src="https://kreya.app/whats-new/1.19/create_new_project.gif" />
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="importer-type-selection">Importer type selection<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#importer-type-selection" title="Direct link to Importer type selection">​</a></h3>
<p>The process of selecting an importer type has been simplified.
Choose your type at the top of the page and enter the required importer information.</p>
<img alt="An animation showcasing selecting the importer type" class="mx-auto" src="https://kreya.app/whats-new/1.19/importer_type_selection.gif" />
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="operation-actions">Operation actions<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#operation-actions" title="Direct link to Operation actions">​</a></h3>
<p>We have moved all operation-related actions into the operation header.
Actions such as 'Change gRPC method', 'Reset operation' and 'History' can now be found there.</p>
<img alt="An animation showcasing using the new operation actions" class="mx-auto" src="https://kreya.app/whats-new/1.19/operation_actions.gif" />
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="inline-create-operation">Inline create operation<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#inline-create-operation" title="Direct link to Inline create operation">​</a></h3>
<p>We have optimized the process of creating an operation in Kreya. First, you enter the name, and then you can select the gRPC method in the operation header.</p>
<img alt="An animation showcasing creating an gRPC operation inline" class="mx-auto" src="https://kreya.app/whats-new/1.19/inline_create_operation_grpc.gif" />
<p>The same applies to REST operations if you have imported API definitions. You can also select a template in the operation header.</p>
<img alt="An animation showcasing creating an REST operation inline" class="mx-auto" src="https://kreya.app/whats-new/1.19/inline_create_operation_rest.gif" />
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="insomnia-collection-v5-import-support">Insomnia collection v5 import support<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#insomnia-collection-v5-import-support" title="Direct link to Insomnia collection v5 import support">​</a></h2>
<p>We have added support for importing Insomnia collection v5 files.
In the application menu, select <code>Kreya &gt; Import</code>, then select <code>Insomnia collection (v5)</code> and your file.</p>
<img alt="An animation showcasing importing an Insomnia collection v5" class="mx-auto" src="https://kreya.app/whats-new/1.19/insomnia_collection_v5_import.gif" />
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="and-more">And more<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#and-more" title="Direct link to And more">​</a></h2>
<p>There are other notable improvements:</p>
<ul>
<li>gRPC v1 reflection support in addition to v1alpha</li>
<li>Session cookies support</li>
<li>Simplified test scripting</li>
</ul>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="kreya-1191">Kreya 1.19.1<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#kreya-1191" title="Direct link to Kreya 1.19.1">​</a></h2>
<p>Version 1.19.1 focuses on polish and quality-of-life improvements across the CLI, UI, and platform integrations.</p>
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="cli">CLI<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#cli" title="Direct link to CLI">​</a></h3>
<ul>
<li>Added the <code>--relative-to</code> option for CLI path resolution relative to the project or current working directory. See <a href="https://kreya.app/docs/cli/path-globs/#relative-path-resolution">relative path resolution</a>.</li>
<li>Added the filename to the JUnit reporter output</li>
<li>Automatically detect Kreya projects in parent directories</li>
<li>Show correct default values in the CLI help output</li>
</ul>
<h3 class="anchor anchorWithStickyNavbar_LWe7" id="kreya-ui">Kreya UI<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#kreya-ui" title="Direct link to Kreya UI">​</a></h3>
<ul>
<li>gRPC: Improved fallback to the v1alpha server reflection importer</li>
<li>Added a <code>Copy as kreyac</code> option to the operation context menu to copy the operation as a kreyac command.</li>
<li>Added quick actions to open settings tabs, clear all cookies and clear all user variables</li>
<li>Added a word wrap option to all editors with horizontal scrolling</li>
</ul>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="release-notes-and-feedback">Release notes and feedback<a class="hash-link" href="https://kreya.app/blog/kreya-1.19-whats-new/#release-notes-and-feedback" title="Direct link to Release notes and feedback">​</a></h2>
<p>For a full list of new features and bugfixes, see the <a href="https://kreya.app/docs/release-notes/">release notes</a>.</p>
<p>If you have feedback or questions, please <a href="mailto:hello@kreya.app" rel="noopener noreferrer" target="_blank">contact us</a> or <a href="https://github.com/riok/Kreya/issues/new/choose" rel="noopener noreferrer" target="_blank">report an issue</a>.</p>
<p>Stay tuned! 🚀</p>

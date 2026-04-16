---


---

<h2 id="project-overview">1. Project Overview</h2>
<p><strong>ODC Corner</strong> is a learning management Mini Program hosted inside the <strong>Maxit Super App</strong> — Liberia’s home-grown super app platform built on a WeChat-compatible Mini Program runtime. ODC Corner enables learners across Liberia and West Africa to discover open development courses, submit applications, track their progress, and earn certificates — all without leaving Maxit.</p>
<p>Administrators get a fully featured dashboard to publish courses, manage the applicant pipeline, and access SAS-powered analytics on enrollment trends and learner outcomes.</p>
<h3 id="strategic-goals">Strategic Goals</h3>

<table>
<thead>
<tr>
<th>Goal</th>
<th>Detail</th>
</tr>
</thead>
<tbody>
<tr>
<td>Zero friction discovery</td>
<td>Users find ODC Corner in the Maxit Mini Program store — no extra app install</td>
</tr>
<tr>
<td>Leverage Maxit identity</td>
<td>Maxit SSO removes the sign-up barrier; users are authenticated in one tap</td>
</tr>
<tr>
<td>Mobile-first for West Africa</td>
<td>All screens designed for low-end Android devices and intermittent connectivity</td>
</tr>
<tr>
<td>Data-driven administration</td>
<td>SAS pipelines process application data; Viya reports surface insights to admins</td>
</tr>
<tr>
<td>Scalable content publishing</td>
<td>Admins can create, publish, and retire courses with no engineering involvement</td>
</tr>
</tbody>
</table><h3 id="tech-stack">Tech Stack</h3>

<table>
<thead>
<tr>
<th>Layer</th>
<th>Technology</th>
</tr>
</thead>
<tbody>
<tr>
<td>Mini Program Runtime</td>
<td>Maxit Super App (WXML / WXSS / JS — WeChat-compatible)</td>
</tr>
<tr>
<td>State Management</td>
<td>Mini Program <code>globalData</code> + local <code>Storage</code> API</td>
</tr>
<tr>
<td>Backend API</td>
<td>Tencent CVM — Node.js REST API</td>
</tr>
<tr>
<td>Database</td>
<td>TencentDB for MySQL</td>
</tr>
<tr>
<td>File Storage</td>
<td>Tencent COS (course materials, profile images, certificates)</td>
</tr>
<tr>
<td>CDN</td>
<td>Tencent CDN (static assets, thumbnails)</td>
</tr>
<tr>
<td>Auth</td>
<td>Maxit SSO (maxit.login() token exchange) + JWT</td>
</tr>
<tr>
<td>Analytics Engine</td>
<td>SAS Viya — pipelines + embedded reports</td>
</tr>
<tr>
<td>CI/CD</td>
<td>Tencent CODING DevOps</td>
</tr>
<tr>
<td>Notifications</td>
<td>Maxit Subscription Message API (like WeChat template messages)</td>
</tr>
</tbody>
</table><hr>
<h2 id="platform-context-—-maxit-super-app">2. Platform Context — Maxit Super App</h2>
<h3 id="what-this-means-for-odc-corner">What This Means for ODC Corner</h3>
<p>Maxit is a super app built on the same foundational paradigm as WeChat — a host app that runs sandboxed Mini Programs using a WXML/WXSS/JS rendering engine. ODC Corner is one Mini Program within that ecosystem.</p>
<h3 id="key-platform-constraints--advantages">Key Platform Constraints &amp; Advantages</h3>

<table>
<thead>
<tr>
<th>Aspect</th>
<th>Detail</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>File size limit</strong></td>
<td>Mini Program package ≤ 2MB main package; subpackages supported up to 20MB total</td>
</tr>
<tr>
<td><strong>Navigation</strong></td>
<td>Stack-based page router — <code>maxit.navigateTo</code>, <code>maxit.redirectTo</code>, <code>maxit.switchTab</code></td>
</tr>
<tr>
<td><strong>Network</strong></td>
<td>All API calls via <code>maxit.request()</code> — HTTPS only; domain whitelisting required</td>
</tr>
<tr>
<td><strong>Storage</strong></td>
<td>Local storage via <code>maxit.setStorage()</code> — max 10MB per Mini Program</td>
</tr>
<tr>
<td><strong>Auth</strong></td>
<td><code>maxit.login()</code> returns a code; backend exchanges it for user identity via Maxit OAuth server</td>
</tr>
<tr>
<td><strong>Payments</strong></td>
<td>Maxit Pay API available (future phase)</td>
</tr>
<tr>
<td><strong>Notifications</strong></td>
<td>Subscription Messages — user opts in; admin can push templated notifications</td>
</tr>
<tr>
<td><strong>Camera / Files</strong></td>
<td><code>maxit.chooseImage()</code>, <code>maxit.uploadFile()</code> — used for profile photo and document uploads</td>
</tr>
<tr>
<td><strong>Share</strong></td>
<td>Users can share ODC Corner pages as cards within Maxit chats</td>
</tr>
<tr>
<td><strong>Discovery</strong></td>
<td>Searchable in Maxit Mini Program store; shareable via Maxit chat links</td>
</tr>
</tbody>
</table><h3 id="liberia--west-africa-ux-considerations">Liberia / West Africa UX Considerations</h3>

<table>
<thead>
<tr>
<th>Consideration</th>
<th>Design Response</th>
</tr>
</thead>
<tbody>
<tr>
<td>Low-end Android devices prevalent</td>
<td>Minimal animations; avoid heavy CSS effects; test on 2GB RAM devices</td>
</tr>
<tr>
<td>Intermittent 3G/4G connectivity</td>
<td>Aggressive local caching; graceful offline states; skeleton loaders</td>
</tr>
<tr>
<td>WhatsApp-first mental model</td>
<td>Familiar card-based UI patterns; bottom tab navigation like mobile apps</td>
</tr>
<tr>
<td>Low WeChat familiarity</td>
<td>Clear onboarding flow explaining Maxit Mini Programs</td>
</tr>
<tr>
<td>English primary language</td>
<td>English UI with future French localisation hooks</td>
</tr>
</tbody>
</table><hr>


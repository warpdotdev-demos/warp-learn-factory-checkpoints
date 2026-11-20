---
triggers:
  - provider: github
    event: issue_labeled
    filter:
      repos: [YOUR_GITHUB_ORG/my-markdown-app]
      labels: [factory]
      skip_bots: self
---
Use the issue that triggered this run as the request:

- author: the requester
- URL: the issue this work tracks; link the pull request on it
- title / body: the description to follow

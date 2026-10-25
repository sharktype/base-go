# base-go

> **Warning**: This repository is not ready for use and should be ignored for now.

## Template

This template already defines a decent production-capable Go API. You will probably want to first
replace all instances of the "base-go" string. It is designed to live alongside other root-level
directories in a monorepo.

First easy find-replace:

```sh
grep -rlE 'github\.com/sharktype/base-go' go \
    --include='*.go' --include='*.mod' --include='*.yml' \
    | xargs sed -i \
        's|github.com/sharktype/base-go|github.com/<org-or-user>/<repo>|g'
```

As with most templates, you'll need to do some significant "massaging" of the source to get it to
work for you. For example, the auth is with a separate IDP by default, and you must have a database
configured, or the app won't even start.

### Why doesn't it have...?

- Emails/messaging: not used often enough, and best as a worker.
- Task queues: Implementations widely differ (River, etc.) and are usually complex architecture.
  You should be diligent to implement this yourself, and copy that implementation, if applicable,
  directly to any other Go services you write.
- Redis: YAGNI at initial request volume. I may implement this in the future.
- Less of a coupling to Sentry: because I personally use Sentry, and I think most people should
  use it rather than expensive observability platforms while starting. I may implement this in the
  future.

Updates to this will be applied retroactively as my applications start to use them.

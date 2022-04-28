This cop suggests `ENV.fetch` for the replacement of `ENV[]`.
`ENV[]` silently fails and returns `nil` when the environment variable is unset,
which may cause unexpected behaviors when the developer forgets to set it.
On the other hand, `ENV.fetch` raises KeyError or returns the explicitly
specified default value.

### Example:
    # bad
    ENV['X']
    ENV['X'] || z
    x = ENV['X']

    # good
    ENV.fetch('X')
    ENV.fetch('X', nil) || z
    x = ENV.fetch('X')

    # also good
    !ENV['X']
    ENV['X'].some_method # (e.g. `.nil?`)
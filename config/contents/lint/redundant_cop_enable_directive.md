# The Lint/RedundantCopEnableDirective cop needs to be disabled so as
# to be able to provide a (bad) example of an unneeded enable.
# rubocop:disable Lint/RedundantCopEnableDirective
This cop detects instances of rubocop:enable comments that can be
removed.

When comment enables all cops at once `rubocop:enable all`
that cop checks whether any cop was actually enabled.
### Example:
    # bad
    foo = 1
    # rubocop:enable Layout/LineLength

    # good
    foo = 1
### Example:
    # bad
    # rubocop:disable Style/StringLiterals
    foo = "1"
    # rubocop:enable Style/StringLiterals
    baz
    # rubocop:enable all

    # good
    # rubocop:disable Style/StringLiterals
    foo = "1"
    # rubocop:enable all
    baz
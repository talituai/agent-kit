# `tests/`: example-set tests

Runs each skill on every case under its `examples/` folder and scores the output against the
expected draft or action. A new skill version is published only when it scores at least as
well as the current one (kit rule 8).

Tests here use no real workspace data and no credentials beyond the model call the test
itself makes with the person's own key, against a non-production workspace.

State: skeleton. Built by the platform's T7.

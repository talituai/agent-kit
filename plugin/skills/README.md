# `plugin/skills/`: one folder per job

```text
plugin/skills/lead-magnet/
  SKILL.md            the job, its inputs, its rules and the operations it calls; short (kit rule 9)
  references/         longer rules and examples of good output, opened only when SKILL.md says
  templates/          starting definitions the skill fills in
  examples/           made-up briefs with the draft each should produce
```

A skill reads the workspace's forms, routes, brand and sources from the platform through the
`talitu` command or the MCP tools, never from files in the kit (kit rule 3). It may call
exactly the operations its `SKILL.md` names. Its examples are made up (kit rule 1). A skill
that generates a form returns a draft and publishes only on the person's approval (kit rule 5).

State: skeleton apart from `using-talitu`, which is written. Built by the platform's T5 and
T7 (`lead-magnet`, `publish`), T9 (`leads`) and T10 and T11 (`connect`).

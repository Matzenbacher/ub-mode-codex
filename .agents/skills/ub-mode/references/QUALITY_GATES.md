# Quality gates and external companions

The upstream `ub-mode` project identifies these tools as companions:

| Check | Original tool | Expected interpretation |
| --- | --- | --- |
| Complexity and test coverage | [unclebob/crapper](https://github.com/unclebob/crapper) | A function should have CRAP score strictly below 10. |
| Similar code blocks | [unclebob/dryer](https://github.com/unclebob/dryer) | Inspect duplication similarity >= 0.8. |
| Mutation testing | [unclebob/mutator](https://github.com/unclebob/mutator) | Investigate surviving mutants; strengthen meaningful tests. |
| Visualization (optional) | [unclebob/uml-viewer](https://github.com/unclebob/uml-viewer) | Inspect components and dependency/quality visualizations when helpful. |

## Execution and evidence

1. Inspect repository-local scripts, installed tools and the tool's current
   documentation before deciding on the exact command.
2. Do **not** assume any of these binaries or commands already exist. Do not
   invent invocation syntax.
3. Run each available, compatible tool on the affected scope (or an
   appropriately representative scope). Save or summarize the actual output.
4. If installation is needed, follow the user's permission and environment
   constraints. Avoid adding global dependencies without authorization.
5. Compare measured output to the gate, record exceptions with reasons, and
   repair the code where the metric reveals a real issue.
6. When a gate is unavailable or inapplicable, write `not run` with the
   specific reason. A conventional lint/test pass is not the same thing as a
   CRAP/duplication/mutation measurement.

The upstream skill provides principles and tool references, **not** tool
executables, credentials, MCP endpoints or guaranteed support across languages.

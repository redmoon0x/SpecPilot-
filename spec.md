---
description: Replicates GitHub Spec Kit for spec-driven AI development
globs:
alwaysApply: true
---

# Spec-Driven Development Rule (GitHub Spec Kit Replication)

## Core Philosophy

- **Specifications as the Lingua Franca**: The specification is the primary artifact. Code is its expression in a particular language and framework.
- **Executable Specifications**: Specifications must be precise, complete, and unambiguous enough to generate working systems.
- **Continuous Refinement**: Consistency validation happens continuously, not as a one-time gate.
- **Research-Driven Context**: Research agents gather critical context throughout the specification process.
- **Bidirectional Feedback**: Production reality informs specification evolution.
- **Branching for Exploration**: Generate multiple implementation approaches from the same specification.

## Storage Convention (NON-NEGOTIABLE)

1. **Every specification artifact lives inside `.SpecPilot/` at the repository root.**  
   - Do **not** create `spec.md`, `plan.md`, `tasks.md` (or any variant) in the public folder.  
   - If `.SpecPilot/` does not exist, create it silently before writing any file.

2. **All three artifacts are mandatory before code is touched.**  
   After `/specify`, `/plan`, and `/tasks` have been executed, the following files must exist:  
   - `.SpecPilot/spec.md`  
   - `.SpecPilot/plan.md`  
   - `.SpecPilot/tasks.md`  

   The assistant must refuse to generate implementation code until all three files are present and pass their respective quality gates.

## Workflow Commands

### /specify
Generate or refine the specification. Use this command when:
- Starting a new feature or project
- Requirements are unclear or incomplete
- Need to validate understanding of the problem space

**Output**: A detailed specification document that includes:
- Goals and user journeys
- Functional requirements
- Non-functional requirements
- Acceptance criteria
- Edge cases and error handling

**Persisted to**: `.SpecPilot/spec.md`

### /plan
Create a technical plan based on the specification. Use this command after `/specify` to:
- Declare architecture and stack
- Define constraints and standards
- Propose implementation approach
- Identify risks and mitigation strategies

**Output**: A technical plan that includes:
- Architecture overview
- Technology stack justification
- Component breakdown
- Data flow diagrams
- Testing strategy
- Deployment considerations

**Persisted to**: `.SpecPilot/plan.md`

### /tasks
Break the plan into implementable tasks. Use this command after `/plan` to:
- Create small, reviewable units of work
- Define clear acceptance criteria for each task
- Identify dependencies between tasks
- Estimate complexity and effort

**Output**: A task list where each task:
- Is independently implementable
- Has clear success criteria
- Includes test requirements
- References relevant specification sections

**Persisted to**: `.SpecPilot/tasks.md`

## Implementation Guidelines

### Before Writing Code
1. **Research-First**: Never act on assumptions. Investigate the current system state.
2. **Specification Validation**: Ensure the specification is complete and unambiguous.
3. **Plan Adherence**: Verify that the implementation aligns with the technical plan.
4. **Storage Validation**: Confirm `.SpecPilot/spec.md`, `.SpecPilot/plan.md`, and `.SpecPilot/tasks.md` exist and pass their quality gates.

### During Implementation
1. **Task Isolation**: Focus on one task at a time. Complete it fully before moving to the next.
2. **Continuous Validation**: Regularly check that the implementation matches the specification.
3. **Test-Driven**: Write tests that validate the specification requirements, not just the code.

### After Implementation
1. **Specification Evolution**: Update the specification based on implementation learnings.
2. **Documentation**: Ensure the code documents how it fulfills the specification.
3. **Review**: Validate that the implementation meets all acceptance criteria.

## Quality Gates

### Specification Gate
- [ ] Goals are clearly defined
- [ ] User journeys are documented
- [ ] Requirements are measurable
- [ ] Edge cases are identified
- [ ] Acceptance criteria are testable
- [ ] File location: `.SpecPilot/spec.md`

### Planning Gate
- [ ] Architecture supports all requirements
- [ ] Technology choices are justified
- [ ] Risks are identified and mitigated
- [ ] Testing strategy is comprehensive
- [ ] Deployment approach is defined
- [ ] File location: `.SpecPilot/plan.md`

### Task Gate
- [ ] Tasks are independently implementable
- [ ] Each task has clear acceptance criteria
- [ ] Dependencies are identified and managed
- [ ] Tasks are sized appropriately (1-3 days max)
- [ ] Test requirements are included
- [ ] File location: `.SpecPilot/tasks.md`

### Implementation Gate
- [ ] Code implements the specification exactly
- [ ] All tests pass
- [ ] Documentation is updated
- [ ] Performance requirements are met
- [ ] Security considerations are addressed

## Error Handling

### Specification Ambiguity
When the specification is unclear:
1. Stop implementation immediately
2. Use `/specify` to clarify the requirement
3. Get stakeholder approval before proceeding
4. Update `.SpecPilot/spec.md` with the clarification

### Implementation Deviation
When implementation deviates from the specification:
1. Document the deviation and its rationale
2. Update the relevant `.SpecPilot/*.md` files to reflect the new approach
3. Get approval for the change
4. Ensure all dependent tasks are updated

### Technical Constraints
When technical constraints prevent specification implementation:
1. Document the constraint in detail inside `.SpecPilot/plan.md`
2. Propose alternative approaches
3. Update the specification with the approved approach
4. Ensure the solution still meets the core requirements

## Best Practices

### Specification Writing
- Use precise, unambiguous language
- Include concrete examples
- Define all terms and concepts
- Specify behavior for all edge cases
- Make requirements testable

### Planning
- Choose the simplest adequate architecture
- Prefer established patterns and practices
- Consider operational requirements
- Plan for monitoring and observability
- Include security from the start

### Task Definition
- Keep tasks small and focused
- Define clear completion criteria
- Include test requirements
- Identify prerequisites
- Estimate realistically

### Implementation
- Write self-documenting code
- Include comprehensive tests
- Follow established patterns
- Document deviations
- Optimize for readability first

## Anti-Patterns to Avoid

- **Vague Specifications**: "Make it fast" or "User-friendly" without concrete criteria
- **Implementation Without Specification**: Coding before `.SpecPilot/spec.md`, `.SpecPilot/plan.md`, and `.SpecPilot/tasks.md` exist and pass gates
- **Big Bang Implementation**: Trying to implement everything at once
- **Specification Drift**: Allowing implementation to diverge from specification without updating `.SpecPilot/*.md`
- **Testing the Code, Not the Specification**: Writing tests that validate implementation details rather than requirements
- **Public Folder Pollution**: Creating any spec artifact outside `.SpecPilot/`

## Continuous Improvement

### After Each Task
1. Reflect on what went well
2. Identify areas for improvement
3. Update `.SpecPilot/spec.md` with learnings
4. Refine the process for next time

### After Each Project
1. Conduct a retrospective
2. Update this rule with improvements
3. Share learnings with the team
4. Refine templates and patterns

### Metrics to Track
- Specification change frequency
- Task completion rate
- Defect density
- Time to implement
- Stakeholder satisfaction

---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Cursor Skills Workshop
info: |
  ## Cursor Skills Deep Dive
  Learn how to create, manage, and leverage Cursor Skills for enhanced AI-assisted development.

  Learn more at [Cursor Docs](https://cursor.sh/docs)
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# duration of the presentation
duration: 45min
---

# Cursor Skills

Extending AI capabilities with custom workflows

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<!--
Welcome to the Cursor Skills workshop. Today we'll explore how to create and use custom skills in Cursor to enhance your AI-assisted development workflow.

This workshop is designed for intermediate developers who want to extend Cursor's capabilities beyond the default features.

Duration: 45 minutes
-->

---
transition: fade-out
---

# What are Cursor Skills?

Skills are **reusable, documented workflows** that teach Cursor how to perform specific tasks

<div class="grid grid-cols-2 gap-4 mt-8">

<div>

## Key Characteristics

- 📝 **Documented instructions** in markdown
- 🎯 **Task-specific** workflows
- 🔄 **Reusable** across projects
- 📚 **Self-contained** knowledge

</div>

<div>

## Benefits

- Standardize common workflows
- Share expertise with team
- Reduce repetitive prompting
- Improve AI accuracy

</div>

</div>

<!--
Skills are essentially markdown files that contain structured instructions for Cursor to follow when performing specific tasks.

Think of them as "playbooks" or "recipes" that the AI can reference to complete complex or repetitive tasks more accurately.

They're stored in `.cursor/skills/` directory and can be shared across projects or with your team.
-->

---
transition: slide-up
level: 2
---

# Why Skills Matter

Skills bridge the gap between **what you know** and **what Cursor can do**

<div class="mt-6">

## Without Skills

- ❌ Repetitive prompting
- ❌ Inconsistent results
- ❌ Context loss between sessions
- ❌ Team knowledge silos

</div>

<div class="mt-6">

## With Skills

- ✅ Consistent, repeatable workflows
- ✅ Team knowledge sharing
- ✅ Reduced prompt engineering
- ✅ Better AI understanding

</div>

<!--
Skills solve real problems:
1. You don't have to re-explain complex workflows every time
2. Team members can benefit from each other's expertise
3. The AI has better context and produces more accurate results
4. Knowledge is preserved and version-controlled

Time: 3-4 minutes
-->

---
layout: two-cols
layoutClass: gap-16
---

# Skills Structure

Every skill follows a consistent structure

```markdown
---
name: Skill Name
description: Brief description
---

# Skill Title

## When to Use
- Use case 1
- Use case 2

## Instructions
### Step 1
...

## Example
...
```

::right::

## Components

1. **Frontmatter** (YAML)
   - `name`: Display name
   - `description`: Short summary

2. **When to Use**
   - Clear use cases
   - Decision criteria

3. **Instructions**
   - Step-by-step guide
   - Code examples
   - Best practices

4. **Examples**
   - Real-world scenarios
   - Complete workflows

<!--
Skills are markdown files with YAML frontmatter. The structure is flexible but follows a pattern:

1. Frontmatter defines metadata
2. "When to Use" helps the AI (and humans) understand when to apply the skill
3. Instructions provide the actual workflow
4. Examples make it concrete

This structure makes skills both human-readable and AI-parseable.

Time: 4-5 minutes
-->

---
transition: slide-up
---

# When to Use Skills

Skills are perfect for **repetitive, well-defined tasks**

<div class="grid grid-cols-2 gap-6 mt-6">

<div>

## ✅ Good Candidates

- **Complex workflows** with multiple steps
- **Project-specific** patterns
- **Team standards** and conventions
- **Domain knowledge** that needs preservation
- **Multi-file** operations

</div>

<div>

## ❌ Not Ideal For

- One-off tasks
- Highly creative work
- Exploratory coding
- Simple refactoring
- Tasks requiring human judgment

</div>

</div>

<div class="mt-6 text-sm opacity-75">

💡 **Rule of thumb**: If you find yourself explaining the same workflow 3+ times, it's a skill candidate

</div>

<!--
Skills work best when:
- The task has clear steps
- The workflow is repeatable
- Multiple people need to do it
- There are specific patterns or conventions to follow

They're less useful for:
- Creative problem-solving
- Tasks that require exploration
- One-time operations
- Simple tasks that don't need documentation

Time: 3-4 minutes
-->

---
layout: image-right
image: https://images.unsplash.com/photo-1551650975-87deedd944c3?w=800
---

# How Skills Work

Cursor reads skills from `.cursor/skills/` and uses them when relevant

## Process Flow

1. **Detection**: Cursor identifies when a skill might be relevant
2. **Selection**: Chooses appropriate skill(s) based on context
3. **Execution**: Follows skill instructions step-by-step
4. **Verification**: Validates results against skill criteria

## Location

```
.cursor/
  skills/
    skill-name/
      SKILL.md
```

<!--
When you ask Cursor to do something, it:
1. Scans available skills in `.cursor/skills/`
2. Matches your request to skill descriptions
3. Loads relevant skills and follows their instructions
4. Uses the skill's guidance to complete the task

Skills are automatically discovered - you don't need to explicitly reference them.

Time: 3-4 minutes
-->

---
level: 2
---

# Creating Custom Skills

Let's build a skill step-by-step

<div class="mt-6">

## Step 1: Identify the Workflow

- What task do you repeat often?
- What steps are always the same?
- What context is needed?

</div>

<div class="mt-6">

## Step 2: Document the Process

- Write clear instructions
- Include code examples
- Add "When to Use" criteria
- Provide troubleshooting tips

</div>

<div class="mt-6">

## Step 3: Structure the File

- Create `.cursor/skills/your-skill-name/SKILL.md`
- Add frontmatter
- Organize with clear headings

</div>

<!--
Creating a skill is straightforward:
1. Start with a real workflow you use
2. Document it clearly with examples
3. Put it in the right location

The key is clarity - both for the AI and for other developers who might read it.

Time: 5-6 minutes
-->

---
layout: two-cols
layoutClass: gap-8
---

# Skill Example: Structure

Let's examine a real skill

```markdown
---
name: Create Slide with OpenAPI Image
description: Generate images using 
  OpenAPI and add to Slidev slides
---

# Create Slide with OpenAPI Image

## When to Use
- Creating custom images for slides
- Generating illustrations programmatically

## Instructions
### Step 1: Generate Image
1. Obtain API key
2. Call OpenAI endpoint
3. Save image URL

### Step 2: Add to Slide
Use `layout: image-right`
```

::right::

## Key Elements

✅ **Clear name** and description  
✅ **When to Use** section  
✅ **Step-by-step** instructions  
✅ **Code examples** with syntax  
✅ **Best practices** included  
✅ **Troubleshooting** section  

<div class="mt-4 text-sm opacity-75">

See: `.cursor/skills/create-slide-with-openapi-image/SKILL.md`

</div>

<!--
This example shows a complete skill structure. Notice:
- Clear frontmatter with name and description
- "When to Use" helps the AI decide when to apply it
- Instructions are broken into logical steps
- Code examples show exact syntax
- Best practices and troubleshooting are included

Time: 4-5 minutes
-->

---
transition: slide-up
---

# Best Practices

Write skills that are **clear, maintainable, and effective**

<div class="grid grid-cols-2 gap-6 mt-6">

<div>

## Content

- ✅ Be specific and concrete
- ✅ Include code examples
- ✅ Add error handling
- ✅ Document edge cases
- ✅ Keep instructions atomic

</div>

<div>

## Structure

- ✅ Use clear headings
- ✅ Number steps sequentially
- ✅ Group related steps
- ✅ Add visual examples
- ✅ Include verification steps

</div>

</div>

<div class="mt-6">

## Maintenance

- 🔄 Update skills as workflows evolve
- 📝 Keep examples current
- 🧪 Test skills regularly
- 👥 Share with team for feedback

</div>

<!--
Good skills are:
- Specific enough to be actionable
- General enough to be reusable
- Well-documented for both AI and humans
- Maintained as codebases evolve

Common mistakes:
- Too vague ("do this well")
- Too specific (only works for one exact case)
- Missing examples
- Outdated information

Time: 4-5 minutes
-->

---
layout: two-cols
layoutClass: gap-12
---

# Skills vs Commands vs Rules

Understanding Cursor's extension system

## Skills
**Purpose**: Teach workflows

- Reusable instructions
- Task-specific
- Located in `.cursor/skills/`
- Used when AI needs guidance

## Commands
**Purpose**: Quick actions

- Shortcut prompts
- Located in `.cursor/commands/`
- Triggered by name
- Fast, single-purpose

::right::

## Rules
**Purpose**: Enforce conventions

- Always-applied guidelines
- Located in `.cursor/rules/`
- Context-aware
- Project standards

## When to Use What?

| Type | Use For |
|------|---------|
| **Skill** | Multi-step workflows |
| **Command** | Quick, repeatable prompts |
| **Rule** | Always-follow conventions |

<!--
Understanding the difference helps you choose the right tool:

- **Skills**: "How to do X" - complex workflows
- **Commands**: "Do X now" - quick actions
- **Rules**: "Always do X this way" - standards

They work together:
- Rules set the baseline
- Commands provide shortcuts
- Skills handle complex tasks

Time: 5-6 minutes
-->

---
transition: slide-up
---

# Managing Skills

Organize and maintain your skill library

<div class="grid grid-cols-2 gap-6 mt-6">

<div>

## Organization

```
.cursor/skills/
  ├── frontend/
  │   ├── create-component/
  │   └── setup-testing/
  ├── backend/
  │   ├── create-api-endpoint/
  │   └── setup-database/
  └── shared/
      └── code-review/
```

</div>

<div>

## Maintenance

- 📝 Keep skills updated
- 🗑️ Remove unused skills
- 📚 Document skill dependencies
- 🔍 Review skill effectiveness
- 👥 Share with team

</div>

</div>

<div class="mt-6">

## Sharing Skills

- Version control in repo
- Team documentation
- Cross-project reuse
- Community contributions

</div>

<!--
Good skill management:
- Organize by domain/team/project
- Keep them in version control
- Review and update regularly
- Share with team members
- Remove skills that are no longer relevant

Skills can be:
- Project-specific (in repo)
- Team-wide (shared repo)
- Personal (local only)

Time: 3-4 minutes
-->

---
level: 2
---

# Hands-On: Create Your First Skill

**Timebox**: 10 minutes

<div class="mt-6">

## Task

Create a skill for a workflow you use regularly

</div>

<div class="mt-6">

## Steps

1. **Choose a workflow** (2 min)
   - Something you do often
   - Has clear steps

2. **Write the skill** (6 min)
   - Create `.cursor/skills/your-skill/SKILL.md`
   - Add frontmatter
   - Document instructions

3. **Test it** (2 min)
   - Ask Cursor to use the skill
   - Verify it works

</div>

<div class="mt-6 text-sm opacity-75">

💡 **Tip**: Start simple - you can always expand later

</div>

<!--
This is a hands-on exercise. Participants should:
1. Pick a real workflow they use
2. Create the skill file
3. Test it with Cursor

Common first skills:
- Creating a new component
- Setting up a test file
- Adding a new API endpoint
- Code review checklist

Walk around and help participants. Common issues:
- Skills too vague
- Missing examples
- Wrong file location

Time: 10 minutes
-->

---
transition: fade-out
---

# Common Patterns

Reusable skill templates for common scenarios

<div class="grid grid-cols-2 gap-6 mt-6">

<div>

## File Creation

- Create new file with template
- Add imports and structure
- Include basic setup

## Refactoring

- Identify code to refactor
- Plan changes
- Apply incrementally
- Verify with tests

</div>

<div>

## Testing

- Write test structure
- Add test cases
- Mock dependencies
- Verify coverage

## Documentation

- Generate docs from code
- Update README
- Add examples
- Include diagrams

</div>

</div>

<!--
These are common patterns you can use as templates:

1. **File Creation**: Standard structure for new files
2. **Refactoring**: Safe refactoring workflow
3. **Testing**: Test writing patterns
4. **Documentation**: Doc generation workflows

You can create base skill templates and customize them for specific use cases.

Time: 3-4 minutes
-->

---
layout: center
class: text-center
---

# Troubleshooting

Common issues and solutions

<div class="grid grid-cols-2 gap-8 mt-8 text-left">

<div>

## Skill Not Used

- ❌ Description too vague
- ❌ Wrong file location
- ❌ Missing "When to Use"
- ✅ Check skill name matches use case

</div>

<div>

## Incorrect Results

- ❌ Instructions unclear
- ❌ Missing examples
- ❌ Outdated information
- ✅ Add more specific steps

</div>

</div>

<div class="mt-8 text-sm opacity-75">

💡 **Debug tip**: Ask Cursor "which skills are available?" to verify discovery

</div>

<!--
Common troubleshooting scenarios:

1. **Skill not being used**: Usually means the description doesn't match the request, or the skill isn't in the right location

2. **Wrong results**: Instructions might be ambiguous or missing context

3. **Skill conflicts**: Multiple skills might match - make descriptions more specific

4. **Outdated skills**: Keep skills updated as workflows change

Time: 3-4 minutes
-->

---
transition: slide-up
---

# Advanced Topics

Taking skills to the next level

<div class="grid grid-cols-2 gap-6 mt-6">

<div>

## Skill Composition

- Reference other skills
- Build complex workflows
- Create skill hierarchies

## Context Awareness

- Use project structure
- Read configuration files
- Adapt to codebase patterns

</div>

<div>

## Dynamic Skills

- Generate skills from templates
- Parameterize instructions
- Conditional steps

## Integration

- Combine with commands
- Use with rules
- Leverage workspace context

</div>

</div>

<div class="mt-6 text-sm opacity-75">

🔮 **Future**: Skills may support parameters, conditionals, and more advanced features

</div>

<!--
Advanced topics for power users:

1. **Composition**: Skills can reference other skills, building complex workflows from simple ones

2. **Context**: Skills can read project files, understand structure, and adapt accordingly

3. **Dynamic**: Some teams generate skills from templates based on project type

4. **Integration**: Skills work best when combined with commands and rules

These are emerging patterns - the ecosystem is still evolving.

Time: 4-5 minutes
-->

---
layout: center
class: text-center
---

# Key Takeaways

<div class="text-left max-w-2xl mx-auto mt-8">

## ✅ Skills are reusable workflows

- Document complex tasks
- Share team knowledge
- Improve AI accuracy

## ✅ Structure matters

- Clear frontmatter
- Step-by-step instructions
- Real examples

## ✅ Start simple, iterate

- Begin with one workflow
- Test and refine
- Expand over time

</div>

<div class="mt-12 text-sm opacity-75">

**Next Steps**: Create your first skill, share with team, build your skill library

</div>

<!--
Summary of key points:

1. Skills extend Cursor's capabilities with documented workflows
2. Good structure makes skills effective
3. Start with simple skills and build complexity
4. Skills are most valuable when shared with teams

Encourage participants to:
- Create at least one skill this week
- Share skills with their team
- Iterate based on usage

Time: 2-3 minutes
-->

---
layout: center
class: text-center
---

# Resources & Next Steps

<div class="grid grid-cols-2 gap-8 mt-8 text-left max-w-3xl mx-auto">

<div>

## Documentation

- [Cursor Docs](https://cursor.sh/docs)
- Skill examples in repo
- Team knowledge base

## Practice

- Create 3 skills this week
- Share with team
- Collect feedback

</div>

<div>

## Community

- Share skills publicly
- Learn from others
- Contribute patterns

## Questions?

Workshop Q&A session

</div>

</div>

<div class="mt-12">

<PoweredBySlidev />

</div>

<!--
Wrap up the workshop:

1. Point to resources for further learning
2. Encourage practice and sharing
3. Open for questions
4. Collect feedback

Remind participants:
- Skills are a tool to improve their workflow
- Start small and build up
- Share knowledge with team
- Keep skills updated

Time: 5 minutes for Q&A
-->

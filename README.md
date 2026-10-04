# Skills

This repository contains my personal set of skills and agents I use for 
open-source projects. Please follow the getting started steps to configure the
skills in your project.

## Project structure

The skills in the repository make a couple of assumptions about the project
structure. You're free to do something else, but the skills will behave better
when you have the structure in place.

### Engineering documentation

Place all engineering docs in `docs/engineering` in your project. Add a 
top-level `README.md` file in the directory with a table of contents of what's
there.

I typically add the following elements:

- How error handling should be done
- Resilience patterns that the agent must follow
- Command-line parsing structures 
- How logging and tracing should be handled
- How to create a release of the project

### Architecture documentation

I prefer to use [arc42](https://docs.arc42.org) to record my architecture docs.
You can use something else, as long as you have a `docs/architecture` directory
in your repo with a top-level `README.md` with the table of contents.

### Agent instructions

I rely on `AGENTS.md` or `CLAUDE.md` to have a top-level set of instructions.
You should have at least the following elements in your agent instruction file:

- **What this is:** describes the purpose of the project in two sentences.
- **Commands:** list the `format`, `lint`, `test` and `build` commands here.
- **Documentation:** list a link to the architecture and engineering docs.
- **Definition of done:** specify when a task is completed.

## Getting started

Install the skills with the following command:

```bash
npx skills install https://github.com/wmeints/skills
```

## License

[MIT](LICENSE)

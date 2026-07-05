# Seed prompt for this lesson

This repository was built by handing the prompt below to Claude Code and
working through it interactively, one commit per stage. If you forked this
repo to learn the same material yourself, copy the prompt in the box below
into a fresh Claude Code session (in your own empty repo, or in this one on
a new branch) and work through it live — don't just read the existing
commits, drive them yourself and ask questions as you go.

The commit history already in this repo is one finished run through the
lesson. You can use it as a reference/answer key, but you'll learn more by
generating your own history from scratch and comparing afterward
(`git log --oneline`, `git diff <stage>..<stage>`).

## The prompt

```
Set up a brand new git repository from scratch to teach me compiling
hands-on, in small realistic steps, with meaningful commits I can
git log/diff/checkout through afterward to see how a real project evolves.

Context on me: I'm comfortable with git, Linux, and Docker at a working
level, but the actual C compile pipeline (preprocessing, compiling,
assembling, linking) and concepts like static vs shared libraries,
headers, and Makefiles genuinely confuse me. I eventually want to try
installing Gentoo (a from-source Linux distro) on an old ThinkPad T470,
and I want to actually understand what's happening when packages compile
from source instead of it being a black box.

Please:
1. Create a small C project that starts as a single hello-world .c file,
   compiled directly with gcc from the command line (no Makefile yet) -
   explain each compiler flag you use and what phase of compilation it
   corresponds to (preprocess/compile/assemble/link).
2. Grow it incrementally over several commits: split into multiple .c
   files with a shared header, introduce a static library, then a
   shared/dynamic library, then finally a Makefile that ties it all
   together - one git commit per stage, with a commit message explaining
   what changed and why.
3. At each stage, explain directly in chat exactly what commands you ran,
   what the compiler/linker actually did, and why - teach me, don't just
   silently generate it.
4. Keep it approachable - I'm not new to computers, but this specific area
   (the compile/link pipeline, build tooling) is new to me, so don't
   assume prior C or build-systems experience.
5. At the end, briefly relate this back to how a source-based package
   manager like Gentoo's portage does the same fundamental compile/link
   steps automatically for every package, just with more configuration
   (USE flags, etc.) layered on top.

Ask me clarifying questions about my level of understanding as we go rather
than assuming - I'd rather this be a real back-and-forth than a wall of
generated code and text.
```

## Calibration questions worth asking up front

Before writing any code, the assistant should ask something like the
following, and actually adjust pacing/depth based on the answers rather
than assuming a default level:

1. **GCC exposure** — Have you ever typed a raw `gcc`/`cc` command yourself
   (even copy-pasted one you didn't fully understand), or would this be
   your first time running the compiler directly?
2. **Header files** — Do you know, even loosely, what a header file (`.h`)
   is for in C?
3. **Pacing** — Do you want to go one stage at a time (build a stage,
   commit, then stop and wait for questions before continuing), or have
   all stages built and explained up front with Q&A after?

Answers to these should change what gets explained and how much - e.g.
someone who already understands headers doesn't need that reexplained,
and "one stage at a time" means the assistant should actually stop and
wait rather than plowing through every stage in one response.

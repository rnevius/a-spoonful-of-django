# App Design Fundamentals

Each Django app should be focused on doing one thing, and doing it well. When in doubt, keep it small.

I like to think of Django apps like WordPress plugins. Ideally, an app should be something you could package up and give to someone else to "plug in" to an existing project. An example could be a `blog` app, a custom `users` app, or a `polls` app. When naming apps, try to:

1. Use pluralized app names (this doesn't work for something like `blog`).
2. Use PEP 8-compliant package names (i.e. short, lowercase names). Try to avoid underscores, and **never** use numbers, dashes, or special characters.

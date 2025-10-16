# Tailwind 4 to Tailwind 3 Downgrade Prompt

You are helping to downgrade React components from Tailwind CSS v4 to v3. Apply these conversions:

## Utility Class Renames

Some utility classes were renamed in Tailwind 4. Below is a guide for you to follow to rename some of these values from Tailwind 4 syntax to Tailwind 3 syntax.

- `shadow-xs` → `shadow-sm`
- `shadow-sm` → `shadow`
- `drop-shadow-xs` → `drop-shadow-sm`
- `drop-shadow-sm` → `drop-shadow`
- `blur-xs` → `blur-sm`
- `blur-sm` → `blur`
- `backdrop-blur-xs` → `backdrop-blur-sm`
- `backdrop-blur-sm` → `backdrop-blur`
- `rounded-xs` → `rounded-sm`
- `rounded-sm` → `rounded`
- `outline-hidden` → `outline-none`
- `ring-3` → `ring`

## Variables in aritrary values

In Tailwind 4, arbitrary values that use CSS variables could be wrapped with "()". However, this syntax is not supported in Tailwind 3 and should be updated to wrap with "[]".

Below is an example:

- `<div class="bg-(--brand-color)"></div>` → `<div class="bg-[--brand-color]"></div>`

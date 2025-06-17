# How to make Custom Callouts in Obsidian

After spending some time experimenting with different ways to style my notes, I realized I wanted custom callouts in Obsidian, but without adding yet another plugin. I’m trying to keep my setup lean and avoid relying on too many plugins for core features. This guide is the result of my process figuring out how to create my own custom callouts using just CSS, so you can do the same!

Callouts are a powerful way to visually style notes in [Obsidian](https://obsidian.md), especially when organising research, study notes, to-do lists, or even documenting your projects. While Obsidian comes with built-in callout styles like `> [!note]`, you can easily create your own custom callouts with a bit of CSS.

This post will walk you through how to make your own **custom callout blocks** in Obsidian.

---

## Step 1: Enable Custom CSS Snippets

Before we begin, make sure you’ve enabled CSS snippets in Obsidian:

1. Open **Settings** → **Appearance**
2. Scroll down to **CSS snippets**
3. Click **Open snippets folder**
4. Create a new `.css` file, for example: `custom-callouts.css`
5. Back in Obsidian, toggle your new snippet **on**

---

## Step 2: Define a Custom Callout Block in the css file

Here’s an example of a custom callout called `figure` with a pink theme and a pencil icon:

```css
/* === FIGURE === */
.callout[data-callout="figure"] {
    --callout-color: 255, 121, 198;
    --callout-icon: lucide-pencil;
    background-color: rgba(255, 121, 198, 0.2);
}
```

To use this in your note, write:

```markdown
> [!figure]
> This is a **figure** callout. Great for highlighting diagrams or illustrations.
```

This is how it looks in Obsidian:

![alt text](../../img/blogs/obidian_callouts/fig1.png)

And voilà, Obsidian will render it with your defined styles.

---

## Customise Labels, Icons & Colors

You can define any name for your callout, it can be `[!theorem]`, `[!tip]`, `[!poetry]`, or whatever suits your workflow. Each one can be styled uniquely by modifying:

* `--callout-color`: the RGB value of your theme
* `--callout-icon`: choose any [Lucide Icon](https://lucide.dev/) (used by Obsidian)

Here's another example using a theorem block:

```css
/* === THEOREM === */
.callout[data-callout="theorem"] {
    --callout-color: 189, 147, 249;
    --callout-icon: lucide-square-sigma;
    background-color: rgba(189, 147, 249, 0.2);
}
```

Use it in your note like this:

```markdown
> [!theorem]
> **Theorem (Pythagoras)**  
> In a right-angled triangle:  
> $a^2 + b^2 = c^2$
```

This will render as:

![alt text](../../img/blogs/obidian_callouts/fig2.png)

Most of the ones I've made have been for equations, theorems, figures or other mathematical content, but you can create any type of callout you need. I even made some "warning" ones:

```css
/* === ATTENTION, CAUTION, WARNING === */
.callout[data-callout="attention"],
.callout[data-callout="caution"],
.callout[data-callout="warning"] {
    --callout-color: 241, 250, 140;
    --callout-icon: lucide-alert-triangle;
    background-color: rgba(241, 250, 140, 0.2);
}
```

Use them like this:

```markdown

> [!attention]
> Attention! This area is under construction.

> [!caution]
> Caution: The process may overwrite existing data.

> [!warning]
> Warning: Unsaved changes will be lost.
```

This will render as:

![alt text](../../img/blogs/obidian_callouts/fig3.png)

---

## Useful Links

* [📘 Obsidian Callouts Documentation](https://help.obsidian.md/Editing+and+formatting/Callouts)
* [🎨 Lucide Icon Library](https://lucide.dev/)

---

## 🧪 Final Tips

* You can define as many custom callouts as you like, one for each purpose.
* Keep your styles readable by using soft background `rgba` values.
* Consider matching your callouts to your Obsidian theme for a cohesive look.
* You can even use transparent or darkened backgrounds to create layered effects.

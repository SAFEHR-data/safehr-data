[![Netlify Status](https://api.netlify.com/api/v1/badges/af9b2397-7510-4bbb-8cb6-ec2393f738ed/deploy-status)](https://app.netlify.com/sites/safehr-data/deploys)

# SAFEHR starter

A simple website to direct users to the SAFEHR resources.

## Getting started

If you're a developer then you can fork this repo, edit, and submit a pull request.
If you're not a developer then you can edit much of the site in a visual editor.

## How it works

This is a Jekyll powered static blog. We chose Jeklyl so we can integrate with the data cards [site](https://safehr-data.github.io/uclh-research-discovery/) at some point. We're using the [Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/) for the visual design. The site is hosted on Netlify, and we're using [DecapCMS](https://decapcms.org/) to manage the content.

## Tips

### Creating diagrams

Design your diagrams using the [mermaid live editor](https://mermaid.live/). You can then copy and paste the code into the markdown file. Set the front matter of your page to include the following:

```yaml
mermaid: true
```

And then insert your diagram code as raw html into the markdown file. For example:

```html
<div class="mermaid">
graph TD
    A[Start] --> B{Is it working?}
    B -->|Yes| C[Great!]
    B -->|No| D[Debug]
    D --> B
</div>
```

## Useful links

- [Documentation for the Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/docs/)
- [Create a diagram with using the mermaid live editor](https://mermaid.live/)
- [Setting up a Jekyll site with GitHub Pages](https://jekyllrb.com/docs/github-pages/)
- [Jekyll documentation](https://jekyllrb.com/docs/home/)
- [Netlify documentation](https://docs.netlify.com/)
- [Decapation CMS documentation](https://decapcms.org/docs/)

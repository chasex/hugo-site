# hugo-site
Chasex's personal blog at [chasex.github.io](https://chasex.github.io)

## Modules
Hugo-site contain two submodules. The fisrt one is public, referred to [chasex.github.io](https://github.com/chasex/chasex.github.io),
which is for publishing generated pages. The second one is hugo-icarus-theme, referred to [hugo-icarus-theme](https://github.com/chasex/hugo-icarus-theme),
for keep theme update with origin repo.

### Usage

1. Clone hugo-site repo and its submodules

        git clone --recursive https://github.com/chasex/hugo-site.git


2. Play hugo on localhost, visit at `localhost:1313`

        hugo server -w


3. Add new post

        hugo new post/post.md


4. Generate static pages

        hugo


5. Publish to github pages

        cd public
        git add -a -m "add post.md"
        git push

6. Do not forget update hugo-site repo

        cd hugo-site
        git add -a -m "add post.md"
        git push

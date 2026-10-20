# dalkaperg.com

Website for the Dalka Physics Education Research Group, built with Jekyll and hosted on GitHub Pages. GitHub builds the site automatically every time you change a file, so there is nothing to install.

## Editing the site

Most updates only require editing the files in `_data/`:

| To change...                         | Edit                    |
|--------------------------------------|-------------------------|
| Group name, institution, email       | `_config.yml`           |
| People (current members and alumni)  | `_data/people.yml`      |
| Publications and presentations       | `_data/publications.yml`|
| Research areas                       | `_data/research.yml`    |
| News items on the home page          | `_data/news.yml`        |
| Home page headline and intro         | `index.html`            |

You can edit any file directly on github.com: open it, click the pencil icon, make your change, and click **Commit changes**. The live site updates within a minute or two.

### Adding a student

Only add students who have agreed to be listed. Copy an existing entry in `_data/people.yml` and change the details. Indentation matters in YAML files: keep the same spacing as the entries around it.

To add a photo, upload a square-ish image to `assets/img/people/` (for example `jane-doe.jpg`) and set `photo: jane-doe.jpg`. If there's no photo, the site shows the person's initials.

When a student leaves, move their entry from `current:` to `alumni:` and optionally add a `now:` line, e.g. `now: Now teaching high school physics in Chicago`. To remove someone entirely, delete their entry.

## Colors and logo

The palette lives at the top of `assets/css/style.css`:

- Base `#F2C83F` (PERG yellow): hero band, section markers, avatars
- Secondary `#2E3A47` (slate): links and buttons
- Tertiary `#D55E00` (vermillion): graphic highlights

All three stay distinguishable under the common forms of color blindness. To change the logo, replace `assets/img/logo.png` (and `assets/img/favicon.png` for the browser tab icon).

All text uses Inter, loaded from Google Fonts.

## Hosting setup (one time)

1. Create a **public** repository on GitHub (Pages is free for public repos). Upload all of these files to the top level of the repo, not inside a subfolder.
2. In the repo, go to **Settings > Pages**. Under *Build and deployment*, choose **Deploy from a branch**, branch **main**, folder **/ (root)**, and save.
3. Still on that page, enter `dalkaperg.com` under *Custom domain* and save. (The `CNAME` file in this repo already contains it.)
4. At your domain registrar, add these DNS records:

   | Type  | Host / Name | Value                    |
   |-------|-------------|--------------------------|
   | A     | @           | 185.199.108.153          |
   | A     | @           | 185.199.109.153          |
   | A     | @           | 185.199.110.153          |
   | A     | @           | 185.199.111.153          |
   | AAAA  | @           | 2606:50c0:8000::153      |
   | AAAA  | @           | 2606:50c0:8001::153      |
   | AAAA  | @           | 2606:50c0:8002::153      |
   | AAAA  | @           | 2606:50c0:8003::153      |
   | CNAME | www         | YOUR-GITHUB-USERNAME.github.io |

   Delete any existing A records or "parking page" / URL-forwarding records the registrar created for `@`.
5. Wait for DNS to propagate (minutes to a few hours). Once GitHub shows the DNS check passing, tick **Enforce HTTPS**.
6. Recommended: verify the domain in your GitHub account (**profile Settings > Pages > Add a domain**), which adds a TXT record and prevents anyone else from claiming it on GitHub.

## Previewing locally (optional)

If you want to preview changes before publishing, install Ruby and run `gem install jekyll` then `jekyll serve` in this folder, and open http://localhost:4000. This isn't required; editing on GitHub works fine.

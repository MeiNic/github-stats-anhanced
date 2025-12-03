# [GitHub Stats Visualization](https://github.com/jstrieb/github-stats)

<!--
https://github.community/t/support-theme-context-for-images-in-light-vs-dark-mode/147981/84
-->
<a href="github.com/MeiNic/github-stats-anhanced">
<img src="https://github.com/MeiNic/github-stats-anhanced/blob/master/generated/overview.svg#gh-dark-mode-only" />
<img src="https://github.com/MeiNic/github-stats-anhanced/blob/master/generated/languages.svg#gh-dark-mode-only" />
<img src="https://github.com/MeiNic/github-stats-anhanced/blob/master/generated/overview.svg#gh-light-mode-only" />
<img src="https://github.com/MeiNic/github-stats-anhanced/blob/master/generated/languages.svg#gh-light-mode-only" />
</a>

Generate visualizations of GitHub user and repository statistics with GitHub
Actions. Visualizations can include data for both private repositories, and for
repositories you have contributed to, but do not own.

Generated images automatically switch between GitHub light theme and GitHub
dark theme.

## Disclaimer

If the project is used with an access token that has sufficient permissions to
read private repositories, it may leak details about those repositories in
error messages. For example, the `aiohttp` library—used for asynchronous API
requests—may include the requested URL in exceptions, which can leak the name
of private repositories. If there is an exception caused by `aiohttp`, this
exception will be viewable in the Actions tab of the repository fork, and
anyone may be able to see the name of one or more private repositories.

Due to some issues with the GitHub statistics API, there are some situations
where it returns inaccurate results. Specifically, the repository view count
statistics and total lines of code modified are probably somewhat inaccurate.
Unexpectedly, these values will become more accurate over time as GitHub
caches statistics for your repositories. Additionally, repositories that were
last contributed to more than a year ago may not be included in the statistics
due to limitations in the results returned by the API.

For more information on inaccuracies, see issues in the origin-repo
[#2](https://github.com/jstrieb/github-stats/issues/2),
[#3](https://github.com/jstrieb/github-stats/issues/3), and
[#13](https://github.com/jstrieb/github-stats/issues/13).

# Installation

<!-- TODO: Add details and screenshots -->

1. Create a personal access token (not the default GitHub Actions token) using
   the instructions
   [here](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token).
   Personal access token must have permissions: `read:user` and `repo`. Copy
   the access token when it is generated – if you lose it, you will have to
   regenerate the token.
   - Some users are reporting that it can take a few minutes for the personal
     access token to work. For more, see 
     [#30](https://github.com/jstrieb/github-stats/issues/30).
2. Create a copy of this repository by clicking
   [here](https://github.com/jstrieb/github-stats/generate). Note: this is
   **not** the same as forking a copy because it copies everything fresh,
   without the huge commit history. 
3. Go to the "Secrets" page of your copy of the repository. If this is the
   README of your copy, click [this link](../../settings/secrets/actions) to go
   to the "Secrets" page. Otherwise, go to the "Settings" tab of the
   newly-created repository and go to the "Secrets" page (bottom left).
4. Create a new secret with the name `ACCESS_TOKEN` and paste the copied
   personal access token as the value.
5. It is possible to change the type of statistics reported by adding other
   repository secrets. 
   - To ignore certain repos, add them (in owner/name format e.g.,
     `meinic/github-stats-anhanced`) separated by commas to a new secret—created as
     before—called `EXCLUDED`.
   - To ignore certain languages, add them (separated by commas) to a new
     secret called `EXCLUDED_LANGS`. For example, to exclude HTML and TeX you
     could set the value to `html,tex`.
   - To show statistics only for "owned" repositories and not forks with
     contributions, add an environment variable (under the `env` header in the
     [main
     workflow](https://github.com/MeiNic/github-stats-anhanced/blob/master/.github/workflows/main.yml))
     called `EXCLUDE_FORKED_REPOS` with a value of `true`.
   - These other values are added as secrets by default to prevent leaking
     information about private repositories. If you're not worried about that,
     you can change the values directly [in the Actions workflow
     itself](https://github.com/MeiNic/github-stats-anhanced/blob/master/.github/workflows/main.yml).
6. Go to the [Actions
   Page](../../actions?query=workflow%3A"Generate+Stats+Images") and press "Run
   Workflow" on the right side of the screen to generate images for the first
   time. 
   - The images will be automatically regenerated every day at 5 AM, but they can
     be regenerated manually by running the workflow this way.
7. Take a look at the images that have been created in the
   [`generated`](generated) folder.
8. To add your statistics to your GitHub Profile README, copy and paste the
   following lines of code into your markdown content. Change the `username`
   value to your GitHub username.
   ```md
   ![](https://raw.githubusercontent.com/username/github-stats/master/generated/overview.svg#gh-dark-mode-only)
   ![](https://raw.githubusercontent.com/username/github-stats/master/generated/overview.svg#gh-light-mode-only)
   ```
   ```md
   ![](https://raw.githubusercontent.com/username/github-stats/master/generated/languages.svg#gh-dark-mode-only)
   ![](https://raw.githubusercontent.com/username/github-stats/master/generated/languages.svg#gh-light-mode-only)
   ```
9. Link back to this repository so that others can generate their own
   statistics images.
10. Star this repo if you like it!


# Support the Project

There are a few things you can do to support the project:

- Star the repository (and follow me on GitHub for more)
- Share and upvote on sites like Twitter, Reddit, and Hacker News
- Report any bugs, glitches, or errors that you find

# Related Projects

- The project was created as a mix of the original [jstrieb/github-stats](https://github.com/jstrieb/github-stats) and a fort of it from [pushpakumarbalan/pushpakumarbalan](https://github.com/pushpakumarbalan/pushpakumarbalan)

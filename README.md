# Lesson template for ReproNim teaching sessions

How to use this template:

1. Go to the <a href="http://import.github.com/new?import_url=https://github.com/ReproNim/lesson-template
" target="_blank"> Github Importer</a>. In the top text box paste the url of this repo. In the bottom part
choose either "ReproNim" (if that's an option) or your own user account and
then enter the name of the lesson/repository that you wish to create.

2. Change the following variables in the `_config.yml` file:
   - `title`
   - `repo`
   - `root`
   - `email` (you can leave Ariel's address here, if you want).
   - `start_time` : this is the start time in minutes since midnight. For
     example, 9 AM is 540 (60 * 9).

3. Edit the content in the `_episodes` folder, adding images (into
  `assets/img`), code (into `code`), data (into `data`) as needed. Pay
  particular attention to the following:

  - Sections should be named `01-first-part.md`, `02-second-part.md`, etc to be ordered in the schedule.
  - Edit the headers of each of your sections. Editing the duration of both `teaching` and `exercises`
  - Add coffee breaks into the lesson. This keeps the timing of each section
    accurate.

# Running with Docker locally for development

Instead of installing ruby and jekyll, you can use docker to run a live version of your repo locally.
As you make changes, it will recompile the changes and all you will need to do is refresh the browser.

The following command it assumes that you are inside your cloned github repo. Adapted from [this blog](https://dev.to/michael/compile-a-jekyll-project-without-installing-jekyll-or-ruby-by-using-docker-4184):

```
docker run --rm -it --volume="$PWD:/srv/jekyll" --volume="$PWD/vendor/bundle:/usr/local/bundle" \
 --env JEKYLL_ENV=development -p 4000:4000 jekyll/jekyll:4.0.1 \
 jekyll serve --config _config.yml,_config_dev.yml
```
You should then be able to open the live page at http://localhost:4000/

What this command does is 

- `--rm` automatically removes the container when it exits
- `-it` allows you to interrupt the running server to exit with Ctrl+C
- `--volume="$PWD:/srv/jekyll"` takes the current directory indicated by `$PWD` and map it to the directory at `/srv/jekyll` within the container so that it could build it
- `--volume="$PWD/vendor/bundle:/usr/local/bundle"` this option maps the contents of the current directory's `/vendor/bundle` and maps it to `/usr/local/bundle`. The reason for this option is so that gems could be cached and reused in future builds
- `--env JEKYLL_ENV=development` allows local development.
- `jekyll/jekyll:4.0.1` this tells it to use this specific tagged version of the Jekyll container
- `jekyll serve --config _config.yml,_config_dev.yml` serves the live compiled content

If you already have jekyll installed for other projects, you can run 
`jekyll serve --config _config.yml,_config_dev.yml` inside your cloned github repo.

# Acknowledgment

Please see [LICENSE.md](LICENSE.md) for copyright, license, and how to acknowledge information.

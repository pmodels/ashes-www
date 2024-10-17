# Website for the AsHES Workshop

The website is created by using **Jekyll** (https://jekyllrb.com/) and published via **Github Actions**. All editions from 2021 will be purely maintained on this github repository.

## History
Old websites (2011-2020) are maintained at [gitlab](https://gitlab.com/pmodels/websites/ashes) and the web server is setup by Argonne.
However, we can no longer make any updates on the old websites. If any change is needed, please migrate the corresponding year's folder to
this repository (need to transfer P2P files to Jekyll formats).

If you need permisison to access [gitlab](https://gitlab.com/pmodels/websites/ashes), please email Min Si.

## How to Modify
The following steps use the 2021 edition as the example.
This is a Jekyll site, so you need ruby.

### Setting up a ruby environment (Ubuntu 22.04 LTS)

```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv

# This will modify your .bashrc!
~/.rbenv/bin/rbenv init
```

get a new shell so rbenv works

```bash
# install this plugin so `rbenv install` works
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build

# install prerequisite build libraries
apt-get install autoconf patch build-essential rustc libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libgmp-dev libncurses5-dev libffi-dev libgdbm6 libgdbm-dev libdb-dev uuid-dev

#install a ruby
rbenv install 3.3.5

# set the ruby to be the one used for this project
rbenv local 3.3.5
```

get a new shell

```bash
ruby --version

# this may give an error about things not being installed. Follow the directions to install the missing packages
cd 2025
bundle exec jekyll serve
```

navigate to localhost:4000/2025/index.html in your browser and you should see the site

### Getting Jekyll

- `git clone git@github.com:pmodels/ashes-www.git ashes-www/`
- Follow **quickstart** at https://jekyllrb.com/docs/ to create a local Jekyll environment under `ashes-www/2021`
- Make change locally and confirm the updated website in the local Jekyll environment
- `git push` ## this step will trigger the [deployment action](https://github.com/pmodels/ashes-www/blob/master/.github/workflows/deploy.yml)
- Confirm the updated website at https://pmodels.github.io/ashes-www/2021/

## Detail of The Deloyment Action
The [deployment action](https://github.com/pmodels/ashes-www/blob/master/.github/workflows/deploy.yml) performs the script
at [./maint/build.bash](https://github.com/pmodels/ashes-www/blob/master/maint/build.bash). The `build.bash` script traverses all subsite folders
and builds the static html files for each of them.

For every newly added subsite, please add the folder name in `build.bash`.

## Setting
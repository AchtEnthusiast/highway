# Highway

Welcome to the Hack Club Highways.

## Local development

To run this project, you need to first install `ruby`, `ruby-stdlib`, `postgresql`, `postgresql-libs`, `docker` and `gem`.

Then, add the following to your `.zshrc` or `.bashrc` to activate the ruby development environment:
```zsh
export GEM_HOME="$(gem env user_gemhome 2>/dev/null)"
export PATH="$PATH:$GEM_HOME/bin"
```

Restart your terminal session, and run the following code at the root of the cloned respository to install the required packages:
```zsh
gem install rails
gem install kamal
bundle install
```

Now, create a postgresql database:
```
sudo su -l postgres -c "initdb --locale=C.UTF-8 --encoding=UTF8 -D '/var/lib/postgres/data'"
sudo su -l postgres
$ createuser --interactive
Enter name of role to add: <your username>
Shall the new role be a superuser? (y/n) y
$ createdb highway_dev
$ createdb highway_test
$ exit
```

Start the docker server:
```zsh
bin/rails credentials:edit
docker build . --tag highway:latest
docker run highway
```

At last, run the executable at `./bin/setup` to start up the development server!


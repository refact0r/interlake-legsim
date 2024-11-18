# seting up legsim

install wsl ubuntu:

```bash
wsl --install
```

restart your computer if it tells you to.

to start a new ubuntu terminal:

```bash
ubuntu
```

clone legsim repo:

```bash
git clone https://github.com/ReeledWarrior14/interlake-legsim.git
```

install rbenv to install ruby:

```bash
sudo apt install rbenv
```

if you get `E: Unable to locate package rbenv`, run this before installing rbenv:

```bash
sudo add-apt-repository main
sudo add-apt-repository universe
sudo add-apt-repository restricted
sudo add-apt-repository multiverse
```

add rbenv init to your bashrc:

```bash
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc
```

enter into legsim directory:

```bash
cd interlake-legsim
```

install the correct ruby version:

```bash
rbenv install
```

switch to the correct ruby version:

```bash
rbenv local 3.1.2
```

check if the ruby version is correct:

```bash
ruby -v
# ruby 3.1.2p20 (2022-04-12 revision 4491bb740a) [x86_64-linux]
```

install gems:

```bash
gem install bundler
bundle install
```

if you get the error: `An error occurred while installing mysql2 (0.5.6), and Bundler cannot continue.`, run this before `bundle install`:

```bash
sudo apt install libmysqlclient-dev
```

once `bundle install` has succeeded, restart your terminal.

check if rails works:

```bash
rails -v
# Rails 7.0.4
```

install nodejs:

```bash
sudo apt install nodejs
```

go to [config/application.rb](config/application.rb) and comment out the lines with `user_name` and `password`.

then edit rails credentials:

```bash
EDITOR="code --wait" rails credentials:edit
```

it should open up a new vscode tab with the rails credentials file. copy the contents of [config/credentials.yml.example](config/credentials.yml.example) below the `secret_key_base:` line and paste it into the file.

fill in `root` for the gmail and database usernames and passwords. ignore elavon.

save and close the file. you should see `File encrypted and saved.` in the terminal.

go back to [config/application.rb](config/application.rb) and uncomment the lines from earlier.

install mysql-server:

```bash
sudo apt install mysql-server
```

edit the [config/database.yml](config/database.yml) file. in the default and development sections, change the username to `railsuser` and the password to `root`.  

now go into mysql and create a user with the username `railsuser` and password `root`.

```bash
sudo mysql
CREATE USER 'railsuser'@'localhost' IDENTIFIED BY 'root';
GRANT ALL PRIVILEGES ON *.* TO 'railsuser'@'localhost';
FLUSH PRIVILEGES;
exit
```

create and migrate the database:

```bash
rails db:create
rails db:migrate
rails db:schema:load
```

try to run the server:

```bash
rails server
```

now you should be able to access the site at the link provided in the terminal, something like `http://127.0.0.1:3000/`.

by default, it will redirect you to the user sign in page. this page is for student users. to access the system menu, go to `/system` to the link. it will show a different login page.

since there are no system users yet, you'll have to create one. create a new terminal, enter the legsim directory, and run:

```bash
rails console
```

you can create a new user by running:

```ruby
SystemUser.create(email:"user@example.com", password:"password", password_confirmation: "password")
```

now you should be able to log in as a system user. note that all of the login buttons are broken and you will have to press enter inside a text field to submit the form.

once you're logged in, you can create a new course by clicking on the 'Courses' tab and then clicking 'Create New Course' and filling in the form.

next, create a new chamber by clicking 'Create New Chamber' and filling in the form.

now you can create normal users (students) by going to the root / route, which will redirect you to the user sign in page. click 'Create New Account' and fill in the form. it may error out, but that's fine. you can verify that the user was created by going to `/system/users` and checking the chamber's number of users.

once a user is created, you can properly log in as a student.

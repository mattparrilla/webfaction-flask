#Flask Project Template For Webfaction Hosting Environment
This repository is meant to provide a quick way to spin up Flask applications on Webfaction and is based off of [Aaron Presley's blog post](http://aaronpresley.com/deploying-a-flask-project-on-webfaction/). I'll rely heavily on that post for instructions and will only provide instruction where I deviate from his recipe.

The project structure I've employed here is slighly different, but similar enough that if you get stuck along the way, you should refer to [his original blog post](http://aaronpresley.com/deploying-a-flask-project-on-webfaction/).

## Steps
1. Create a new application on Webfaction
2. Edit `apache2/conf/httpd.conf` (see Step 3 of post)
3. Clone project
    1. `cd ~/webapps/project_name`
    2. `git clone <YOUR PROJECT'S CLONE URL> app`
4. Instantiate virtual environment and install dependencies
    1. `cd ~/webapps/project_name/app/`
    2. `virtualenv venv`
    3. `source venv/bin/activate`
    4. `pip install -r requirements.txt`
5. Create `htdocs/index.py`

        import sys

        # Active your Virtual Environment, which I'm assuming you've already setup
        activate_this='/home/username/webapps/app/venv/bin/activate.py'
        execfile(activate_this, dict(__file__=activate_this))

        # Appending our Flask project files
        sys.path.append('/home/username/webapps/application_name/app')

        # Launching our app
        from main import app as application

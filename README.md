flask-jade2underscore
=====================

A small Flask extension that makes it easy to use Jade to Underscore templates compiler (used in Backbone) with your Flask application.

## Installation

### Install with PIP

    pip install -e git+git@github.com:weapp/flask-jade2underscore.git#egg=flask-jade2underscore


### Install with setup.py

    git clone https://github.com/weapp/flask-jade2underscore.git
    python setup.py install


## Usage

You can activate it by calling the `jade2underscore` function with your Flask app as a parameter:

    from flaskext.jade2underscore import jade2underscore
    jade2underscore(app, underscore_folder='underscore', jade_folder='src/jade')

This will intercept the request to `underscore_folder` and compile de file if is necesary using the files from `jade_folder`.

When you deploy your app you might not want to accept the overhead of checking the modification time of your `.jade` and `.tpl` files on each request. A simple way to avoid this is wrapping the jade2underscore call in an if statement:

    if app.debug:
        from flaskext.jade2underscore import jade2underscore
        jade2underscore(app)
        
If you do this you’ll be responsible for rendering the `.jade` files into `.tpl` when you deploy in non-debug mode to your production server.
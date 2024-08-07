# mergecal <a href="https://www.buymeacoffee.com/abe101" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" align="right" height="41" width="174"></a>

[![Actively Maintained](https://img.shields.io/badge/Maintenance%20Level-Actively%20Maintained-green.svg)](https://gist.github.com/cheerfulstoic/d107229326a01ff0f333a1d3476e068d)
[![Discord](https://img.shields.io/discord/1017782904509710366)](https://discord.gg/2vqUzSpt6N)

Welcome to mergecal, a Django webapp that allows you to merge multiple iCalendar feeds into a single feed. With mergecal, you can easily keep track of events from multiple sources in one place.

Available at [https://MergeCal.org](https://mergecal.org)

## Using mergecal

To use mergecal, you'll need to create an account and log in. Once you're logged in, you can create a calendar and add iCalendar feeds to your calendar by entering the URL of the feed and clicking "Add Feed".

### Explanation

1. When a user adds an iCalendar feed to their account, mergecal stores the URL of the feed in the database.

2. The webapp has a background task that runs every so often to fetch the events from all of the iCalendar feeds associated with a user's calendar.

3. The events are then merged into a single calendar and stored in the database.

4. To view the events from all of your added iCalendar feeds in one place, click on the "Subscribe" button and copy the provided URL.

5. Add the URL to your calendar client (e.g. Google Calendar) to view all of the events from the merged feeds in one place.
<!--
Here's a [blog post](https://happyandeffective.notion.site/Blog-Post-Draft-Community-Calendars-897779ae1fb041d3a2e4a6b8829b1deb) written by [Casey Watts](https://github.com/caseywatts) detailing the problem and multiple approaches how to solve it.
-->

### Deployment Diagram

![Project-Diagram](https://user-images.githubusercontent.com/82916197/205155655-4371301d-b5f7-42dc-a210-518e161c314e.png)

## Contributing

We welcome contributions to mergecal! If you have ideas for new features, bug fixes, or other improvements, please feel free to open an issue or pull request on our [GitHub repository](https://github.com/abe-101/mergecal).

If you'd like to discuss the project or get more involved, join us on our [Discord channel](https://discord.gg/2vqUzSpt6N). We'd love to have you as part of the mergecal community!

## Local Development

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

- Python 3.9 or higher
- Django 4.0 or higher

### Installing

Clone the repository to your local machine:

```
git clone https://github.com/abe-101/mergecal.git
```

Navigate to the project directory:

```
cd mergecal
```

Create a virtual environment:

```
virtualenv env
```

Activate the environment:

```
source env/bin/activate
```

Install the required dependencies:

```
pip install -r requirements/local.txt
```

Run the Django migrations:

```
python manage.py migrate
```

Start the development server:

```
python manage.py runserver
```

The app should now be running at http://localhost:8000/.

This app comes with Celery.

To run a celery worker with celerybeat:

```bash
celery -A config.celery_app worker -l info
```

```bash
celery -A config.celery_app beat -l info --scheduler django_celery_beat.schedulers:DatabaseScheduler
```

[![Built with Cookiecutter Django](https://img.shields.io/badge/built%20with-Cookiecutter%20Django-ff69b4.svg?logo=cookiecutter)](https://github.com/cookiecutter/cookiecutter-django/)
[![Black code style](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/ambv/black)

License: MIT

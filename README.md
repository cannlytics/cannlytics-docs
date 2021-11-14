# <img height="32" alt="" src="https://cannlytics.com/static/cannlytics_website/images/logos/cannlytics_calyx_detailed.svg"> Cannlytics Documentation

[![License: MIT](https://img.shields.io/badge/License-MIT-darkgreen.svg)](https://opensource.org/licenses/MIT)

Cannlytics is simple, easy-to-use, **end-to-end** cannabis analytics software designed to make your data and information accessible. Cannlytics makes cannabis analysis **simple** and **easy** through data accessibility. We believe that everyone in the cannabis industry should be able to access rich, valuable data quickly and easily and that you will be better off for it. This documentation covers the Cannlytics architecture and how to build, develop, and publish the Cannlytics platform. You can view the platform live at <https://console.cannlytics.com> and the documentation at <https://docs.cannlytics.com>.

- [🌱 Installation](#installation)
- [🔨 Development](#development)
- [🚀 Publishing](#publishing)
- [❤️ Support](#support)
- [🏛️ License](#license)

## 🌱 Installation <a name="installation"></a>

In your root directory, you will need to create a `.firebaserc` file that looks like:

```json
{
  "projects": {
    "default": "your-project"
  },
  "targets": {
    "your-project": {
      "hosting": {
        "docs": [
          "your-project-docs"
        ]
      }
    }
  }
}
```

## 🔨 Development <a name="development"></a>

Documentation for the project is written in [Markdown](https://guides.github.com/features/mastering-markdown/). Building the documentation locally requires installing [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) and [Docker](https://www.docker.com/get-started). The configuration for the documentation is contained within `mkdocs.yml`. You can serve the documentation locally by first pulling and building the Material for MKDocs image:

```shell
docker pull squidfunk/mkdocs-material
docker build -t squidfunk/mkdocs-material docs
```

Once setup, you can preview the documentation as you write:

```shell
docker run --rm -it -p 8000:8000 -v squidfunk/mkdocs-material
```

or

```shell
npm run docs
```

> Note that there is [a namespace conflict between `django-livereload-server` and `livereload`](https://gist.github.com/hangtwenty/f53b3867db1e33780505ccafd8d2eef0), so you need to be careful when and where you install Python requirements. If you run into a `django-livereload-server` import error, first check that `PRODUCTION = False` in your `console/settings.py` and then follow [these instructions](https://gist.github.com/hangtwenty/f53b3867db1e33780505ccafd8d2eef0) to uninstall `livereload` and reinstall  `django-livereload-server`.

## 🚀 Publishing <a name="publishing"></a>

When you are ready, you can build the documentation:

```shell
npm run build-docs
```

You can publish the documentation to Firebase Hosting with one simple command:

```shell
firebase deploy --project your-project --only hosting:docs
```

## ❤️ Support <a name="support"></a>

Made with ❤️ and <a href="https://opencollective.com/cannlytics-company">your good will</a>.

## 🏛️ License <a name="license"></a>

```
Copyright (c) 2021 Cannlytics and Cannlytics Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

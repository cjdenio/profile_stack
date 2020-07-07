# profile_stack ![GitHub release (latest by date)](https://img.shields.io/github/v/release/Matt-Gleich/profile_stack)

![test](https://github.com/Matt-Gleich/profile_stack/workflows/test/badge.svg)
![build](https://github.com/Matt-Gleich/profile_stack/workflows/build/badge.svg)

🚀 Display your tech stack on your GitHub profile's README

## ✨ Example

Add the following to a file in `.github/workflows`:

```yml
name: Profile Stack

on: [push]

jobs:
  profile_stack:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: Matt-Gleich/profile_stack@master
```

Based off your config file (see below) this GitHub action will generate a table showing technologies and projects you've used them in (doesn't have to be all, pick any):

| 💻 **Technology**                                                                                                                     | 🚀 **Projects**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [![Dart](https://img.shields.io/static/v1?label=&message=Dart&color=52C0F2&logo=dart&logoColor=white)](https://dart.dev/)             | [![import_sorter](https://img.shields.io/static/v1?label=import_sorter&message=%20&color=000605&logo=github&logoColor=white&labelColor=000605)](https://github.com/fluttercommunity/import_sorter) [![Personal-Site](https://img.shields.io/static/v1?label=Personal-Site&message=%20&color=000605&logo=github&logoColor=white&labelColor=000605)](https://github.com/Matt-Gleich/Personal-Site) [![auralite-mobile](https://img.shields.io/static/v1?label=auralite-mobile%20%28WIP%29&message=%20&color=000605&logo=github&logoColor=white&labelColor=000605)](https://github.com/Matt-Gleich/auralite-mobile) |
| [![Flutter](https://img.shields.io/static/v1?label=&message=Flutter&color=52C0F2&logo=flutter&logoColor=white)](https://flutter.dev/) | [![Personal-Site](https://img.shields.io/static/v1?label=Personal-Site&message=%20&color=000605&logo=github&logoColor=white&labelColor=000605)](https://github.com/Matt-Gleich/Personal-Site) [![auralite-mobile](https://img.shields.io/static/v1?label=auralite-mobile%20%28WIP%29&message=%20&color=000605&logo=github&logoColor=white&labelColor=000605)](https://github.com/Matt-Gleich/auralite-mobile)                                                                                                                                                                                                    |

A live example at my repo: [github.com/Matt-Gleich/Matt-Gleich](https://github.com/Matt-Gleich/Matt-Gleich)

## ⚙️ Config

Configuration for the profile stack. Located by default in `stack.yml` at the root of your repository.

Here is an example config:

```yml
- name: Dart
  logo: dart
  url: https://dart.dev/
  color: 52C0F2
  logoColor: FFFFFF
  projects:
    - https://github.com/fluttercommunity/import_sorter
    - https://github.com/Matt-Gleich/Personal-Site
    - url: https://github.com/Matt-Gleich/auralite-mobile
      wip: true
- name: Flutter
  logo: flutter
  url: https://flutter.dev/
  color: 52C0F2
  logoColor: FFFFFF
  projects:
    - https://github.com/Matt-Gleich/Personal-Site
    - url: https://github.com/Matt-Gleich/auralite-mobile
      wip: true
```

So for each technology there are the following fields you need to fill in:

| **Key**     | **Example Value**                                                                                    | **Description**                                                     |
| ----------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `name`      | Dart                                                                                                 | Name of the technology                                              |
| `logo`      | dart                                                                                                 | Logo for the technology ([list of logos](https://simpleicons.org/)) |
| `url`       | https://flutter.dev/                                                                                 | URL for the technology                                              |
| `logoColor` | FFFFFF                                                                                               | Hex color code for the logo color                                   |
| `color`     | 52C0F2                                                                                               | Hex color code for the background color                             |
| `projects`  | - https://github.com/Matt-Gleich/Personal-Site <br> - https://github.com/Matt-Gleich/auralite-mobile | List of GitHub project URLs or [project objects](#project-object)   |

### Project object

You can optionally pass a list of YAML objects to the `projects` field.
| **Key** | **Example Value** | **Description** |
| - | - | - |
| `url` | https://github.com/Matt-Gleich/Personal-Site | URL to a GitHub project |
| `wip` | `true` | Mark a project as work-in-progress |

### 🦎 Action Configuration

Here is an example config:

```yaml
name: Profile Stack

on: [push]

jobs:
  profile_stack:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: Matt-Gleich/profile_stack@master
        with:
          path: config/stack.yml
          badges: false
          technology_emoji: 👨🏻‍💻
          project_emoji: ✨
```

You can also configure the following when declaring your action:

| **Key**          | **Example Value** | **Description**                                               |
| ---------------- | ----------------- | ------------------------------------------------------------- |
| `path`             | config/stack.yml  | The path in your repository where the config file is located  |
| `badges`           | false             | Don't have badges, just plain old urls                        |
| `technology_emoji` | 👨🏻‍💻                | The emoji to be displayed to the left of the Technology title |
| `project_emoji`    | ✨                | The emoji to be displayed to the left of the Project title    |
| `badge_style`      | flat              | The [Shields.IO style](https://shields.io#styles) that you'd like to be applied to your badges. |

## 💻 Contributing

We would love to have your contribution! Just make sure isn't an already open or closed PR or issue. When contributing use the `dev.Dockerfile` for testing so you don't change any environment variables.

Thank you to our current contributors:

- Matthew Gleich ([@Matt-Gleich](https://github.com/Matt-Gleich))
- Caleb Denio ([@cjdenio](https://github.com/cjdenio))

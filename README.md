
# Projects and TODOs

This is a lightweight Ruby on Rails application for managing Projects and associated TODOs.
It provides simple CRUD for Project and Todo records with basic validations, and uses
modern Rails features (Importmap, Turbo, Stimulus) for a minimal frontend toolchain.

## Features

- Create / Read / Update / Delete Projects
- Create / Read / Update / Delete Todos (each Todo belongs to a Project)
- Basic model validations and error rendering in forms
- Uses Importmap, Turbo and Stimulus (no Node build required for basic development)

## Tech stack

- Ruby on Rails (see `Gemfile`; this repo uses Rails ~> 8.x)
- Importmap / Turbo / Stimulus for frontend behavior
- SQLite3 for development by default (change in `config/database.yml` if needed)

## Prerequisites

- Ruby (use your system manager: `rbenv`, `rvm`, or `chruby`).
- Bundler (`gem install bundler`).
- SQLite3 (or configure another DB in `config/database.yml`).
- `RAILS_MASTER_KEY` environment variable or local master key file if `config/credentials.yml.enc` is present.

Check the `Gemfile` for the exact Rails and Ruby constraints used by this project.

## Setup (development)

1. Install gems:

```bash
bundle install
```

2. Create and migrate the database:

```bash
bin/rails db:create db:migrate
```

3. (Optional) Load seeds:

```bash
bin/rails db:seed
```

4. Start the server:

```bash
bin/rails server
# or: bin/rails server -p 3000
```

Open http://localhost:3000 in your browser. The app exposes `Projects` and `Todos` resources.

## Routes

This app defines RESTful routes for `projects` and `todos`. To inspect available routes run:

```bash
bin/rails routes | grep projects
bin/rails routes | grep todos
```

Common path helpers provided by the routes include `projects_path`, `project_path(@project)`,
`new_project_path`, `edit_project_path(@project)`, and the equivalent `todos_*` helpers.

## Tests

Run the Rails test suite with:

```bash
bin/rails test
```

System tests use Capybara / Selenium and may require a browser driver installed on your machine.

## Development notes

- The app uses `importmap-rails`; JS code lives in `app/javascript` and mappings are in `config/importmap.rb`.
- Prefer `bin/rails` and other `bin/` helpers to ensure the correct Ruby environment is used.
- Controllers render model validation errors (for example, `@project.errors`) — ensure controller actions set the
  corresponding instance variables (e.g., `@project`) before rendering forms.

## Running in Docker

There is a `Dockerfile` included — typical steps: build image, run migrations, and start the server.
Make sure `DATABASE_URL` and credentials are set appropriately for your environment.

## Deployment

Deploy like a standard Rails application. Provide production credentials and a production database adapter.
If the platform requires assets precompilation, run `bin/rails assets:precompile` during deploy.

## Contributing

- Fork the repo, create a feature branch, add tests, and open a pull request.
- Run `bundle exec rubocop` and the test suite before submitting changes.

If you'd like, I can add a `CONTRIBUTING.md`, a `LICENSE` file, or a `bin/setup` helper to automate local setup.

## License

This repository does not include an explicit license. Add a `LICENSE` file (for example, MIT) to make the terms explicit.

---

If you'd like any of the following, tell me which and I'll add them:

- `CONTRIBUTING.md` and a `LICENSE` file
- A small `bin/setup` script or `Makefile` for development
- More precise Ruby/Rails version documentation in the README



# Rails Codespace Template

A ready-to-use template for creating new Ruby on Rails projects in GitHub Codespaces. This template includes a pre-configured development container, GitHub Actions workflows, and helpful setup scripts.

## Features

- **DevContainer Configuration**: Pre-configured development environment with Ruby 3.3, Node.js, and essential VS Code extensions
- **GitHub Actions**: CI/CD workflows for testing, linting, and security scanning
- **Rails 8.1.1**: Latest version of Rails with modern features
- **PostgreSQL Ready**: Database service pre-configured in CI workflows
- **Development Tools**: RuboCop, Brakeman, ERB Lint, and more

## Prerequisites

- GitHub account with Codespaces access
- Basic knowledge of Ruby on Rails

## Quick Start

### Option 1: Using This Template

1. Click "Use this template" button at the top of this repository
2. Create a new repository from this template
3. Open the repository in GitHub Codespaces
4. Follow the setup instructions below

### Option 2: Cloning Without Git History

If you want to use this template without creating a fork or maintaining a connection to this repository, you can download the files directly:

```bash
# Create a new directory for your project
mkdir my-rails-app
cd my-rails-app

# Download the template files
wget -qO- https://github.com/nhorton/rails-codespace-template/archive/refs/heads/main.tar.gz | tar xz --strip-components=1

# Initialize a new git repository
git init
git add .
git commit -m "Initial commit from Rails template"
```


## Creating Your Rails Application

Once you have the template set up, you can create your Rails application using one of the following approaches:

### Default Rails Application

Create a standard Rails application with default settings:

```bash
# Install dependencies
bundle install

# Create new Rails app in current directory
rails new .

# Set up the database
bin/rails db:prepare

# Start the Rails server
bin/rails server
```

### Rails Application with Modern Stack

Create a Rails application with Tailwind CSS, RSpec, SolidQueue, and SolidCache:

```bash
# Install dependencies
bundle install

# Create new Rails app with modern features in current directory
rails new . \
  --database=postgresql \
  --css=tailwind \
  --skip-test \
  --skip-bundle

# Add RSpec, SolidQueue, and SolidCache to Gemfile
cat >> Gemfile << 'EOF'

# Testing framework
group :development, :test do
  gem 'rspec-rails', '~> 7.1'
  gem 'factory_bot_rails', '~> 6.4'
  gem 'faker', '~> 3.5'
end

# Background job processing
gem 'solid_queue', '~> 1.1'

# Caching
gem 'solid_cache', '~> 1.0'
EOF

# Install all gems
bundle install

# Install RSpec
bin/rails generate rspec:install

# Install SolidQueue
bin/rails solid_queue:install

# Install SolidCache
bin/rails solid_cache:install

# Set up the database
bin/rails db:prepare

# Start the Rails server
bin/rails server
```

## Post-Setup Steps

After creating your Rails application:

1. **Update the README**: Replace this README with one specific to your application
2. **Configure Environment Variables**: Copy `.env.example` to `.env` if created
3. **Set Up CI/CD**: The GitHub Actions workflows are already configured and will run on push/PR
4. **Configure Database**: Update `config/database.yml` if needed
5. **Add Dependencies**: Install any additional gems your project needs

## Included GitHub Actions Workflows

This template includes three GitHub Actions workflows:

### 1. CI Workflow (`.github/workflows/ci.yml`)
Runs on every push and pull request:
- Sets up Ruby and Node.js
- Installs dependencies
- Creates and migrates the test database
- Runs RSpec or Minitest tests
- Runs system tests if available

### 2. Lint Workflow (`.github/workflows/lint.yml`)
Runs code quality checks:
- RuboCop for Ruby code style
- ERB Lint for template files

### 3. Security Workflow (`.github/workflows/security.yml`)
Runs security checks (weekly and on push):
- Bundler Audit for vulnerable dependencies
- Brakeman for security vulnerabilities

## Development Container Features

The `.devcontainer/devcontainer.json` includes:

- **Base Image**: Microsoft's official Ruby 3 devcontainer
- **Node.js**: LTS version for JavaScript tooling
- **GitHub CLI**: For interacting with GitHub
- **VS Code Extensions**:
  - Ruby language support
  - Solargraph for intellisense
  - Endwise for automatic end insertion
  - Tailwind CSS IntelliSense
  - GitHub Copilot

## Customization

### Adding More Gems

Edit the `Gemfile` in the template root to add gems you want available before creating your Rails app:

```ruby
gem "your-gem-name", "~> version"
```

Then run:

```bash
bundle install
```

### Modifying GitHub Actions

The workflow files in `.github/workflows/` can be customized to match your project's needs:
- Add more test steps
- Configure different linting rules
- Add deployment workflows
- Integrate with external services

### DevContainer Customization

Modify `.devcontainer/devcontainer.json` to:
- Add VS Code extensions
- Configure environment variables
- Install additional tools
- Change default settings

## Troubleshooting

### Port Already in Use

If port 3000 is already in use:

```bash
bin/rails server -p 3001
```

### Database Connection Issues

Make sure PostgreSQL is running and credentials are correct in `config/database.yml`.

For Codespaces, the default PostgreSQL credentials should work out of the box.

## Resources

- [Rails Guides](https://guides.rubyonrails.org/)
- [Rails 8.1 Release Notes](https://rubyonrails.org/category/releases)
- [GitHub Codespaces Documentation](https://docs.github.com/en/codespaces)
- [SolidQueue Documentation](https://github.com/rails/solid_queue)
- [SolidCache Documentation](https://github.com/rails/solid_cache)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

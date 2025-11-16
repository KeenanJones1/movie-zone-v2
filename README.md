# Movie Zone v2

A modern Rails 7.1.6 application with PostgreSQL database and Vite asset bundling.

## Technology Stack

- **Ruby**: 3.2.3
- **Rails**: 7.1.6
- **Database**: PostgreSQL 16.x
- **JavaScript Bundler**: Vite 5.x with vite-plugin-ruby
- **Frontend Framework**: Hotwire (Turbo + Stimulus)
- **Node.js**: 20.x (for asset compilation)

## Prerequisites

Before setting up this project, ensure you have the following installed:

- Ruby 3.2.3 or higher
- Node.js 20.x or higher
- PostgreSQL 16.x or higher
- Bundler gem

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/KeenanJones1/movie-zone-v2.git
cd movie-zone-v2
```

### 2. Install Dependencies

Install Ruby gems:

```bash
bundle install
```

Install Node.js packages:

```bash
npm install
```

### 3. Database Setup

Make sure PostgreSQL is running:

```bash
# On Ubuntu/Debian
sudo service postgresql start

# On macOS with Homebrew
brew services start postgresql
```

Create and setup the database:

```bash
bin/rails db:create
bin/rails db:migrate
bin/rails db:seed  # Optional: Load sample data
```

## Development

### Running the Application

The easiest way to run both Rails and Vite servers concurrently is using the Procfile.dev:

#### Option 1: Using Foreman (Recommended)

```bash
gem install foreman
foreman start -f Procfile.dev
```

#### Option 2: Manual Start (Two Terminal Windows)

Terminal 1 - Rails Server:
```bash
bin/rails server
```

Terminal 2 - Vite Dev Server:
```bash
bin/vite dev
```

The application will be available at:
- Rails app: http://localhost:3000
- Vite dev server: http://localhost:3036

### Database Commands

```bash
# Create databases
bin/rails db:create

# Run migrations
bin/rails db:migrate

# Rollback last migration
bin/rails db:rollback

# Reset database (drop, create, migrate, seed)
bin/rails db:reset

# Access Rails console
bin/rails console
```

## Production Deployment

### Asset Compilation

Build assets for production:

```bash
npm run build
```

### Environment Variables

Required environment variables for production:

- `RAILS_MASTER_KEY`: Rails master encryption key
- `DATABASE_URL`: PostgreSQL connection URL
- `MOVIE_ZONE_V2_DATABASE_PASSWORD`: Database password (if not using DATABASE_URL)

## Testing

Run the test suite:

```bash
bin/rails test
```

Run system tests:

```bash
bin/rails test:system
```

## Project Structure

```
movie-zone-v2/
├── app/
│   ├── assets/          # Static assets (images, stylesheets)
│   ├── channels/        # ActionCable channels
│   ├── controllers/     # Rails controllers
│   ├── helpers/         # View helpers
│   ├── javascript/      # Vite-managed JavaScript
│   │   ├── controllers/ # Stimulus controllers
│   │   └── entrypoints/ # Vite entry points
│   ├── jobs/            # ActiveJob classes
│   ├── mailers/         # ActionMailer classes
│   ├── models/          # ActiveRecord models
│   └── views/           # ERB view templates
├── config/              # Application configuration
│   ├── vite.json        # Vite Ruby configuration
│   └── database.yml     # Database configuration
├── db/                  # Database files
│   ├── migrate/         # Database migrations
│   └── seeds.rb         # Seed data
├── public/              # Static files served directly
├── test/                # Test files
├── Gemfile              # Ruby dependencies
├── package.json         # Node.js dependencies
├── vite.config.mts      # Vite configuration
└── Procfile.dev         # Development process configuration
```

## Key Features

### Vite Integration

This application uses Vite for fast, modern asset bundling:

- **Hot Module Replacement (HMR)**: Changes to JavaScript/CSS reflect immediately
- **Fast builds**: Optimized production builds
- **Modern JavaScript**: Support for ES modules and latest JavaScript features

### Hotwire Stack

- **Turbo**: SPA-like navigation without writing JavaScript
- **Stimulus**: Modest JavaScript framework for sprinkles of interactivity

## Troubleshooting

### Database Connection Issues

If you encounter database connection errors:

1. Ensure PostgreSQL is running
2. Check database credentials in `config/database.yml`
3. Verify the database user has appropriate permissions

### Vite Build Errors

If Vite fails to build:

1. Clear node_modules and reinstall: `rm -rf node_modules && npm install`
2. Check Node.js version: `node --version` (should be 20.x)
3. Clear Vite cache: `rm -rf public/vite*`

### Rails Server Won't Start

1. Check for port conflicts: `lsof -i :3000`
2. Clear tmp files: `bin/rails tmp:clear`
3. Check logs: `tail -f log/development.log`

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is available as open source under the terms of the [MIT License](LICENSE).

## Support

For issues and questions, please open an issue on the GitHub repository.

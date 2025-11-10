# Faleproxy

A Node.js web application that fetches a URL, replaces every instance of "Yale" with "Fale" in the document, and displays the modified content.

## Features

- Simple and intuitive user interface
- Fetches web content from any URL
- Replaces all instances of "Yale" with "Fale" while preserving case (Yale→Fale, yale→fale, YALE→FALE)
- Preserves URLs and attributes containing "yale" unchanged
- Displays the modified content in an iframe
- Shows original URL and page title in an info bar

## Installation

1. Clone this repository
2. Navigate to the project directory
3. Install dependencies:

```bash
npm install
```

## Usage

1. Start the server:

```bash
npm start
```

2. Open a browser and go to `http://localhost:3001`
3. Enter a URL in the input field (e.g., https://www.yale.edu)
4. Click "Fetch & Replace" to see the modified content

## Development

To run with auto-restart on file changes:

```bash
npm run dev
```

## Testing

The application includes a comprehensive test suite:

- **Unit tests**: Test the Yale-to-Fale replacement logic
- **API tests**: Test the application endpoints
- **Integration tests**: Test the entire application workflow

### Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode during development
npm run test:watch

# Run tests with coverage for CI/CD
npm run test:ci
```

## CI/CD Pipeline

The repository includes a GitHub Actions workflow configuration in `.github/workflows/ci.yml` that:

1. Runs on pushes to main/master branches and on pull requests
2. Tests the application on multiple Node.js versions (18.x, 20.x)
3. Generates and uploads test coverage reports
4. Automatically deploys to Vercel production (only when tests pass on main/master)
5. Creates preview deployments for feature branches

**Important**: Deployment to production only occurs when all tests pass, ensuring code quality.

### Setting up Vercel Deployment

To enable automatic deployments to Vercel, you need to:

1. Create a Vercel account and link your repository
2. Create a Vercel project for your application
3. Run `vercel link` in your project directory to get your Vercel IDs
4. Add the following secrets to your GitHub repository (Settings → Secrets → Actions):
   - `VERCEL_TOKEN`: Your Vercel API token
   - `VERCEL_ORG_ID`: Your Vercel organization ID (from `.vercel/project.json`)
   - `VERCEL_PROJECT_ID`: Your Vercel project ID (from `.vercel/project.json`)

## Technologies Used

- Node.js
- Express - Web server framework
- Axios - HTTP client for fetching web pages
- Cheerio - HTML parsing and manipulation
- Vanilla JavaScript for frontend functionality
- Jest, Supertest, and Nock for testing

# Gist.ai Website Replicator

A comprehensive website replication system that can extract, clone, and replicate any article website or webpage with complete fidelity and error resilience.

## 🚀 Features

- **Multi-browser support**: Puppeteer and Playwright
- **Parallel asset downloading**: Configurable concurrency for optimal performance
- **Intelligent asset detection**: Discovers all types of web resources
- **HTML rewriting**: Updates all asset references to local paths
- **Error handling**: Comprehensive retry mechanisms with exponential backoff
- **Circuit breaker pattern**: Prevents cascading failures
- **Structured logging**: Correlation IDs for request tracing
- **Security**: Respects robots.txt, rate limiting, and proper user agent identification
- **Monitoring**: Health checks and performance metrics
- **Docker support**: Production-ready containerization

## 📋 Prerequisites

- Node.js 16+ 
- npm or yarn
- Chrome/Chromium browser (for Puppeteer)

## 🛠️ Installation

1. Clone the repository:
```bash
git clone https://github.com/gist-ai/website-replicator.git
cd website-replicator
```

2. Install dependencies:
```bash
npm install
```

3. Run health check:
```bash
npm run health
```

## 💻 Usage

### Command Line Interface

```bash
# Basic replication
npm start replicate https://example.com

# Custom output directory
npm start replicate https://example.com -o ./my-output

# Use Playwright instead of Puppeteer
npm start replicate https://example.com --engine playwright

# Skip asset downloading (HTML only)
npm start replicate https://example.com --no-assets

# Preserve original links in HTML
npm start replicate https://example.com --preserve-links

# Increase download concurrency
npm start replicate https://example.com --max-concurrency 10

# Custom timeout
npm start replicate https://example.com --timeout 60000
```

### Programmatic Usage

```javascript
const WebsiteReplicator = require('./src/index');

const replicator = new WebsiteReplicator({
  outputDir: './replicated-sites',
  browserEngine: 'puppeteer',
  includeAssets: true,
  maxConcurrency: 5,
  timeout: 30000
});

async function replicateWebsite() {
  try {
    const report = await replicator.replicateWebsite('https://example.com');
    console.log('Replication completed:', report);
  } catch (error) {
    console.error('Replication failed:', error);
  }
}

replicateWebsite();
```

## 🐳 Docker Usage

### Build and run with Docker:

```bash
# Build the image
docker build -t gist-replicator .

# Run replication
docker run --rm -v $(pwd)/output:/app/replicated-sites gist-replicator \
  node src/index.js replicate https://example.com

# Run with docker-compose
docker-compose up
```

## 📁 Output Structure

```
replicated-sites/
└── example_com_2024-01-15T10-30-00-000Z/
    ├── index.html              # Main HTML file
    ├── metadata.json           # Replication metadata
    ├── screenshot.png          # Full page screenshot
    ├── replication-report.json # Detailed report
    └── assets/
        ├── images/             # Downloaded images
        ├── css/               # Stylesheets
        ├── js/                # JavaScript files
        ├── fonts/             # Web fonts
        └── misc/              # Other assets
```

## 🔧 Configuration Options

| Option | Default | Description |
|--------|---------|-------------|
| `outputDir` | `./replicated-sites` | Output directory for replicated sites |
| `browserEngine` | `puppeteer` | Browser engine (`puppeteer` or `playwright`) |
| `maxConcurrency` | `5` | Maximum concurrent asset downloads |
| `timeout` | `30000` | Request timeout in milliseconds |
| `includeAssets` | `true` | Download and include assets |
| `optimizeImages` | `true` | Optimize downloaded images |
| `preserveOriginalLinks` | `false` | Keep original URLs as data attributes |
| `headless` | `true` | Run browser in headless mode |

## 📊 Monitoring and Logging

The system provides comprehensive logging and monitoring:

- **Structured logs**: JSON formatted with correlation IDs
- **Health checks**: Browser engine availability and system status
- **Performance metrics**: Download speeds, success rates, error patterns
- **Error tracking**: Categorized errors with retry strategies
- **Circuit breakers**: Automatic failure isolation

## 🧪 Testing

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run tests in watch mode
npm run test:watch

# Health check
npm run health
```

## 🚨 Error Handling

The system implements sophisticated error handling:

- **Categorized errors**: Network, HTTP, browser, parsing errors
- **Retry mechanisms**: Exponential backoff with jitter
- **Circuit breakers**: Prevents cascading failures
- **Graceful degradation**: Continues operation despite individual failures

## 🔒 Security and Compliance

- **Rate limiting**: Respects server resources
- **User agent identification**: Proper identification as a bot
- **Robots.txt respect**: Honors robot exclusion protocols
- **Content filtering**: Excludes sensitive content types
- **Access controls**: Authorized user verification

## 📈 Performance Optimization

- **Parallel processing**: Concurrent downloads with configurable limits
- **Resource blocking**: Skip unnecessary resources for faster extraction
- **Memory management**: Efficient buffer handling
- **Caching**: Optional Redis integration for improved performance

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Run the test suite
6. Submit a pull request

## 📄 License

MIT License - see LICENSE file for details.

## 🆘 Support

For issues and questions:
- Create an issue on GitHub
- Check the troubleshooting guide in `docs/TROUBLESHOOTING.md`
- Review the API documentation in `docs/API.md`

## 🎯 Use Cases

Perfect for:
- **Content archiving**: Preserve websites for historical reference
- **Offline browsing**: Create local copies of important content
- **Demo preparation**: Replicate websites for investor presentations
- **Testing**: Create static copies for testing purposes
- **Backup**: Maintain copies of critical web content

---

**Built with ❤️ by the Gist.ai team**# gist-website-replicator

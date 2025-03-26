# DataFlow Support Chatbot

An AI-powered conversational customer support chatbot for DataFlow, a fictional SaaS data analytics and visualization platform.

## Features

- Interactive chat interface with AI-powered responses
- Knowledge base with 15 documents about the fictional product
- Context-aware conversation handling
- Fallback mechanism for unknown queries
- Basic analytics dashboard
- Responsive design with Tailwind CSS

## Tech Stack

- Vue.js 3 (Composition API)
- Tailwind CSS for styling
- Chart.js for analytics visualization
- Vite for build and development

## Project Setup

### Prerequisites

- Node.js (v14 or higher)
- npm (v6 or higher)

### Standard Setup

```bash
# Install dependencies
npm install

# Start development server
npm run dev
```

The application will be available at http://localhost:3000

### Docker Setup (Recommended)

For a consistent development environment, you can use Docker:

```bash
# Build and start the container
docker-compose up
```

The application will be available at http://localhost:3000

### Additional Commands

```bash
# Build for production
npm run build

# Preview production build
npm run preview
```

## Environment Variables

Create a `.env` file in the root directory with the following variables:

```
VITE_GOOGLE_AI_STUDIO_KEY=your_api_key_here
```

## Project Structure

```
├── public/              # Static assets
├── src/                 # Source files
│   ├── assets/          # CSS and other assets
│   ├── components/      # Vue components
│   ├── config/          # Configuration files
│   ├── data/            # Knowledge base data
│   ├── services/        # API services
│   ├── App.vue          # Main application component
│   └── main.js          # Application entry point
├── .env                 # Environment variables (create this file)
├── package.json         # Dependencies and scripts
├── vite.config.js       # Vite configuration
└── docker-compose.yml   # Docker configuration
```

## How It Works

The chatbot uses a simple but effective matching algorithm to find the most relevant information from the knowledge base based on the user's query. It matches keywords and content to provide accurate responses.

The system includes:

1. A comprehensive knowledge base with information about the fictional SaaS product
2. Context-aware conversation handling to maintain conversation flow
3. A fallback mechanism for queries that don't match any knowledge base entries
4. Basic analytics to track user interactions and popular questions

## API Integration

The chatbot is designed to work with Google AI Studio API. To enable AI-powered responses:

1. Obtain an API key from Google AI Studio
2. Add your API key to the `.env` file as shown in the Environment Variables section

## Customization

To customize the chatbot for a different product:

1. Update the knowledge base in `src/data/knowledgeBase.js`
2. Modify the UI in the Vue components as needed
3. Adjust the matching algorithm in the `findBestMatch` function if necessary

## Troubleshooting

- **API Key Issues**: Ensure your Google AI Studio API key is correctly set in the `.env` file
- **Build Errors**: Make sure all dependencies are installed with `npm install`
- **Docker Issues**: Ensure Docker is running and ports are not in use

## License

MIT
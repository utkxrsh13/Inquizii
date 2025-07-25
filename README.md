# AI Quiz Generator (Inquizi)

A full-stack application that generates intelligent quiz questions from text content or uploaded documents using AI.

## Features

- 📄 **Multiple Input Methods**: Support for direct text input, PDF, and DOCX files
- 🤖 **AI-Powered**: Uses advanced AI to generate intelligent questions
- 🎯 **Interactive Quiz**: Take quizzes with immediate feedback
- 📊 **Score Tracking**: Get instant results with detailed feedback
- 🎨 **Modern UI**: Clean, responsive interface built with React and Tailwind CSS

## Project Structure

```
Galelio/
├── client/                 # React + TypeScript frontend
│   ├── src/
│   │   ├── components/     # React components
│   │   ├── api/           # API service layer
│   │   ├── types/         # TypeScript type definitions
│   │   └── App.tsx        # Main application component
│   ├── package.json
│   └── vite.config.ts
├── server/                 # FastAPI backend
│   ├── services/          # Business logic services
│   │   ├── quiz_generator.py
│   │   └── file_parser.py
│   ├── main.py           # FastAPI application
│   ├── models.py         # Pydantic models
│   └── requirements.txt
└── README.md
```

## Setup Instructions

### Prerequisites

- Python 3.8+
- Node.js 16+
- npm or yarn

### Backend Setup

1. Navigate to the server directory:
   ```bash
   cd server
   ```

2. Create a virtual environment:
   ```bash
   python -m venv venv
   venv\\Scripts\\activate  # On Windows
   # source venv/bin/activate  # On macOS/Linux
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the server directory:
   ```env
   HUGGINGFACEHUB_API_TOKEN=your_huggingface_token_here
   ```

5. Start the backend server:
   ```bash
   python -m uvicorn main:app --reload --host 0.0.0.0 --port 8000
   ```

### Frontend Setup

1. Navigate to the client directory:
   ```bash
   cd client
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```

## Usage

1. **Access the Application**: Open your browser and go to `http://localhost:5173`

2. **Generate Quiz Questions**:
   - **Text Input**: Paste your content directly into the text area (minimum 50 characters)
   - **File Upload**: Drag and drop or select a PDF/DOCX file (max 10MB)

3. **Take the Quiz**:
   - Select answers for each question
   - Click "Submit Quiz" to see results
   - Get instant feedback with correct answers highlighted

4. **Generate New Quiz**: Click "Generate New Quiz" to start over

## API Endpoints

### Backend API (http://localhost:8000)

- `GET /` - Health check
- `POST /generate` - Generate quiz from text input
- `POST /upload` - Generate quiz from uploaded file

### Example API Usage

```javascript
// Generate quiz from text
const response = await fetch('http://localhost:8000/generate', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ content: 'Your text content here...' })
});

// Generate quiz from file
const formData = new FormData();
formData.append('file', fileInput.files[0]);
const response = await fetch('http://localhost:8000/upload', {
  method: 'POST',
  body: formData
});
```

## Technologies Used

### Frontend
- **React 19** - UI framework
- **TypeScript** - Type safety
- **Tailwind CSS** - Styling
- **Vite** - Build tool and dev server

### Backend
- **FastAPI** - Web framework
- **Python** - Programming language
- **Uvicorn** - ASGI server
- **Pydantic** - Data validation
- **Hugging Face Inference Client** - AI integration

## Recent Fixes

### Backend Improvements
- ✅ Fixed quiz parsing algorithm to handle AI-generated content better
- ✅ Added proper error handling for malformed responses
- ✅ Improved prompt engineering for consistent question format
- ✅ Added CORS support for frontend integration
- ✅ Enhanced fallback mechanism when parsing fails

### Frontend Features
- ✅ Complete responsive UI with Tailwind CSS
- ✅ Drag-and-drop file upload functionality
- ✅ Real-time character counting for text input
- ✅ Interactive quiz with answer selection
- ✅ Immediate feedback and scoring system
- ✅ Tab-based navigation between input methods
- ✅ Loading states and error handling

## Troubleshooting

### Common Issues

1. **CORS Errors**: Ensure the backend server is running on port 8000 and CORS is configured
2. **File Upload Issues**: Check file size (max 10MB) and format (PDF/DOCX only)
3. **API Token**: Make sure your Hugging Face API token is set in the `.env` file
4. **Port Conflicts**: Ensure ports 8000 (backend) and 5173 (frontend) are available

### Development Tips

- Use the browser's Developer Tools to monitor network requests
- Check the backend logs for detailed error messages
- The frontend shows user-friendly error messages for common issues

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source and available under the MIT License.

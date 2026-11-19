# Document Digitizer

An OCR-powered web application for digitizing scanned documents, extracting text, translating regional languages, and exporting the results into multiple document formats.

## Features

- **Document Upload:** Upload scanned documents in PDF, PNG, JPG, and JPEG formats.
- **Text Extraction:** Extract text from documents using Tesseract OCR.
- **PDF Processing:** Process multi-page PDF documents and combine extracted text.
- **Regional Language Support:** Work with multiple Indian languages and scripts, including Tamil, Hindi, Telugu, Kannada, Malayalam, Bengali, Gujarati, Odia, Punjabi, and Urdu.
- **Text Translation:** Translate extracted content between supported languages using Google Translate integration.
- **Document Editing:** Review and edit extracted or translated text through an interactive editor.
- **Multi-format Export:** Download processed content as TXT, PDF, or DOCX files.
- **Indic Font Support:** Use bundled Noto fonts to support regional scripts in exported documents.
- **User Authentication:** Manage access to application pages through Clerk authentication.

## Technology Stack

**Frontend**
- React
- TypeScript
- Vite
- Tailwind CSS
- Clerk

**Backend**
- Python
- Flask
- Tesseract OCR
- OpenCV
- Googletrans
- FPDF
- python-docx

## Project Structure

```text
document-digitizer/
├── code/
│   ├── backend/
│   │   ├── app.py
│   │   ├── requirements.txt
│   │   ├── fonts/
│   │   ├── assets/
│   │   └── services/
│   │       ├── document_processor.py
│   │       ├── image_preprocessor.py
│   │       ├── preprocess_image.py
│   │       ├── ocr_processor.py
│   │       ├── text_translator.py
│   │       ├── text_postprocessor.py
│   │       └── document_converter.py
│   │
│   └── frontend/
│       ├── public/
│       ├── src/
│       │   ├── components/
│       │   ├── pages/
│       │   ├── sections/
│       │   ├── services/
│       │   │   └── api.ts
│       │   └── markdowns/
│       ├── .env.example
│       ├── package.json
│       └── vite.config.ts
│
├── review/
├── niral_thiruvizha/
└── README.md
```

## Getting Started

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- **Node.js** (for frontend)
- **Python 3.x** (for backend)
- **Tesseract OCR** (for text extraction)
- **Poppler** (for PDF processing)

You can install them as follows:

1. **Node.js:** [Install Node.js](https://nodejs.org/)
2. **Python 3.x:** [Install Python](https://www.python.org/)
3. **Tesseract OCR:** [Install Tesseract OCR](https://github.com/tesseract-ocr/tesseract)
4. **Poppler:**
   - **Linux:** `sudo apt-get install poppler-utils`
   - **MacOS:** `brew install poppler`
   - **Windows:** [Install Poppler on Windows](http://blog.alivate.com.au/poppler-windows/)


### 1. Backend Setup

Navigate to the backend directory:

```bash
cd code/backend
```

Create and activate a Python virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

On Windows, activate it using:

```bash
.venv\Scripts\activate
```

Install the Python dependencies:

```bash
pip install -r requirements.txt
```

Start the Flask server:

```bash
flask run
```

The backend runs at:

```text
http://localhost:5000
```

### 2. Frontend Setup

Open another terminal and navigate to the frontend directory:

```bash
cd code/frontend
```

Install the dependencies:

```bash
npm install
```

Create an environment file:

```bash
cp .env.example .env
```

Configure the required environment variables:

```env
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
VITE_CLERK_SIGN_IN_URL=/login
VITE_CLERK_SIGN_UP_URL=/register
VITE_API_BASE_URL=http://localhost:5000/api
```

Replace the Clerk publishable key with your own Clerk application key.

Start the frontend development server:

```bash
npm run dev
```

Open the local URL displayed in the terminal, typically:

```text
http://localhost:5173
```

## Application Workflow

1. Upload a scanned document or PDF.
2. Select the source language or use automatic language detection.
3. Extract text using the OCR processing pipeline.
4. Review and edit the extracted content in the document editor.
5. Select a target language to translate the text if required.
6. Export the final content as TXT, PDF, or DOCX.

## Backend API

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Backend health check |
| POST | `/api/extract` | Extract text from an uploaded document |
| POST | `/api/translate` | Translate extracted text |
| POST | `/api/convert` | Convert text into TXT, PDF, or DOCX |

## Implementation Notes

- The backend uses Tesseract OCR for text extraction.
- PDF documents are converted into images using Poppler before OCR processing.
- Googletrans is used for translation.
- Noto fonts are bundled to support regional language scripts in exported documents.
- Image preprocessing experiments are available in `preprocess_image.py`; the current `image_preprocessor.py` implementation does not yet integrate those processing techniques.
- The application uses a Flask REST API to connect the frontend and backend.


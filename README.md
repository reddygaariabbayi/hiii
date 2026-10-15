# SmartFoodGuard — Full-Stack BTech Final-Year Project

AI-assisted personalized food-product dietary concern assessment.

## Exact user flow

1. Register/login.
2. Upload a clear image of a packaged-food Nutrition Facts or Ingredients label.
3. Select age:
   Child / Teenager / Young adult / Middle-aged adult / Older adult.
4. Select optional health/dietary considerations:
   Diabetes, high blood pressure, thyroid-related condition, high cholesterol,
   kidney-related dietary restriction, heart-related dietary restriction,
   weight-management goal.
5. Enter allergies and diet preference.
6. Backend extracts label information with Tesseract OCR.
7. Optional Gemini Vision can be enabled for multimodal extraction.
8. Personalized deterministic rules generate a transparent Dietary Concern Score.
9. Frontend displays a detailed report.

## Important meaning of the percentage

The "Dietary Concern Score (%)" is a project-specific decision-support score.
It is NOT a probability of illness, medical risk probability, diagnosis, or guarantee
that a product is safe/unsafe.

Prototype rule weights must be validated against authoritative nutrition guidance
before publication in an IEEE paper.

## Windows setup

### Backend
```powershell
cd backend
python -m venv .venv
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
copy .env.example .env
uvicorn app.main:app --reload --port 8000
```

Open: http://127.0.0.1:8000/docs

### Tesseract
Install a Windows Tesseract build separately.
Then:
```powershell
where.exe tesseract
tesseract --version
```
If it is not on PATH, set TESSERACT_CMD in backend/.env.

### Frontend
Open another PowerShell:
```powershell
cd frontend
npm install
npm run dev
```
Open: http://localhost:5173

### Optional Gemini
Set GEMINI_API_KEY and GEMINI_MODEL in backend/.env.
If Gemini is not configured, local OCR remains available.

## Research
The research contribution is a hybrid pipeline:
image extraction + validation + personalized deterministic rules + explainable report.
Do not fabricate datasets, thresholds, experimental results or medical claims.

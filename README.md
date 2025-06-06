# 🧠 Suicide Risk Detector

A web-based AI application that analyzes user-submitted text to detect signs of suicidal intent using a machine learning model. The app predicts whether the text is **suicidal** or **not suicidal**, along with a risk-level assessment (e.g., NONE, MODERATE, HIGH). It’s designed for awareness, not diagnosis—think of it as a friendly (and slightly nosy) AI buddy, not a therapist replacement.

---

## 🚀 Features

- 🔍 **Real-Time Detection**  
  Paste or type any text and get an immediate assessment. It’s like having an AI-powered “OMG, are you okay?” whisper in your ear.

- 🤖 **Robust Backend**  
  Python + Flask serve up a trained deep learning model (`.h5`) that learned everything it knows from a dataset of real-world sentences. Don’t worry—no psychic powers, just good old TensorFlow.

- 🖥️ **Sleek React Frontend**  
  Modern, responsive, and friendly UI. Designed so that even your least tech-savvy friend can figure out where to paste their existential poetry.

- ⚡ **Risk Level Breakdown**  
  - **NONE** (Everything’s cool, keep scrolling memes.)  
  - **MODERATE** (Take a breath; maybe talk to a friend.)  
  - **HIGH** (Consider reaching out to a professional—or at least a really good pet.)

- 📊 **Confidence Scores** (Optional)  
  Want to know how sure the model is? Toggle on a confidence-percentage display to see if it’s 99% sure or just “pretty darn confident.” (Hint: we recommend trusting a human more than math sometimes.)

---

## 🛠️ Tech Stack

| Layer        | Tech Stack                                                             | Why We Chose It                                                           |
|--------------|------------------------------------------------------------------------|---------------------------------------------------------------------------|
| **Frontend** | React.js, React Hooks, CSS Modules/BEM                                  | Fast, component-based, and keeps our CSS sane-ish.                        |
| **Backend**  | Python 3.9+, Flask, Gunicorn (for production), Flask-CORS                | Lightweight, familiar, and deploys easily to Heroku or any VPS.           |
| **ML Model** | TensorFlow / Keras (`model.h5`), scikit-learn (preprocessing), NLTK      | Proven libraries, good documentation, and a large community of nerds.      |
| **Styling**  | CSS3, Bootstrap (optional utility classes), Google Fonts (“Inter” & “Roboto”) | Looks nice out-of-the-box; we customized to match our brand guidelines.    |
| **Data**     | Custom-labeled dataset of suicidal vs. non-suicidal text (public & private)   | Built from a combination of public posts and curated expert-reviewed samples. |
| **Version Control** | Git + GitHub                                                         | For managing code changes, issue tracking, and not losing your life’s work. |

---

## 📚 How It Works (Under the Hood)

1. **Text Input**  
   - You paste your text into the web form.  
   - On “Analyze,” the frontend packages it as JSON and sends it to the backend via a POST request.

2. **Preprocessing**  
   - The Flask server tokenizes the text, removes stopwords, converts to lowercase, and pads/truncates sequences to a fixed length.  
   - If you wrote “I’m not feeling great,” it’ll break down into tokens like `["im", "not", "feeling", "great"]` before sending to the model.

3. **Model Inference**  
   - The preprocessed sequence goes into our Keras model (`model.h5`).  
   - The model outputs a probability distribution over classes: `{ suicidal: 0.12, not_suicidal: 0.88 }`.

4. **Risk Level Assignment**  
   - If `suicidal_probability > 0.7`, label = **HIGH**.  
   - If `0.3 < suicidal_probability <= 0.7`, label = **MODERATE**.  
   - Else, label = **NONE**.

5. **Response to Frontend**  
   - Backend returns JSON:  
     ```json
     {
       "final_result": "Not Suicidal",
       "risk_level": "NONE",
       "model_confidence": 0.88
     }
     ```  
   - Frontend displays the result card, complete with friendly colors:  
     - **Green** for “NONE” (whee! 🎉)  
     - **Yellow** for “MODERATE” (caution: take a break ☕)  
     - **Red** for “HIGH” (please reach out 🙏).

---

## ⚙️ Local Setup

> **Note:** This guide assumes you have Python 3.9+ and Node.js (v14+) installed. If not, go install them now. We’ll wait. 🕒

### 1. Clone the Repo

```bash
git clone https://github.com/Lightinw/SuicideWatch.git
cd SuicideWatch
```

### 2. Start the backend (Flask + model)
```bash
cd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

### 3. Start the frontend (React)
```bash
cd ../frontend
npm install
npm start
```

## 🧠 Model Info

- Trained on a carefully labeled dataset of **"I'm fine"** vs **"I'm definitely not fine"** texts.
- Powered by **Keras + TensorFlow**, aka the peanut butter and jelly of deep learning.
- Saved as `model.h5`, because `.h5` just sounds cooler than `.pickle`.
- Want to give the model new brain cells? Just retrain it with your own data!

---

## ⚠️ Disclaimer

> ⚠️ This AI is **not a licensed therapist**, doctor, or even your nosy aunt.  
It’s a tool for **awareness and education**, not diagnosis.  
If you or someone you know is struggling, please contact a real, living, breathing **mental health professional**. Or at least a very wise cat.

---

## 🤝 Contributing

Love fixing typos at 2AM? Got a wild idea for the next killer feature?  
We welcome **pull requests**, **issues**, and **enthusiastic commits**!

To contribute your genius:

```bash
git fork https://github.com/Lightinw/SuicideWatch.git
git checkout -b i-got-this
```

Add your magic, then:

```bash
git commit -m "Added emotional support duck"
git push origin i-got-this
```

Open a Pull Request, sprinkle emojis, and boom — you’re now an open-source hero.

---

## 📬 Contact

**Aniket Wani**  
🔗 GitHub: [Lightinw](https://github.com/Lightinw)

Slide into my inbox (for project questions, not therapy sessions 😅).  
Always happy to talk code, AI ethics, or how to train models with memes.

---

## ⭐️ Support

If this project made you smile, helped your research, or saved you from a really bad regex —  
give it a ⭐️ on GitHub! It fuels future features and prevents dev burnout.


# Resume_Matching System Using NLP

Objective : Build a system that automatically ranks resumes based on their similarity to a job description using NLP techniques.

Dataset:

Resumes CSV: resumes.csv

Columns:
resume_id
resume_text 
experience → Years of experience (optional, can be used later)

job_description.txt:  Plain text of the job posting

Note: Both files are small and synthetic .

🔹Key Concept Used:

1️⃣ Preprocessing
.lower() → all text lowercase
re.sub(r'[^a-z\s]', '', text) → remove numbers/punctuation
Stopwords removal → remove common filler words like “the”, “is”

2️⃣ TF-IDF
Converts text into numeric vectors
fit_transform(documents) → learn vocabulary + compute IDF
JD is first element, resumes follow → easy indexing

3️⃣ Cosine Similarity
tfidf_matrix[0:1] → JD
tfidf_matrix[1:] → resumes
.flatten() → 1D array for easy ranking

4️⃣ Ranking
Add match_score column to DataFrame
sort_values(by="match_score", ascending=False) → rank from most relevant to least
Keeps all resume info (name, email, experience) together

5️⃣ Top N resumes
Slice DataFrame → recruiter sees best matches quickly

🔹 Business Interpretation
Higher match_score → more relevant resume
Recruiter can focus on top candidates
TF-IDF + cosine similarity considers word importance and context


**Future Improvements:**

Combine experience with similarity score
Use dynamic keyword weighting based on JD
Use semantic embeddings(BERT, Sentence Transformers) for better understanding of text meaning
Build a web interface for recruiters to upload JD and view ranked resumes

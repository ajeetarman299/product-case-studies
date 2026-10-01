# FAQ chatbot: a product review of my own RAG assistant

Code: [Question-Answering-ChatBot-System-Development](https://github.com/ajeetarman299/Question-Answering-ChatBot-System-Development)

I built a retrieval-augmented chatbot that answers student questions from an e-learning company's FAQ sheet. This page reviews it as a product: would I ship it to students, and what would I measure?

## The user and the job

Learners ask the same questions over and over on Discord and email. The job is a correct answer in seconds, taken only from the official FAQ, so staff handle fewer repeat questions.

## What the prototype showed

| Behaviour | Example | Product read |
|---|---|---|
| Handles paraphrase | "how about job placement support?" finds the job-assistance FAQ | Good. Users never use the FAQ's wording |
| Merges two-part questions | Internship and EMI answered in one reply | Good when both parts are in the FAQ, risky when one is missing |
| Declines unknowns | "do you have javascript course?" gets "I don't know." | Right call. A wrong "yes" costs more than a decline |

## Launch criteria

1. **Grounded.** Every answer shows the source FAQs it used. The app already does this.
2. **Honest refusal.** A question outside the FAQ gets a decline, never a guess.
3. **Two-part questions.** Each part is answered or declined on its own.
4. **Deflection.** The business metric: the share of questions answered without staff.

## What I would change before launch

- **Hand off, don't dead-end.** Replace a bare "I don't know." with a route to staff on Discord or email.
- **Log the declines.** Declined questions are the backlog for new FAQ entries.
- **Keep a fixed test set.** Re-run a set of real student questions on every model change. This is not hypothetical: Google shut down PaLM, and the app had to move to Gemini.

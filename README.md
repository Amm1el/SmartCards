# SmartCards

An AI flashcard generator. Paste in your notes or a topic, and SmartCards turns them into a set of study flashcards you can flip through, save, and come back to on any device.

**Live site:** https://ai-flashcards-black.vercel.app

## Features

- **AI generation:** sends your text to the OpenAI API with a structured prompt and gets back 10 flashcards as JSON (front and back).
- **Study mode:** click a card to flip between the question and the answer.
- **Saved sets:** name a set and save it to your account; your sets are listed on the Flashcards page.
- **Accounts:** sign up and sign in with Clerk.
- **Payments:** Basic and Pro subscription plans through Stripe Checkout.

## How it works

1. `/api/generate` sends the input text and a system prompt to the OpenAI Chat Completions API, which returns flashcards as JSON.
2. Saved sets are written to **Firebase Firestore** under `users/{userId}`, with one subcollection per set.
3. `/api/checkout_session` creates a Stripe Checkout session for the selected plan, and the result page confirms the payment.

## Tech stack

| Layer | Tools |
|---|---|
| Frontend | Next.js 14, React, Material UI |
| AI | OpenAI API |
| Auth | Clerk |
| Database | Firebase Firestore |
| Payments | Stripe Checkout |
| Hosting | Vercel |

## Run locally

```bash
git clone https://github.com/Amm1el/SmartCards.git
cd SmartCards
npm install
npm run dev
```

Create `.env.local` with:

| Variable | Description |
|---|---|
| `OPENAI_API_KEY` | OpenAI API key |
| `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` | Clerk publishable key |
| `CLERK_SECRET_KEY` | Clerk secret key |
| `STRIPE_SECRET_KEY` | Stripe secret key |
| `NEXT_PUBLIC_STRIPE_PUBLIC_KEY` | Stripe publishable key |

Firebase project settings live in `firebase.js`.

## Context

Built during the Headstarter AI Software Engineering Fellowship (Summer 2024).

## Author

Ammiel Bowen · [ammielbowen.com](https://ammielbowen.com) · [LinkedIn](https://www.linkedin.com/in/ammielbowen/)

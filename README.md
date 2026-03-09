# BayMax - E-Commerce Shopping Assistant

## What it does
BayMax is a conversational, voice-enabled AI shopping assistant designed to streamline the online e-commerce experience. It acts as a personal shopping concierge that allows users to search for products, apply filters, explore top brands, check out daily deals, and retrieve detailed product reviews directly through a chat interface. By leveraging data scraped live from Amazon, BayMax provides users with up-to-date pricing, availability, and delivery information. It solves the problem of overwhelming product discovery by guiding users through a seamless, interactive conversational flow.

## How I built it
**Stack:** Python, Rasa, Flask, BeautifulSoup, PyTorch, HTML/CSS/JS

- **Rasa Framework:** Used for robust Natural Language Understanding (NLU) and dialogue management, allowing the bot to handle complex, multi-turn conversations and contextual entity extraction (e.g., maintaining state for product filters and options).
- **BeautifulSoup & Requests:** Implemented live web scraping to fetch real-time product search results, reviews, and daily deals directly from Amazon, ensuring the displayed data is never stale.
- **Voice Synthesis (SV2TTS):** A state-of-the-art Real-Time Voice Cloning system built with PyTorch and served via a Flask backend. It utilizes an encoder, synthesizer (Tacotron), and vocoder to generate natural-sounding speech for the bot's responses.
- **Frontend UI:** Constructed with HTML, CSS (Bootstrap/Materialize), and JavaScript to provide a responsive web chat interface capable of rendering complex media like product cards, carousels, and suggestion buttons.

## What was hard
- **Dynamic Web Scraping:** Amazon frequently changes its DOM structure and employs strict anti-bot measures. Extracting consistent product data (prices, images, variants, and reviews) required writing robust fallback parsing logic and handling varying HTML class names to ensure the pipeline didn't break during live interactions.
- **Voice Synthesis Integration:** Running a real-time voice cloning pipeline with multiple heavy deep learning models (Encoder, Synthesizer, Vocoder) locally is highly resource-intensive. Managing model weights, audio processing (`librosa`), and spectrogram generation within a synchronous Flask API without causing severe memory leaks or timeout issues was a major technical hurdle.
- **Contextual State Management:** Handling multi-turn e-commerce dialogues in Rasa—such as sequentially searching for a product, filtering by brand, and then isolating a specific option to view full details—required complex custom actions (`actions.py`) and careful slot-filling logic to persist the user's focus across the entire session.

## Results / Impact
- **Hackathon Success:** Successfully built and showcased a "Level 3" conversational agent for the Deep Vision Tech Hackathon (Team Octave) capable of autonomous product discovery.
- **Time Saved:** Centralized product discovery, daily deals, and review aggregation into a single chat window, eliminating the need for users to manually browse and tab-switch across traditional e-commerce catalogs.
- **Enhanced Accessibility:** The integration of the custom text-to-speech engine empowered the bot to generate realistic audio responses, creating a more engaging and accessible hands-free user experience compared to a standard text-only interface.

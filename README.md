# TensorFlow Veggie Cooking Chat
This is a simple web-based chat application that answers questions about cooking vegetables (broccoli, carrots, and zucchini) using TensorFlow.js. It uses a static JSON dataset with pre-trained question embeddings to match user questions to the best answer. The app displays the answer, cooking time, difficulty, and the math behind the matching process (cosine similarity). If no good match is found, it says "I don't know."

## How It Works (In Simple Terms)

The app uses TensorFlow.js, a JavaScript library for machine learning, to compare a user's question to a list of known questions about cooking vegetables. It converts questions into numerical "fingerprints" (embeddings) and finds the closest match using a math formula called cosine similarity. Think of it like finding the most similar recipe card in a box by comparing their ingredients.

## Steps of How the Program Works

Load the Page:

The HTML page loads in a browser, showing a chat box, an input field, and buttons ("Ask" and "Clear").
It includes a list of recommended prompts (e.g., "How do I steam broccoli?") to guide users.
A static JSON dataset is loaded, containing:
Questions about cooking broccoli, carrots, or zucchini.
Simulated embeddings (numerical representations of questions, like [0.1, 0.2, 0.3, 0.4, 0.5]).
Answers, cooking times, and difficulty levels (easy, medium, hard).




User Asks a Question:

The user types a question (e.g., "How to steam broccoli?") in the input field and clicks "Ask."
If the input is empty, an alert asks for a question.


## Generate an Embedding:

TensorFlow.js creates a simulated embedding for the user’s question (a list of 5 random numbers, e.g., [0.1234, 0.2345, 0.3456, 0.4567, 0.5678]).
In a real app, a pre-trained model (like Universal Sentence Encoder) would create this embedding, but here it’s random for simplicity.


## Compare with Known Questions:

TensorFlow.js calculates the cosine similarity between the user’s question embedding and each question’s embedding in the JSON dataset.
Cosine Similarity Formula:[\text{Cosine Similarity} = \frac{A \cdot B}{|A| |B|}]
(A \cdot B): Dot product (sum of pairwise multiplications of embedding values).
(|A|): Norm of the user’s embedding (square root of sum of squared values).
(|B|): Norm of the training question’s embedding.
Example: For embeddings (A = [0.1, 0.2]) and (B = [0.3, 0.4]):
Dot product: (0.1 \times 0.3 + 0.2 \times 0.4 = 0.11)
Norm (A): (\sqrt{0.1^2 + 0.2^2} = \sqrt{0.05} \approx 0.2236)
Norm (B): (\sqrt{0.3^2 + 0.4^2} = \sqrt{0.25} = 0.5)
Similarity: (\frac{0.11}{0.2236 \times 0.5} \approx 0.982)




## The highest similarity score indicates the closest match.


Find the Best Match:

If the highest similarity score is greater than 0.5, the app selects the corresponding answer, cooking time, and difficulty.
If no score exceeds 0.5, it returns "I don’t know" with a suggestion to try a recommended prompt.


## Display the Response:

The chat box shows:
The user’s question.
The answer (or "I don’t know").
If an answer is found, the cooking time and difficulty.
The math behind the match, including:
The cosine similarity formula.
The user’s question embedding.
For each training question: its embedding, dot product, norms, similarity score, and whether it was the best match.




Example output for "How to steam broccoli?" (if matched):Q: How to steam broccoli?
A: Place broccoli florets in a steamer basket over boiling water, cover, and steam for 5-7 minutes...
Time: 7 min | Difficulty: easy
Math:
Cosine Similarity = (A · B) / (||A|| ||B||)
Question Embedding: [0.1234, 0.2345, 0.3456, 0.4567, 0.5678]
- Compared to "How do I steam broccoli?":
  Training Embedding: [0.1000, 0.2000, 0.3000, 0.4000, 0.5000]
  Dot Product: 0.2876
  Norm A: 0.7890, Norm B: 0.7416
  Similarity: 0.6452 (Best Match)
- Compared to "What's the best way to roast carrots?":
  Similarity: 0.4321
...




Clear the Chat:

Clicking "Clear" empties the chat box and input field for a fresh start.



Prerequisites

A modern web browser (e.g., Chrome, Firefox).
No server setup needed; the app runs entirely in the browser.

How to Run

Save the index.html file to your computer.
Open it in a web browser by double-clicking or dragging it into the browser.
Type a question about cooking broccoli, carrots, or zucchini (use recommended prompts for best results).
Click "Ask" to see the response and math.
Click "Clear" to reset the chat.

Notes

Embeddings: The embeddings are random for demonstration. In a real app, a pre-trained model like Universal Sentence Encoder would generate them.
Threshold: The 0.5 similarity threshold ensures "I don’t know" for poor matches. Adjust in the code (findBestAnswer) if needed.
TensorFlow.js: Handles tensor operations (dot products, norms) for cosine similarity. It’s loaded via a CDN.
Limitations: The app uses static data and doesn’t train a model. It simulates inference with pre-trained embeddings.
Styling: Uses Tailwind CSS for a clean, responsive design.

Example Questions

"How do I steam broccoli?"
"What’s the best way to roast carrots?"
"How can I sauté zucchini?"
If you ask something unrelated (e.g., "How to bake potatoes?"), it may say "I don’t know."

License
MIT License. Feel free to use and modify!

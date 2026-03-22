# Unit Converter Web App

## Overview, Design, and Implementation
This project is a lightweight, responsive web application that converts distances between kilometers and miles. It was developed as part of a Technical Assessment for the Pursuit AI Native program.

### Deliverables
*   [My conversation with Gemini can be found here.](https://docs.google.com/document/d/1q_kLs3_OAdNGsbEwSKBkM6a7oqkj7_FxTZYd2FcBZcU/edit?usp=sharing)
*   [My deployed app can be found here.]()

**Core Technologies:**
*   HTML5
*   Vanilla JavaScript (ES6+)
*   Bootstrap 5.3 (via CDN)

**Design Philosophy:**
The UI is designed to be clean, distraction-free, and accessible. Using Bootstrap's flexbox utilities, the main conversion card is locked to the dead center of the viewport. The application defaults to Bootstrap's dark theme to reduce eye strain, but includes an absolute-positioned toggle button in the top-right corner, allowing users to switch between light and dark modes instantly.

**Implementation Details:**
*   **Decoupled Architecture:** The mathematical conversion logic is strictly separated from DOM manipulation. Pure functions handle the calculations, making the core engine predictable and highly testable.
*   **Real-Time Processing:** Instead of relying on a "Submit" button, the application uses `input` and `change` event listeners to update the conversion dynamically as the user types or switches the conversion direction.
*   **Dynamic Localization (l10n):** The application features built-in region detection using the browser's `navigator.language` property. It dynamically updates the UI spelling to either the US standard ("Kilometers") or the International standard ("Kilometres") without altering the underlying data structures.
*   **Float Formatting:** Output values are constrained to a maximum of four decimal places for precision, utilizing `parseFloat` and `toFixed(4)` to elegantly strip unnecessary trailing zeros.

---

## Prompting Methodology
This project was developed through an iterative pair-programming session with an AI assistant (Gemini). The prompting methodology utilized several key software engineering best practices:

1.  **Plan Before Execution:** Before any code was generated, the AI was instructed to provide a detailed implementation plan. This ensured architectural alignment (like decoupling logic and choosing the right localization strategy) before committing to a codebase.
2.  **Strict Scope Control:** Feature additions (such as the l10n spelling update and float constraints) were handled one at a time. Prompts explicitly instructed the AI to limit the scope of its changes to the requested item only.
3.  **Context Management:** To prevent "context drift" and hallucinated code, the exact, current state of the `index.html` file was provided to the AI whenever a targeted insertion or modification was requested. 
4.  **Reversion and Version Control:** When testing a change (e.g., restricting the output to a single decimal place), the output was evaluated, and the decision was explicitly communicated to the AI to revert back to the four-decimal standard, establishing a clear source of truth for the final codebase.

---

## Reflection and Recommendations
**Process Reflection:**
This collaborative session was highly efficient. By acting as the "Tech Lead" and treating the AI as the "Junior Developer," the human developer maintained total control over the architecture, user experience, and feature set. The AI handled the boilerplate generation and syntax execution, while the human developer dictated the constraints, evaluated the approaches (like choosing `navigator.language` over IP Geolocation), and managed the version history.

**Recommendations for Future Collaborative Sessions:**
*   **Continue Context Anchoring:** Providing the current codebase when asking for updates is the single best way to keep the AI grounded in reality. Continue this practice.
*   **Maintain the "Plan First" Rule:** Always ask the AI to explain its proposed technical approach before it writes the code. It is much easier to correct a flawed plan than to debug a flawed script.
*   **Isolate Complex Logic:** As applications grow beyond a single file, continue to explicitly instruct the AI to separate concerns (e.g., "Write the business logic in `utils.js` and the UI updates in `main.js`") to prevent the AI from generating monolithic, tightly coupled code.
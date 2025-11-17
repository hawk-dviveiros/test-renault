**Application Description**

This is a single-page web application that functions as a "Perfect Match" car recommendation tool. Users can input their preferences through a questionnaire, and the page will calculate and display the best car models for them based on a predefined set of rules.

**Functionality**

The user answers a series of questions about their lifestyle and preferences, including:

*   Number of people in the car
*   Preferred car "vibe"
*   Driving distance frequency
*   Priorities (design, tech, comfort, etc.)
*   Typical driving day
*   Desired high-end features
*   Access to a charging point

Based on the user's answers, the application filters and scores a list of car models. The results are then displayed to the user, ranked from highest to lowest score.

**Scoring Logic**

The scoring logic is implemented in JavaScript within the `index.html` file. It works as follows:

1.  **Filtering:** Some user preferences act as hard filters, immediately disqualifying certain car models. For example, if a user needs to transport 5 people, models with a lower capacity are filtered out.
2.  **Weighted Scoring:** Other preferences contribute to a weighted score. Different questions have different weights, meaning they have a greater or lesser impact on the final score.
3.  **Ranking:** After all models have been scored, they are ranked and displayed to the user.

**Car Models**

The application includes a predefined list of car models, each with its own set of attributes (capacity, vibe, features, etc.). These models are stored in a JavaScript array within the `index.html` file.

**File Structure**

*   `index.html`: The main HTML file containing the structure, styling, and JavaScript logic of the application.
*   `tailwind.min.js`: A local copy of the Tailwind CSS library, used for styling the application.
*   `prompt.md`: This file, providing a detailed description of the application.
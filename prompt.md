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

Based on the user's answers, the application first filters the list of car models to exclude any that don't meet the user's essential requirements. Then, it scores the remaining models based on how well they match the user's weighted preferences. The results are then displayed to the user, ranked from highest to lowest score.

**Filtering Logic**

Certain questions act as hard filters, immediately disqualifying models that do not meet the user's needs.

*   **Q1: People Capacity:** The filtering logic for the number of people is as follows:
    *   If the user selects "1-2", no models are filtered out based on capacity.
    *   If the user selects "2-4", models with a "1-2" capacity are filtered out. Models with "2-4" and "5" capacity are shown.
    *   If the user selects "5", only models with a "5" capacity are shown.

*   **Q6: Towing Capability:** If the user checks the "Capable of towing above 700 KGs" box, any model with a `towingWeight` less than 700 is filtered out.

*   **Q7: Charging Point Access:** If the user selects "No", all fully electric models (where `isElectric` is `true`) are filtered out. For all other selections ("At home", "At work", etc.), no filter is applied.

**Weighted Scoring**

After filtering, the remaining models are scored based on a weighted system. The maximum possible score is **19 points**.

*   **Q2: Perfect Car Vibe (1 point per match):** Users can select multiple "vibes". For each selected vibe that matches a car model's `vibe` array, 1 point is added to the score.

*   **Q3: Driving Distance Frequency (6 points):** This is a heavily weighted question. If the user's selection matches the model's `longDistanceFrequency`, the model receives 6 points.

*   **Q4: Prioritise (3 points):** If the user's selection for their main priority matches the model's `prioritise` attribute, the model receives 3 points.

*   **Q5: Typical Driving Day (2 points):** If the user's selection for their typical driving day matches the model's `drivingDay`, the model receives 2 points.

*   **Q6: High-end Features (2 points per match):** This is another heavily weighted category. For each selected high-end feature (excluding the towing option, which is a filter) that the model has, the model receives 2 points.

**Car Models**

The application includes a predefined list of car models stored in a JavaScript array in `index.html`. Each model object has several attributes, including `capacity`, `vibe`, `features`, `towingWeight`, and a new boolean attribute `isElectric` to identify if the model is fully electric.

**File Structure**

*   `index.html`: The main HTML file containing the structure, styling, and all JavaScript logic for filtering and scoring.
*   `tailwind.min.js`: A local copy of the Tailwind CSS library for styling.
*   `prompt.md`: This file, providing a detailed description and logic summary of the application.
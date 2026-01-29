**Application Description**

This is a single-page web application that functions as a "Perfect Match" car recommendation tool. Users can input their preferences through a simplified questionnaire, and the page will calculate and display the best car models for them based on a predefined set of rules.

**Functionality**

The user answers a series of questions about their lifestyle and preferences, including:

1.  **What size car feels right for your needs?** (Filter)
2.  **How often do you drive long distances?** (2x Weight)
3.  **Above all else, you prioritise...** (3x Weight)
4.  **What's your typical driving day?** (1x Weight)
5.  **Do you have access to a charging point?** (Filter)

Based on the user's answers, the application first filters the list of car models to exclude any that don't meet the user's essential requirements (car size and charging access). Then, it scores the remaining models based on how well they match the user's weighted preferences. The results are then displayed to the user, ranked from highest to lowest score.

**Filtering Logic**

Certain questions act as hard filters, immediately disqualifying models that do not meet the user's needs.

*   **Q1: Car Size:** The user selects a single car size from a dropdown list. If a size is selected, any models that do not have a matching `vibe` string are filtered out.

*   **Q5: Charging Point Access:** This is a multiple-choice question. The filtering logic is as follows:
    *   If the user selects "No", all fully electric models (where `isElectric` is `true`) are filtered out.
    *   If the user selects any combination of "At home", "At work", or "Not currently but I could install at home", the application checks if a model is electric. If it is, the model's `chargingAccess` array must contain at least one of the user's selected options to pass the filter. Non-electric cars are unaffected.

**Weighted Scoring**

After filtering, the remaining models are scored based on a weighted system. The maximum theoretical score is **6 points**.

*   **Q2: Driving Distance Frequency (2 points):** If the user's selection matches the model's `longDistanceFrequency`, the model receives **2 points**.

*   **Q3: Prioritise (3 points):** If the user's selection matches the model's `prioritise` attribute, the model receives **3 points**.

*   **Q4: Typical Driving Day (1 point):** If the user's selection matches the model's `drivingDay`, the model receives **1 point**.

**Car Models**

The application includes a predefined list of car models in `index.html`. The data structure has been updated as follows:

*   `vibe`: Is now a single string (e.g., "Small (ideal for 1-2, big enough for 4)").
*   `chargingAccess`: Is now an array of strings indicating compatible charging options (e.g., ["At home", "At work"]).
*   The `features` and `towingWeight` properties have been removed.

**File Structure**

*   `index.html`: The main HTML file containing the structure, styling, and all JavaScript logic.
*   `README.md`: This file, providing a detailed description of the application logic.

**Application Description**

This is a single-page web application that functions as a "Perfect Match" car recommendation tool. Users can input their preferences through a questionnaire, and the page will calculate and display the best car models for them based on a predefined set of rules.

**Functionality**

The user answers a series of questions about their lifestyle and preferences, including:

*   Number of people in the car
*   Preferred car "vibe"
*   Driving distance frequency
*   Priorities (design, tech, comfort, etc.)
*   Typical driving day
*   Desired high-end features (options include "Panoramic sunroof", "Accessibility features", "High-end audio system", "High-end on-board tech", "Equipment customisation", "Exciting colourways", "Bike rack", "Sporty add-ons", and a filter for "Capable of towing above 700 KGs")
*   Access to a charging point

Based on the user's answers, the application first filters the list of car models to exclude any that don't meet the user's essential requirements. Then, it scores the remaining models based on how well they match the user's weighted preferences. The results are then displayed to the user, ranked from highest to lowest score.

**Filtering Logic**

Certain questions act as hard filters, immediately disqualifying models that do not meet the user's needs.

*   **Q1: People Capacity:** The filtering logic for the number of people is as follows:
    *   If the user selects "1-2", no models are filtered out based on capacity.
    *   If the user selects "2-4", models with a "1-2" capacity are filtered out.
    *   If the user selects "5", only models with a "5" capacity are shown.

*   **Q6: Towing Capability:** If the user checks the "Capable of towing above 700 KGs" box, any model with a `towingWeight` less than 700 is filtered out.

*   **Q7: Charging Point Access:** If the user selects "No", all fully electric models (where `isElectric` is `true`) are filtered out.

**Weighted Scoring**

After filtering, the remaining models are scored based on a weighted system. The maximum theoretical score is **20 points**.

*   **Q2: Perfect Car Vibe (1 point per match):** For each selected vibe that matches a car model's `vibe` array, **1 point** is added.

*   **Q3: Driving Distance Frequency (2 points):** If the user's selection matches the model's `longDistanceFrequency`, the model receives **2 points**.

*   **Q4: Prioritise (1 point):** If the user's selection matches the model's `prioritise` attribute, the model receives **1 point**.

*   **Q5: Typical Driving Day (1 point):** If the user's selection matches the model's `drivingDay`, the model receives **1 point**.

*   **Q6: High-end Features (2 points per match):** For each selected high-end feature (excluding towing), the model receives **2 points**. The available options are: "Panoramic sunroof", "Accessibility features", "High-end audio system", "High-end on-board tech", "Equipment customisation", "Exciting colourways", "Bike rack", and "Sporty add-ons". If the user selects "None of the above", all other feature checkboxes are disabled and no points are awarded for this category.

**Car Models**

The application includes a predefined list of car models in `index.html`. Each model object's `features` attribute has been updated to include a wider variety of options to match the expanded questionnaire.

**File Structure**

*   `index.html`: The main HTML file containing the structure, styling, and all JavaScript logic.
*   `tailwind.min.js`: A local copy of the Tailwind CSS library.
*   `prompt.md`: This file, providing a detailed description of the application logic.
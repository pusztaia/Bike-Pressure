# Bicycle Tire Pressure Calculator

## Overview
This project provides a web-based bicycle tire pressure calculator, optimized for mobile use, particularly for iOS devices. It helps cyclists determine optimal tire pressure based on various factors such as bike, wheelset, tire type, rider weight, gear weight, and environmental conditions.

## Features
*   **Dynamic Pressure Calculation:** Calculates recommended front and rear tire pressures based on a sophisticated physics engine considering multiple inputs.
*   **Temperature-Adjusted Recommendations:** Utilizes the Ideal Gas Law to adjust pressure for differences between inflation temperature (garage) and riding temperature (outside).
*   **Interactive Temperature-Pressure Graph:** Visualizes how tire pressure changes with temperature, allowing users to understand the impact of thermal variations.
*   **Safety Protocols:** Provides warnings and highlights limits for hookless rims and tire maximum pressures.
*   **Theme Toggle:** Switch between dark and light modes with user preference saved in local storage.
*   **Intuitive UI/UX:** Clean, modern, and readable interface with an enhanced color palette, refined typography, and clear layout.
*   **Customizable Profiles:** Easily create and manage different bike setups.

## Files
*   `iphone_app.html`: The generic version of the tire pressure calculator. It includes all core functionalities and UI/UX enhancements, suitable for various bike setups.
*   `index.html`: A customized version of the calculator, pre-configured for a specific road bike setup:
    *   **Bike:** BMC Alpenchallenge 01 THREE (L), 9.6kg
    *   **Wheelset:** DT SWISS C 1800 SPLINE 23 DB (Hooked, 22mm inner width)
    *   **Tires:** Panaracer Gravelking Slick TLC Folding Tire - 32-622 (Max 75 PSI)

## Usage
To use the application:
1.  Open either `iphone_app.html` or `index.html` in a web browser (preferably on an iPhone or a mobile device).
2.  For iPhone users, you can add the page to your home screen for an app-like experience (Safari: Share button -> "Add to Home Screen").
3.  Adjust the input parameters (Bike, Wheel, Tire, Rider Weight, Surface Type, Temperatures) to get your personalized tire pressure recommendations.
4.  Toggle between dark and light themes using the switch in the header.

## Customization (Creating New Bike Profiles)
You can easily create new bike profiles or customize existing ones by editing the JavaScript objects (`bikes`, `wheelsets`, `tireMaxPressure`) within the HTML file. Follow the existing structure to add new entries and update the `bikeSelect` and `wheelSelect` dropdowns accordingly.

## Technology Used
*   **HTML, CSS, JavaScript:** Core web technologies.
*   **Chart.js:** For interactive data visualization (temperature-pressure graph).
*   **Feather Icons:** Inlined SVG icons for a lightweight and customizable icon set.

## Assumptions (for `index.html`)
During the creation of `index.html`, some assumptions were made due to the difficulty in finding precise component specifications online:
*   **BMC Alpenchallenge 01 THREE Weight:** Assumed to be 9.6 kg.
*   **DT SWISS C 1800 SPLINE 23 DB Wheelset:** Assumed to be "Hooked" with an inner rim width of 22mm and a max pressure limit of 110 PSI (typical for hooked rims).
*   **Panaracer Gravelking Slick TLC 32-622 Max Pressure:** Assumed to be 75 PSI (a common max for a 32mm tubeless gravel/road tire).

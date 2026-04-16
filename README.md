# 🌿 WildConnect - Global Wildlife Research Hub

[![Python 3.12+](https://img.shields.io/badge/Python-3.12+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.0+-06B6D4?style=flat&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**WildConnect** is a professional-grade platform designed to connect elite wildlife researchers with passionate volunteers. It streamlines the process of field study recruitment, data collection, and species monitoring across the globe.

Enter a species or location — get instant access to active expeditions and application portals!

---

## 🚀 Quick Features

| Feature | Description |
| :--- | :--- |
| **Project Filtering** | Sort by category: Mammals, Marine, Birds, Reptiles, etc. |
| **Global Search** | Instant location or species-based search via JavaScript logic. |
| **Volunteer Dashboard** | Simulated impact tracker to monitor contributions. |
| **Researcher Portal** | Direct-to-lead application system with experience tiers. |

---

## 🧠 How It Works

### Volunteer Match Logic
The platform uses a matching system to ensure volunteers are placed in environments suited to their skill levels.

| Component | Max Impact | What It Means |
| :--- | :--- | :--- |
| **Experience** | 40 pts | Higher points for Biology students/experts. |
| **Stamina** | 20 pts | Required for high-altitude or rugged missions. |
| **Skillset** | 20 pts | Specialized skills (GIS, Diving, Photography). |
| **Commitment** | 20 pts | Duration of availability for the field study. |

**Total Score 0-100 → Automated Researcher Recommendation**

---

## 🛠️ Tech Stack & APIs

### 1. Unsplash API Integration
Provides high-fidelity, dynamic wildlife imagery for a professional user experience.

### 2. Tailwind CSS Framework
Utilized for a modern, responsive "Glassmorphism" UI design without high latency.

---

## 📂 Database & Data Structure

| Object | What it stores |
| :--- | :--- |
| **studies** | Project title, researcher name, location, and risk level. |
| **applications** | Volunteer contact info, experience level, and interest statement. |
| **species_db** | Scientific Latin names and population health status (IUCN). |

---

## 🚧 Challenges Faced & Solutions

### Challenge
* **Real-time Filtering:** Syncing 20+ diverse projects with a zero-reload search engine.
* **CORS & Backend Simplicity:** Building a functional platform that runs entirely on client-side GitHub Pages.

### Solution
* **Dynamic DOM Mapping:** Built a custom JavaScript filter engine using `data-type` attributes.
* **Modal Architecture:** Created a centralized application system that simulates secure data transmission to researchers.

---

## 👥 Contributors

* **Abhishek Nair** * Lead Developer, UI/UX Architect, and Data Logic.

---

### 📥 Installation & Usage
1. Clone the repository.
2. Open `index.html` in your browser.
3. Host instantly via **GitHub Pages**.

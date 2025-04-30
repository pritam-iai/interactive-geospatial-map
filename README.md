**Project Title: Interactive Geospatial Visualization Dashboard (Next.js)**  

**Overview**  
Build a responsive Next.js application that renders two distinct interactive map visualizations—an Icon Layer map and a Hexagonal Layer map—using JSON data as its source. Users will be able to explore spatial data points, filter time‑series data on the hexagon map via a slider, add custom annotations directly on the map, and persist those annotations locally for later retrieval.  

---

### Key Features

1. **Dual Map Visualizations**  
   - **Icon Layer Map**: Plot individual data points as icons (e.g., markers) at their specified latitude/longitude coordinates.  
   - **Hexagonal Layer Map**: Aggregate time‑series data into hexagonal bins, coloring each hexagon by the numerical value for a selected date.  

2. **Time Slider for Hexagon Map**  
   - **Date Filter Slider**: A UI slider with handles corresponding to each distinct `datetime_info` in the JSON payload (e.g. 2020, 2021, 2022).  
   - **Dynamic Update**: Sliding to a given year filters the HexagonLayer to display only data points matching the selected date.  
   - **Visual Feedback**: Current slider value prominently displayed, and hexagon colors/counts update smoothly on slide.

3. **Dynamic Data Loading**  
   - Accept a JSON payload containing an array of records with fields such as `latitude`, `longitude`, `datetime_info`, `numerical_data`, etc.  
   - Parse and feed this data into both map layers, ensuring smooth transitions and reactivity when the JSON changes or slider position updates.

4. **Point Annotation Workflow**  
   - **Click-to-Select**: When the user clicks anywhere on either map, display a small popup at that location.  
   - **Modal Input**: Upon clicking the popup, open a modal dialog containing:  
     - A **textarea** for entering a custom description.  
     - **Save** and **Cancel** controls.  
   - **Local Persistence**: On “Save,” capture:  
     - A generated **message_id** (e.g., UUID)  
     - The clicked point’s **latitude** & **longitude**  
     - The **user-entered message**  
     - Append this record to an array in **`localStorage`** so that annotations persist across page reloads.  
   - **Cancel** simply closes the modal without saving.

5. **State Management & Reactivity**  
   - Use React hooks (e.g., `useState`, `useEffect`) or a lightweight global store (e.g., Zustand) to manage:  
     - Loaded JSON data  
     - Current slider value and filtered dataset  
     - User annotations  
     - Modal visibility and form state  

6. **User Experience & Responsiveness**  
   - Ensure maps and slider resize and reposition gracefully on different screen sizes.  
   - Provide smooth animated transitions when updating hexagon colors or adding/removing annotations.  
   - Display tooltips and hover effects for both icon and hex layers to surface additional metadata.

---

### Technical Stack & Libraries

- **Framework**: Next.js (React-based rendering, API routes if needed)  
- **Map Rendering**:  
  - `deck.gl` for high-performance IconLayer and HexagonLayer  
  - `react-map-gl` or `maplibre-gl` as the underlying map engine  
- **UI Components**: Tailwind CSS (for layout, modals, slider, buttons)  
- **State & Storage**:  
  - React Context / Zustand for in-app state  
  - Browser `localStorage` API for annotation persistence  
- **Data Handling**: JSON parsing with TypeScript interfaces for data validation

---

### Deliverables

1. **Interactive Dashboard Page** showing both map visualizations side-by-side or toggleable, with a time-slider control for the hexagon map.  
2. **Slider-Controlled Hexagon Map** that filters and updates based on selected `datetime_info`.  
3. **Annotation System** that lets users click-map → open modal → save description → persist locally.  
4. **Documentation** with:  
   - Data JSON schema (including time-series fields)  
   - Instructions to run and build (`npm run dev` / `npm run build`)  
   - How to clear or migrate stored annotations

---

This project will empower end-users to visualize both static and time‑series geospatial datasets interactively, and to enrich map contexts with personal annotations—all within a modern Next.js environment.


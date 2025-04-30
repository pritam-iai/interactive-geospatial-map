**Project Title: Interactive Geospatial Visualization Dashboard (Next.js)**  

**Overview**  
Build a responsive Next.js application that renders two distinct interactive map visualizations—an Icon Layer map and a Hexagonal Layer map—using JSON data as its source. Users will be able to explore spatial data points, add custom annotations directly on the map, and persist those annotations locally for later retrieval.

---

### Key Features

1. **Dual Map Visualizations**  
   - **Icon Layer Map**: Plot individual data points as icons (e.g., markers) at their specified latitude/longitude coordinates.  
   - **Hexagonal Layer Map**: Aggregate data density into hexagonal bins, coloring each hexagon by the count or intensity of events within it.

2. **Dynamic Data Loading**  
   - Accept a JSON payload containing an array of records with fields such as `latitude`, `longitude`, and other metadata.  
   - Parse and feed this data into both map layers, ensuring smooth transitions and reactivity when the JSON changes.

3. **Point Annotation Workflow**  
   - **Click-to-Select**: When the user clicks anywhere on the map, display a small popup at that location.  
   - **Modal Input**: Upon clicking the popup, open a modal dialog containing:  
     - A **textarea** for entering a custom description.  
     - **Save** and **Cancel** controls.  
   - **Local Persistence**: On “Save,” capture:  
     - A generated **message_id** (e.g., UUID)  
     - The clicked point’s **latitude** & **longitude**  
     - The **user-entered message**  
     - Append this record to an array in **`localStorage`** so that annotations persist across page reloads.  
   - **Cancel** simply closes the modal without saving.

4. **State Management & Reactivity**  
   - Use React hooks (e.g., `useState`, `useEffect`) or a lightweight global store (e.g., Zustand) to manage:  
     - Loaded JSON data  
     - User annotations  
     - Modal visibility and form state  

5. **User Experience & Responsiveness**  
   - Ensure maps resize and reposition gracefully on different screen sizes.  
   - Provide smooth animated transitions when adding or removing annotations.  
   - Display tooltips and hover effects for both icon and hex layers to surface additional metadata.

---

### Technical Stack & Libraries

- **Framework**: Next.js (React-based rendering, API routes if needed)  
- **Map Rendering**:  
  - `deck.gl` for high-performance IconLayer and HexagonLayer  
  - `react-map-gl` or `maplibre-gl` as the underlying map engine  
- **UI Components**: Tailwind CSS (for layout, modals, buttons)  
- **State & Storage**:  
  - React Context / Zustand for in-app state  
  - Browser `localStorage` API for annotation persistence  
- **Data Handling**: JSON parsing with TypeScript interfaces for data validation

---

### Deliverables

1. **Interactive Dashboard Page** showing both map visualizations side-by-side or toggleable.  
2. **Annotation System** that lets users click-map → open modal → save description → persist locally.  
3. **Documentation** with:  
   - Data JSON schema  
   - Instructions to run and build (`npm run dev` / `npm run build`)  
   - How to clear or migrate stored annotations  

---

This project will empower end-users to visualize geospatial datasets in two complementary ways and to enrich the map context with their own notes—all within a modern Next.js environment.

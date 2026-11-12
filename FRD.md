# FUNCTIONAL REQUIREMENTS DOCUMENT (FRD)

**Project Identifier:** PRD-BHRT-2026-V2  
**Project Name:** BharatDimension: 3D Geospatial Vector Explorer  
**System Architecture:** Zero-Scripting Vector Architecture (Semantic Web Standards)  
**Target Coverage:** All 28 States and 8 Union Territories of India (36 Administrative Entities)  
**Document Classification:** Technical Design & Functional Specification  

---

## 1. Project Purpose & Scope

### 1.1 Purpose
The purpose of this project is to build an interactive, browser-native digital atlas of India using web-native vector cartography and declarative layout specifications without client-side JavaScript dependencies. The application provides an interactive exploration path starting from a nationwide 3D overview, zooming smoothly into any selected state or Union Territory, and presenting an administrative, demographic, and cultural dossier.

### 1.2 Core Architectural Principles
* **Declarative State Management:** The application state is driven entirely by URL fragment routing, ensuring that browser history, bookmarked links, and native Back/Forward browser navigation operate out of the box.
* **Continuous Spatial Canvas:** The application operates on a single continuous vector canvas, using hardware-accelerated viewport pan-and-scan kinematics to bring selected territories into focus rather than switching between static sub-pages.
* **Tactile 3D Physicality:** Geographic entities simulate physical tactile depth through multi-tiered elevation and geometric shadow extrusion when interacting via pointer or keyboard controls.

### 1.3 Scope Boundaries

#### In-Scope
* Complete vector representation of the Republic of India containing all 28 States and 8 Union Territories (36 distinct interactive units).
* Multi-stage visual depth simulation across all territory boundaries during pointer hover and keyboard focus states.
* Coordinate-calibrated viewport focusing and smooth camera panning for every individual state and Union Territory.
* Slide-out contextual state profile dossiers displaying administrative, statistical, geographical, and cultural data.
* Bidirectional navigation allowing users to freely inspect territories and return to the national overview without losing application context.

#### Out-of-Scope
* Dynamic external API querying or asynchronous database fetching.
* Route calculation, GPS location tracking, or real-time spatial measuring.
* User authentication, saved favorites, or persistent profile data.

---

## 2. User Roles & Interaction Flows

### 2.1 User Personas
* **The Technical Recruiter / Senior Reviewer:** Evaluates the developer’s architectural discipline, semantic structuring, visual polish, and mastery of modern browser specifications.
* **The General Explorer:** Interacts with the map as an educational or reference tool, seeking geographic, economic, and cultural information about Indian states and union territories.

### 2.2 End-to-End User Interaction Flow
1. **Entry Point (National Overview):** The user arrives at the primary canvas displaying the full map of India within a 3D-angled perspective viewport, accompanied by an ambient interface header.
2. **State Inspection (Tactile Elevation):** The user hovers or tabs across the territories. Individual states lift off the surface plane along the simulated visual axis, casting multi-tiered geometric shadows and revealing territory labels.
3. **State Selection (Camera Glide & Zoom):** The user selects a state or Union Territory. The camera glides and zooms into that entity's geographic coordinates, placing it in clear focus at the center of the canvas while neighboring territories soften in visual priority.
4. **Dossier Presentation (Contextual Drawer):** Simultaneously with the camera glide, an administrative profile drawer slides into view from the edge of the viewport, presenting comprehensive data for the selected state.
5. **Dismissal & Camera Reset:** The user closes the dossier drawer or triggers the camera reset control. The drawer slides away and the camera glides smoothly back to the full national view.

---

## 3. Data Sources & Asset Specifications

### 3.1 Cartographic Vector Requirements
* **Boundary Validation:** Vector boundaries must strictly adhere to the official administrative borders established by the Survey of India.
* **Source Repositories:** Vector assets are sourced from verified GIS repositories (such as the DataMeet Community Maps project or Wikimedia Commons administrative boundary datasets) converted from standard shapefiles into standardized vector graphics.
* **Coordinate Normalization:** The master map vector must be configured within a normalized bounding box of 1000 units by 1150 units to preserve aspect ratio uniformity and coordinate precision across varying screen dimensions.
* **Vector Entity Identification:** Every administrative territory must be configured as a standalone interactive node assigned a unique, kebab-case geographic slug identifier corresponding to its official administrative name.

### 3.2 Demographic & Geospatial Data Repository
* **Statistical Authority:** Demographic figures, headquarters names, and land areas must be derived from official government databases, including the Census of India and the National Informatics Centre (NIC).
* **Uniform State Dossier Schema:** Every territory record must contain:
  * Official Territory Name and Administrative Classification (State or Union Territory)
  * Executive Capital (and Judicial/Legislative Capital if distinct)
  * Total Geographical Area (in square kilometers)
  * Demographic Data (Population magnitude, population density, and literacy rate)
  * Official State Emblems (State Animal, State Bird, or Floral Emblem)
  * Primary Official Language(s)
  * Core Economic Pillars and Industrial Centers
  * Premier Cultural Heritage Highlight or UNESCO World Heritage Site

---

## 4. Functional Requirements

### 4.1 Module 1: The Interactive 3D National Board (Level 1)

* **FR-1.1 Territory Addressability:** All 28 States and 8 Union Territories must be distinct vector entities wrapped in accessible link anchors that point to their unique territorial identifiers.
* **FR-1.2 Pseudo-3D Lift Simulation:** 
  * In the resting state, territories rest flush against the dark background surface with thin, clean boundary outlines.
  * Upon pointer hover or keyboard focus, the targeted territory must elevate vertically along the simulated visual axis within a 250-millisecond response window.
  * Elevation must be accompanied by three distinct shadow layers: a sharp structural chamfer edge, an intermediate body thickness shadow, and a soft ambient ground occlusion shadow.
  * The elevated territory must automatically occupy the highest visual layer to prevent its simulated edges from clipping beneath adjacent territories.
* **FR-1.3 Identity Display:** Hovering or focusing on any territory must reveal an immediate contextual tooltip or floating label displaying the territory's name, administrative designation, and capital city.

### 4.2 Module 2: State Zoom & Camera Kinematics (Level 2)

* **FR-2.1 URL Routing Activation:** The application must transition into the focused state view whenever the active URL fragment matches a registered territory identifier.
* **FR-2.2 Kinematic Camera Movement:** 
  * The camera must zoom in by a scale factor between 3.0x and 4.5x, calibrated specifically to each territory’s bounding area.
  * The camera must pan across the canvas to place the selected state's centroid at the visual center of the screen.
  * The transition must execute using smooth, acceleration-deceleration curve timing over a duration not exceeding 850 milliseconds.
* **FR-2.3 Visual Isolation:** The targeted state must illuminate with distinct accent border strokes and surface fills, while non-selected territories dim in opacity to maintain visual focus on the selected entity.
* **FR-2.4 Persistent Navigation HUD:** 
  * A persistent Heads-Up Display (HUD) must display the path hierarchy (e.g., "India / Western Region / Maharashtra").
  * A clearly labeled reset action must be visible at all times to return the camera to the full national view.

### 4.3 Module 3: State Profile Dossier Drawer (Level 3)

* **FR-3.1 Drawer Invocation:** When a state is targeted, its corresponding profile drawer must slide smoothly into the viewport from the right-hand boundary over a duration of 350 to 400 milliseconds.
* **FR-3.2 Background Preservation:** The state map behind the open drawer must maintain its active zoom level and boundary illumination. A translucent, frosted glass backdrop must visually separate the drawer from the underlying map.
* **FR-3.3 Structured Dossier Layout:** The drawer must present data organized into distinct visual sections:
  * **Header:** Official territory name, administrative designation badge, and capital city.
  * **Vital Statistics Matrix:** Grid display presenting Geographical Area, Population, Density, and Literacy Rate.
  * **Emblems & Identity:** Badges showcasing official state languages and natural emblems.
  * **Economic & Cultural Brief:** Structured narrative cards highlighting major industries, tourism landmarks, and heritage significance.
* **FR-3.4 Dismissal & Reset:** The drawer must feature a distinct close control linking back to the root application state. Activating it must slide the drawer out of view while simultaneously triggering the camera to zoom back out to the national overview.

---

## 5. Regional Calibration Matrix

To support all 36 administrative units across India, the system organizes territories into five geographic zones with standardized zoom and coordinate adjustments:

| Geographic Zone | Administrative Territories Included | Typical Scale Factor | Viewport Coordinate Adjustment |
| :--- | :--- | :--- | :--- |
| **Northern Zone** | Jammu & Kashmir, Ladakh, Himachal Pradesh, Punjab, Haryana, Uttarakhand, Delhi, Chandigarh | 3.6x – 4.0x | Shifts downward and rightward to frame upper northern latitudes. |
| **Western Zone** | Rajasthan, Gujarat, Maharashtra, Goa, Dadra & Nagar Haveli and Daman & Diu | 3.0x – 3.5x | Shifts rightward to center western peninsular regions. |
| **Central Zone** | Madhya Pradesh, Uttar Pradesh, Chhattisgarh | 3.0x – 3.4x | Applies minimal horizontal shift to balance the central landmass. |
| **Southern Zone** | Karnataka, Andhra Pradesh, Telangana, Tamil Nadu, Kerala, Puducherry, Lakshadweep | 3.5x – 4.2x | Shifts upward and rightward to capture southern peninsular territories. |
| **Eastern & North-Eastern Zone** | Bihar, Jharkhand, Odisha, West Bengal, Sikkim, Assam, Meghalaya, Arunachal Pradesh, Nagaland, Manipur, Mizoram, Tripura, Andaman & Nicobar | 3.8x – 4.5x | Shifts leftward and downward to focus on the eastern landmass and coastal archipelagos. |

---

## 6. Non-Functional Requirements

### 6.1 Performance & Rendering Fluidity
* **Frame Rate:** All hover elevations, camera zooms, and drawer slide transitions must render at a consistent 60 frames per second on standard consumer hardware.
* **Zero Runtime Scripting:** The application must execute zero client-side JavaScript. All interactive states, transitions, elevations, and viewport shifts must be powered entirely by declarative browser engine features.
* **Hardware Acceleration:** The main map canvas must use GPU-accelerated rasterization layers to prevent frame stutter during large-scale canvas transforms.

### 6.2 Responsive Boundaries & Ergonomics
* **Viewport Adaptability:** The application viewport must lock to a full-screen, application-style layout on desktop screens, preventing unexpected window-level scrollbars.
* **Mobile & Small-Screen Behavior:** On narrower screens, the state detail drawer must dynamically transition from a side panel into a bottom sheet occupying the lower portion of the screen, leaving the focused state visible above it.

### 6.3 Accessibility & Keyboard Ergonomics
* **Keyboard Tab Flow:** Every administrative territory must be reachable in sequential order via keyboard tab navigation.
* **Focus Indicators:** Active keyboard focus must trigger the same 3D elevation and high-contrast outline cues as a pointer hover.
* **Screen Reader Semantics:** Every interactive vector element must include standard accessibility labels containing the territory name, administrative designation, and navigation cues.

---

## 7. Step-by-Step Implementation Roadmap

### Phase 1: Asset Assembly & Vector Normalization
* Acquire a verified master vector map of India containing all 28 States and 8 Union Territories.
* Clean raw vector files: strip editor metadata, normalize viewBox proportions to the standard bounding box, and eliminate hardcoded fills.
* Assign consistent, semantic identifiers to each state and union territory node.

### Phase 2: Design Tokens & Layout Scaffolding
* Establish root design tokens for the interface: primary background hues, boundary stroke widths, elevation shadow depths, and typography scales.
* Build the fixed application layout: lock the viewport, center the vector stage, and frame the upper navigation header.

### Phase 3: Tactile 3D Styling Engine
* Implement base visual treatments for all 36 administrative territories.
* Build the three-tiered shadow elevation system for hover and focus states.
* Ensure elevated territories render cleanly above neighboring borders without visual clipping.

### Phase 4: State Camera Calibration & Kinematics
* Configure URL fragment routing rules for all 36 states and union territories.
* Calibrate the zoom scale factor and pan offsets for each geographic zone to ensure territories are properly framed.
* Set transition timings and easing curves to maintain smooth camera motion between zoom levels.

### Phase 5: State Profile Dossier Drawers
* Construct the slide-out profile drawer components for all territories, populating demographic, administrative, and cultural data fields.
* Configure the drawer slide-in transitions to synchronize with camera zoom movements.
* Wire drawer close controls to reset the URL fragment and return the camera to the national view.

### Phase 6: Verification, Accessibility Audit & Deployment
* Perform end-to-end user navigation audits across all 36 administrative territories.
* Validate keyboard navigation and verify screen reader accessibility labels.
* Verify smooth rendering performance across major modern browser engines (Chromium, Gecko, WebKit).
* Deploy the production build to a static web hosting platform (such as GitHub Pages).

---

## 8. Quality Assurance & Acceptance Criteria

| Test ID | Scenario | Execution Action | Expected Result |
| :--- | :--- | :--- | :--- |
| **TC-01** | Territory Completeness | Review vector node inventory. | All 28 States and 8 Union Territories are distinct, selectable entities. |
| **TC-02** | Tactile 3D Elevation | Hover pointer over any state. | The state raises along the visual axis with clear multi-layer shadows within 250ms. |
| **TC-03** | Layer Stacking Order | Hover over a state bordering multiple regions. | The hovered state renders above adjacent borders without edge clipping. |
| **TC-04** | State Zoom Centering | Activate a state link. | The canvas pans and zooms smoothly, placing the state within the viewport boundaries. |
| **TC-05** | Visual Territory Focus | Observe map canvas after zoom completion. | The targeted state illuminates clearly while non-selected territories dim in visual intensity. |
| **TC-06** | State Dossier Slide-In | Activate any territory link. | The profile drawer slides in from the right edge displaying accurate demographic and administrative data. |
| **TC-07** | Drawer Dismissal Continuity | Select the close action within the drawer. | The drawer closes, and the camera glides smoothly back to the full national view. |
| **TC-08** | Browser History Reversal | Use the native browser Back button from an open state dossier. | The view returns cleanly to the full national overview without screen flicker or reload. |
| **TC-09** | Script-Free Operation | Inspect the browser Network and Sources tabs. | Zero JavaScript files are loaded or executed; all interactions run via native browser styling rules. |
# 3D Cuboid Annotation Guidelines (Cars)

## 1. Project Overview
This annotation project focuses on labeling **cars using 3D cuboids** in images for training and evaluating machine learning models in **autonomous driving, traffic monitoring, and vehicle detection systems**.

The goal is to produce high-quality, consistent 3D cuboid labels that represent:
- Vehicle position in the image
- Vehicle orientation (heading direction)
- Vehicle dimensions (length, width, height approximation)

These cuboids are used to support downstream tasks such as:
- 3D object detection
- Tracking and motion prediction
- Vehicle localization and scene understanding

---

## 2. Annotation Objective
Annotators must draw a **tight-fitting 3D cuboid** around each visible car in the image.

Each cuboid must:
- Represent the real physical shape of the vehicle
- Match the vehicle's perspective in the camera view
- Align with vehicle edges and visible corners
- Follow consistent rules for occlusion and truncation

---

## 3. Label Classes
### 3.1 Primary Class
- **Car**: Standard passenger vehicles (sedans, SUVs, hatchbacks, vans, pickups).

### 3.2 Exclusions (Do NOT label as Car)
- Motorcycles / bicycles
- Tricycles
- Buses (unless explicitly included by project scope)
- Trucks (unless explicitly included)
- Trailers
- Construction vehicles
- Stationary objects resembling cars (car-shaped ads, toy cars)

If the dataset includes additional classes, they must be listed in the project taxonomy.

---

## 4. Cuboid Definition
A **3D cuboid** consists of:
- 8 corners
- 12 edges
- A visible front face and rear face (depending on viewpoint)

The cuboid should approximate the car as a rectangular prism.

### 4.1 Cuboid Alignment Rules
Annotators must align the cuboid with the car’s:
- **Length**: front bumper to rear bumper
- **Width**: left side to right side
- **Height**: ground contact to roofline

---

## 5. Annotation Procedure
### Step-by-Step Workflow
1. Identify all cars in the image.
2. For each car, determine if it qualifies (see visibility rules).
3. Place a cuboid that encloses the vehicle body.
4. Adjust corners so the cuboid is tight and consistent.
5. Assign required attributes (occlusion, truncation, orientation).
6. Validate against quality checklist.

---

## 6. Cuboid Placement Guidelines
### 6.1 Tightness
Cuboids must be **as tight as possible** without cutting into the car.

- Cuboid edges should touch the visible outer boundary of the car body.
- Do not include excessive background space.

### 6.2 Ground Contact
The cuboid bottom face should align with the car's contact with the ground.

If wheels are visible:
- Bottom edge should touch the wheel-ground contact point.

If wheels are not visible:
- Infer the ground contact using car body perspective.

### 6.3 Roof Height
The top face should match the roofline, not including:
- Roof racks (unless part of permanent structure)
- Temporary objects (cargo, luggage)

### 6.4 Side Mirrors
Side mirrors are usually should be included.

### 6.5 Open Doors / Trunk
If a door is open:
- Annotate the cuboid for the **main vehicle body only**
- Ignore open door extension unless the door is clearly part of the stable vehicle geometry.

---

## 7. Orientation and Heading Direction
Annotators must align the cuboid to represent the vehicle’s direction of travel.

### 7.1 Heading Rules
- The **front face** corresponds to the vehicle's front (headlights, grille).
- The **rear face** corresponds to taillights and trunk.

If uncertain:
- Use visual cues like headlights, license plates, windshield slope.

### 7.2 Cars Parked or Stationary
Even if stationary, cuboid orientation must reflect the actual car direction.

---

## 8. Occlusion Handling
Occlusion occurs when part of the car is hidden behind another object.

### 8.1 Occlusion Levels
Annotators must assign one of the following occlusion values:

- **0 (None)**: fully visible car
- **1 (Partial)**: up to 50% hidden
- **2 (Heavy)**: 50–80% hidden
- **3 (Severe)**: more than 80% hidden

### 8.2 Cuboid Completion Under Occlusion
Even if parts are hidden, the cuboid must represent the **full car body**, inferred from visible edges.

Example:
- If rear half is behind a wall, still extend cuboid to expected rear position.

---

## 9. Truncation Handling
Truncation occurs when the car is cut off by the image boundary.

### 9.1 Truncation Levels
- **0 (None)**: fully inside frame
- **1 (Truncated)**: partially outside image boundary

### 9.2 Cuboid Placement Under Truncation
Extend cuboid beyond the image boundary logically, following perspective.

Do not shrink cuboid to fit only visible portion.

---

## 10. Minimum Visibility Threshold
Annotate a car only if:
- At least **25% of the car body** is visible, OR
- The vehicle can be confidently identified as a car

If the visible portion is too small or ambiguous, mark as **ignore**.

---

## 11. Overlapping Cars
When cars overlap:
- Annotate each car separately.
- Ensure cuboids do not merge.

If one car fully blocks another:
- Only annotate the visible car unless the hidden car is still clearly identifiable.

---

## 12. Reflections and Shadows
### 12.1 Reflections
Do not annotate reflections of cars in:
- Glass buildings
- Mirrors
- Water surfaces

### 12.2 Shadows
Do not include shadows in cuboid boundaries.

---

## 13. Difficult Cases and Special Rules
### 13.1 Cars on Slopes or Uneven Roads
Cuboid should still align with the vehicle geometry, not the road.

### 13.2 Motion Blur
If blurred but identifiable:
- Annotate normally using best estimate.

### 13.3 Night Scenes / Low Visibility
If headlights only and body not visible:
- Do not annotate unless vehicle shape is still clear.

### 13.4 Partially Covered Cars
If covered with tarp or cloth:
- Annotate only if clear car geometry is visible.

---

## 14. Attribute Schema (Recommended)
Each cuboid annotation should include:

| Attribute | Type | Description |
|----------|------|-------------|
| class | string | "car" |
| occlusion | int | 0–3 |
| truncation | int | 0 or 1 |
| orientation | float/int | heading angle or direction |
| confidence | float | optional quality confidence |

---

## 15. Quality Assurance Checklist
Before submitting an annotation, verify:

### Cuboid Geometry
- [ ] Cuboid tightly fits car body
- [ ] Bottom aligns with ground contact
- [ ] Top aligns with roofline
- [ ] Cuboid matches vehicle perspective

### Orientation
- [ ] Front face correctly identified
- [ ] Cuboid direction matches heading

### Occlusion/Truncation
- [ ] Occlusion labeled correctly
- [ ] Truncation labeled correctly
- [ ] Hidden parts inferred logically

### Consistency
- [ ] Mirrors excluded consistently
- [ ] Doors/trunk treated consistently
- [ ] No reflections labeled

---

## 16. Common Annotation Mistakes
Avoid the following:
- Loose cuboids with large background margins
- Incorrect front/back direction
- Including shadows or reflections
- Shrinking cuboid when object is truncated
- Failing to infer occluded vehicle portions

---

## 17. Submission Standards
Annotations must be:
- Consistent with project rules
- Free of missing attributes
- Saved in the required format (JSON, XML, etc.)
- Verified with QA checklist

---

## 18. Final Notes
High-quality cuboid annotation requires strong attention to:
- geometry
- perspective
- consistency
- interpretability under occlusion

When uncertain, always follow the rule:
> "Annotate the car as it exists in the real world, not just what is visible in the image."

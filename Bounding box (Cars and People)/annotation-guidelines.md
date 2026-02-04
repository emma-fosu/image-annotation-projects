# Image Annotation Guidelines  
## Bounding Box Annotation for Cars and People (CVAT)

## 1. Objective

The objective of this project is to create a high-quality, consistent, and machine-learning-ready dataset of **bounding box annotations** for:

- **Cars**
- **People**

Annotations will be performed using **CVAT (Computer Vision Annotation Tool)** and will be used for training and evaluating object detection models.

---

## 2. Annotation Tool

- **Tool:** CVAT
- **Annotation Type:** Bounding Boxes (2D)
- **Dataset Type:** Image-based

---

## 3. Classes and Definitions

### 3.1 Person

**Definition:**  
A *Person* refers to any visible human, regardless of age, gender, or clothing.

**Include:**
- Standing, sitting, walking, or running people
- Partially visible people (e.g., torso, legs only)
- People inside vehicles (if clearly visible)
- People reflected in mirrors or glass *only if clearly distinguishable*

**Exclude:**
- Statues, mannequins, posters, or images of people
- Very small or indistinguishable human-like shapes

---

### 3.2 Car

**Definition:**  
A *Car* refers to a motorized road vehicle designed primarily for passenger transport.

**Include:**
- Sedans, hatchbacks, SUVs, coupes
- Taxis and ride-hailing vehicles
- Parked or moving cars
- Partially visible cars

**Exclude:**
- Trucks, buses, vans, motorcycles, bicycles
- Toy cars or images/posters of cars

---

## 4. Bounding Box Rules

### 4.1 Box Placement

- Bounding boxes **must tightly enclose** the visible extent of the object
- Boxes should align closely with object edges
- Do **not** include excessive background
- Do **not** cut off visible parts of the object

---

### 4.2 Occlusion Rules

| Scenario | Action |
|--------|--------|
| Object partially occluded | Annotate the visible part only |
| Object heavily occluded (>50%) | Annotate only if class is unambiguous |
| Object fully occluded | Do not annotate |

---

### 4.3 Truncation

- If an object extends beyond the image boundary, annotate the visible region
- Bounding box may touch image borders

---

### 4.4 Overlapping Objects

- Annotate **each object separately**
- Overlapping objects must have **separate bounding boxes**
- Do not merge multiple objects into one box

---

## 5. Edge Cases

### 5.1 Small Objects

- Annotate small objects **only if clearly identifiable**
- If unsure of the class, **do not annotate**

---

### 5.2 Reflections and Shadows

- Reflections: Annotate only if clearly recognizable as a person or car
- Shadows: **Do not annotate shadows**

---

### 5.3 Crowds

- Each individual person must receive **one bounding box**
- Do not draw a single box around multiple people

---

## 6. Annotation Consistency

- Maintain consistent box tightness across images
- Follow class definitions strictly
- When uncertain, **flag the image for review**

---

## 7. Quality Checklist (Annotators)

Before submitting work, verify:
- [ ] All cars are annotated
- [ ] All people are annotated
- [ ] No incorrect classes assigned
- [ ] Boxes are tight and accurate
- [ ] No duplicate annotations

---

## 8. Review and Feedback

- All annotations will undergo quality review
- Feedback will be provided via CVAT comments
- Annotators must address all reviewer comments

---

## 9. Common Mistakes to Avoid

- Loose bounding boxes
- Annotating non-target objects
- Missing partially visible objects
- Labeling vans or trucks as cars

---

## 10. Contact

For questions or clarification, contact the project administrator.

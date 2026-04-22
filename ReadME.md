# 📚 Recommendation System Assignment

## Overview

This project builds a simple recommendation system to predict what a user should read next using:

- Sequential logic (for next chapter prediction)
- Popularity-based recommendations
- Tag-based filtering for personalization

The system handles:
- Continuing an ongoing book
- Discovering new books
- Cold start scenarios (new users/books)

---

## Problem Framing

We define three tasks:

1. **Next Chapter Prediction**
   - Recommend the next chapter within a book using sequence

2. **New Book Recommendation**
   - Suggest books based on user reading history

3. **Cold Start Handling**
   - New users → recommend popular books  
   - New books → rely on tags and metadata  

---

## Approach

- Built a mapping from `chapter_id → next_chapter_id` using chapter sequence
- Used popularity-based ranking for baseline recommendations
- Used tag-based similarity to personalize recommendations
- Added logic to switch between:
  - Continue reading
  - Discover new books

---

## Evaluation

### Next Chapter Prediction
- Used accuracy (deterministic due to sequence)

### Book Recommendation
- Used holdout strategy
- Evaluated using **Recall@K**
- Performed qualitative validation by manually inspecting whether recommended books align    with user-preferred tags

---

## Trade-offs

- Used rule-based approach instead of ML due to strong sequential signal
- Used tag-based filtering instead of collaborative filtering for simplicity
- Did not use complex models (LightGBM, ALS) due to time constraints
- Limited evaluation due to lack of timestamps and explicit feedback

---

## How to Run

1. Clone the repository:
--

2.Run the notebook `notebooks/recommendation_system.ipynb`

---

## Future Improvements

- Use timestamps to model user behavior more accurately
- Add collaborative filtering for better personalization
- Use ranking models to combine multiple signals

---

## Summary

This solution focuses on simplicity, interpretability, and effective use of available data while handling key recommendation scenarios.
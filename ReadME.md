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

I have defined three tasks:

1. **Next Chapter Prediction**
   - Recommend the next chapter within a book using sequence

2. **New Book Recommendation**
   - Suggest books based on user reading history

3. **Cold Start Handling**
   - New users → recommend popular books  
   - New books → rely on tags and metadata  

---

## Assumptions

- Users generally read chapters in sequential order within a book  
- The highest chapter_sequence_no a user has interacted with represents their current reading position within a book, since no interaction
  timestamps are available.  
- Interactions are implicit feedback (no ratings or dislikes)  
- Tags and authors reflect user preferences  
- Popularity can serve as a reasonable fallback in cold start scenarios
  
This framing allows us to handle:
- Continuation (next chapter)  
- Discovery (new books)  
- Cold start (new users/books)


## Approach

- Built a mapping from `chapter_id → next_chapter_id` using chapter sequence
- Used popularity-based ranking for baseline recommendations
- Used tag-based similarity to personalize recommendations
- Added logic to switch between:
  - Continue reading
  - Discover new books


---

## How to Run

1. Clone the repository:
   
```bash
   git clone https://github.com/vamshigaddi/Recommendation-System.git
```

2. Run the test.ipyndb notebook

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


## Future Improvements

- Timestamps — If interaction timestamps were available, we could model true reading order, detect dropped books, and give more weight to recent behavior instead  of relying on chapter_sequence_no as a proxy.
- Hybrid Recommendation — Combine collaborative filtering (users with similar reading patterns) with the current tag-based content filtering to improve personalization, especially for users with rich interaction history.
- Better Ranking — Instead of returning a flat list, use a ranking model (e.g. LightGBM) that combines multiple signals — tag match score, book popularity, author affinity — to score and rank recommendations more precisely.

---

## Summary

This solution focuses on simplicity, interpretability, and effective use of available data while handling key recommendation scenarios.

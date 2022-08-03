---
title: Home
layout: page
---

# Simple Gender Classifiers

## Gender and Race bias in Duckduckgo generated datset
I uesd Duckduckgo to generate my female-male dataset by searching for "female photos" and "male photos", and the model performs well on the testing set (err_rate = 0.17). However, the searching result of Duckduckgo and thus the whole dataset, including testing set, is biased. As a result, there are some interesting "mistakes" the classifier made:
1. When I tested **drag queen** photos, the one with beard and drag has female probability = 56%, and the one with half drag queen face and half male face has a super high female probs = 90% (see 2nd img pairs). Seems like the model depends on female features rather than male features to determine the gender, indicating how female are thought to belong to the second gender that's separated from "nature" human - males.
2. When tested with **angry** **female** photos (3rd img pairs), the model wrongly detected one of them to be male with male prob = 66%, while another angry female face with gentler facial expressions still got high female prob = 98%
3. When tested with **muscle** **female** photos (4th img pairs), the model detected one of them as male, showing their female probs = 72% and 42%, with female probs decreasing as muscle increasing
4. When tested with diferrent **races** (European and Asian) **male** photos (5th img pairs) with almost the same posture, the model has slightly higher confidence on the European one (male probs = 97%) than the Asian one (male probs = 89%).
5. At the same time, the model performed the same on European and Asian female photos (6th img pairs) with similar posture.
6. I tested male tears-noTears (tears eliminated by PS) photo pairs (7th img pairs)to see if non-vulnerability is one of the charactrissitcs the model learned, but no, surprisingly the one PSed **without** tears has actually **lowered** the male prob from 60% to 49%. I wonder if it's becuase PS contaminated the authenticity of the photo, or removing tears helped eye-detecting, or it's also caused biased dataset (though traditionally males are encouraged to be less emotional)?
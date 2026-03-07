---
title: "NSUT Hive"
excerpt: "A student-run academic review platform <br/> <img src='/images/p1cover.png'>"
collection: portfolio
---
<div align="center">
<img src='/images/p1cover.png'>
<br>
<a href='https://nsuthive.com' target="_blank">View Live Website</a>
<br>
<a href='https://github.com/IndoRexian/NSUT-Hive' target="_blank">View GitHub Repo</a>
</div>

## Overview
NSUT Hive is a student-run academic review platform designed to centralize insights about professors at NSUT.

Unlike discussion threads on different platforms, NH organises reviews into clearly defined and distinct rating categories, making reviews more comparable, searchable, and meaningful over time. 

## Core Features
- Passwordless Authentication from scratch (OTP Based).
- Structured Rating System based on distinct factors:
    - Teaching Effectiveness
    - Grading
    - Attendence Policy
    - Ease of Workload
- Bayesian Weighted Rating System for fair ranking.
- Reactions(likes and dislikes) on reviews.
- Encrypted Email Storage.

## Tech Stack
### Backend
- FastAPI
- SQLAlchemy 2.0
- PostgreSQL
- [JWT](https://www.jwt.io/) Based Authentication
- [Brevo](https://www.brevo.com/) (for delivering emails)

### Frontend
- NextJS v16
- Tailwind CSS
- [ShadCN UI](https://ui.shadcn.com/)
- [Hero UI v3](https://www.heroui.com/)

## Professors Data Scraping

A pretty easy task. All of the professors data such as their branches, images and more were just scraped from already publically available data from the [NSUT Official Website](https://www.nsut.ac.in/). Selenium library was used for the same. The script to do so can be found [here](https://github.com/IndoRexian/NSUTProfData).

## Ratings System Overview

To overcome the bias and to improve clarity of ratings for professor, NH uses a Bayesian weighted formula:

![Formula](https://latex.codecogs.com/png.image?\dpi{200}\bg{white}&space;Rating=\frac{Total&space;Reviews}{Total&space;Reviews&plus;Minimum&space;Reviews&space;Threshold}*Weighted&space;Average&plus;(\frac{Minimum&space;Reviews&space;Threshold}{Total&space;Reviews&plus;Minimum&space;Reviews&space;Threshold}*Global&space;Average))

This also solves the issue of a single review skyrocketing the rating of a professor in comparison to professors who have multiple reviews.

The `Minimum Reviews Threshold` is currently set to 5 and the `Global Average` is currently set to 3. However, these values are subject to change in later future considering the amount of reviews.

## Authentication Flow
1. User Enters Email.
2. OTP is generated and stored(hashed) with expiration.
3. Upon verification of OTP with the help of JWT, User is either redirected to account creation or an access token gets created.
4. The access token gets stored in HTTP-Only cookies.

- Future considerations:
    - Adding rate limits.
    - Adding the ability to ban users.

I plan on publishing a blog post soon regarding this project soon.
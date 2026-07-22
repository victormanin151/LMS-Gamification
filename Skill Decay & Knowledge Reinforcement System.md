# Skill Decay & Knowledge Reinforcement System

## Business Need

Traditional online learning platforms assume that once a learner completes a course, the acquired knowledge remains permanent. In reality, educational research demonstrates that knowledge naturally deteriorates when it is not practiced or applied over time. This phenomenon, commonly known as the **Forgetting Curve**, often results in learners forgetting concepts they had previously mastered.

Current learning management systems typically record course completion as a permanent achievement without evaluating whether the learner still retains the acquired knowledge months later. Consequently, certificates and completed courses may no longer accurately represent the learner's current abilities.

To address this limitation, the platform will introduce a **Skill Decay & Knowledge Reinforcement System** that continuously monitors knowledge usage and recommends revision activities before significant knowledge loss occurs.

---

# Business Objective

The objective of this feature is to transform learning from a one-time achievement into a continuous process of knowledge maintenance.

The system aims to:

- Improve long-term knowledge retention.
- Encourage regular revision of previously mastered concepts.
- Reduce knowledge loss caused by inactivity.
- Help learners maintain professional competencies.
- Increase learner engagement through personalized revision recommendations.

---

# Business Value

Instead of treating knowledge as permanently acquired, the platform recognizes that maintaining expertise requires continuous practice.

Rather than notifying learners that they have forgotten a skill, the platform proactively encourages revision through personalized recommendations.

For example, instead of displaying:

> Java Collections - Completed

the learner may see:

```text
Java Collections

██████████ 100%

Last Practiced: 7 months ago

Knowledge Health: 72%

Recommendation:
Complete two revision exercises to refresh your mastery.
```

This approach creates a realistic representation of the learner's current competency.

---

# Feature Overview

Every mastered knowledge node receives a **Knowledge Health Score** representing the learner's estimated familiarity with that topic.

Knowledge Health gradually decreases during periods of inactivity.

Completing relevant educational activities restores the Knowledge Health score.

Knowledge decay never removes certificates, achievements, or completed courses. Instead, it indicates when revision would be beneficial.

---

# Knowledge Health

Each mastered concept contains a health indicator.

Example:

```text
Java Programming

Variables          ██████████ 100%

Loops              █████████░ 90%

Collections        ███████░░░ 72%

Streams            █████░░░░░ 51%

Concurrency         ███░░░░░░ 32%
```

Lower Knowledge Health values indicate that revision is recommended.

---

# Reinforcement Activities

The platform recommends revision through several educational activities:

- Short quizzes
- Coding exercises
- Flashcards
- Practical projects
- AI-generated review questions
- Mini assessments

Completing reinforcement activities restores Knowledge Health.

---

# Intelligent Revision

Revision recommendations are personalized.

Examples:

> You have not practiced Java Streams for 90 days.

> Complete three short coding exercises to restore your mastery.

or

> SQL Joins appear to be weakening. A five-minute review is recommended.

The platform prioritizes concepts that are both important and likely to be forgotten.

---

# User Experience

Dashboard Example

```text
Knowledge Health

Java Collections        72%

SQL Joins               54%

REST APIs               94%

Docker                  48%
```

Weekly Summary

> Three previously mastered skills would benefit from revision this week.

---

# Business Rules

**BR-1**

Knowledge Health decreases only after prolonged inactivity.

**BR-2**

Knowledge Health never affects earned certificates or completed courses.

**BR-3**

Revision recommendations are generated automatically.

**BR-4**

Revision activities restore Knowledge Health.

**BR-5**

Administrators may configure decay rates for different knowledge categories.

---

# Technical Implementation

## Architecture

```text
User
 │
 ├── UserKnowledgeProgress
 │
 ├── KnowledgeHealth
 │
 └── RevisionHistory
```

## KnowledgeHealth Collection

```javascript
{
    user: ObjectId,

    knowledgeNode: ObjectId,

    healthScore: 82,

    lastPracticed: Date,

    decayRate: 0.15,

    recommendedRevision: true
}
```

The platform periodically recalculates Knowledge Health using learner activity and timestamps.

---

# Future Expansion

Future versions may include:

- AI-generated revision plans.
- Spaced repetition scheduling.
- Adaptive quiz difficulty.
- Calendar-based revision reminders.
- Integration with interview preparation mode.

The Skill Decay System transforms learning from a one-time accomplishment into a continuous process of knowledge reinforcement, helping learners maintain their competencies long after completing a course.

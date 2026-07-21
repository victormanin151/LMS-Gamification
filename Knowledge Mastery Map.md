# Business Requirement: Knowledge Mastery Map

## Business Need

Traditional online learning platforms primarily measure learner progress through course completion percentages and linear progress bars. While these indicators show how much content has been completed, they do not accurately represent what knowledge or skills the learner has actually acquired.

For example, two learners may both complete a Java Fundamentals course, yet one may have mastered Collections and Streams while the other struggles with these concepts. Despite this difference, both learners appear to have achieved identical progress.

This approach limits both learner self-assessment and personalized learning because it focuses on content completion rather than knowledge acquisition.

To address this limitation, the platform will introduce a **Knowledge Mastery Map**, replacing traditional progress indicators with a visual representation of mastered skills and learning paths.

---

# Business Objective

The objective of the Knowledge Mastery Map is to provide learners with a clear visualization of the knowledge they have acquired rather than simply tracking completed courses.

The system aims to:

- Shift learner focus from course completion to skill mastery.
- Improve learner understanding of their own strengths and weaknesses.
- Encourage continuous learning beyond individual courses.
- Provide personalized recommendations based on missing skills.
- Increase learner motivation through visible knowledge progression.

---

# Business Value

Rather than rewarding learners for finishing courses alone, the platform recognizes the specific concepts and competencies they have mastered.

This approach provides significantly more meaningful feedback.

Instead of displaying:

> Java Fundamentals - 100% Complete

the learner sees:

```text
Java Programming

✔ Variables
✔ Data Types
✔ Loops
✔ Methods
✔ Arrays
✔ Object-Oriented Programming
◐ Collections
✖ Streams
✖ Multithreading
```

This representation helps learners immediately understand what they know and what remains to be learned.

The Knowledge Mastery Map also provides employers and instructors with a more accurate representation of learner competencies.

---

# Feature Overview

The Knowledge Mastery Map organizes educational content into interconnected knowledge nodes.

Each node represents a specific skill or concept rather than an individual lesson or course.

Completing lessons, quizzes, practical exercises, or assessments contributes toward mastering these knowledge nodes.

The learner progressively unlocks new concepts as prerequisite skills are completed.

---

# Knowledge Structure

Learning content is represented as a hierarchical skill tree.

Example:

```text
Programming

├── Variables ✔
├── Data Types ✔
├── Loops ✔
├── Functions ✔
├── Arrays ✔
├── Object-Oriented Programming
│      ├── Classes ✔
│      ├── Objects ✔
│      ├── Inheritance
│      ├── Polymorphism
│      └── Encapsulation
│
├── Collections
│      ├── Lists ✔
│      ├── Sets
│      ├── Maps
│      └── Queues
│
└── Streams
```

Each skill may contain multiple child skills, allowing learners to understand how concepts build upon one another.

---

# Knowledge States

Each knowledge node can exist in one of several states.

| Status | Meaning |
|---------|----------|
| Locked | Prerequisite knowledge has not yet been completed. |
| Available | The learner may begin studying this concept. |
| In Progress | The learner has started learning the concept. |
| Mastered | The learner has successfully demonstrated competency. |
| Expert (Optional) | The learner consistently demonstrates advanced understanding. |

These states provide a more meaningful measure of progress than simple completion percentages.

---

# Mastery Evaluation

A concept is considered mastered only when the learner demonstrates sufficient understanding.

Mastery may be determined through one or more educational activities, including:

- Completing lessons.
- Passing quizzes above a predefined threshold.
- Completing practical programming exercises.
- Successfully finishing coding challenges.
- Completing assessments.
- Successfully applying prerequisite knowledge in later topics.

For example, completing a lesson alone may not immediately unlock mastery if assessment results indicate insufficient understanding.

---

# Progressive Unlocking

Knowledge is unlocked progressively based on prerequisite relationships.

Example:

```text
Variables
      │
      ▼
Loops
      │
      ▼
Arrays
      │
      ▼
Collections
      │
      ▼
Streams
```

Learners cannot access advanced concepts before demonstrating mastery of the required foundational knowledge.

This encourages structured learning while reducing cognitive overload.

---

# User Experience

Rather than presenting a traditional progress bar, learners interact with an interactive knowledge map.

Dashboard Example

```text
Java Backend Roadmap

✔ Variables

✔ Data Types

✔ Loops

✔ Methods

✔ Arrays

◐ Collections

🔒 Streams

🔒 Multithreading
```

Selecting a knowledge node displays:

- Learning resources
- Recommended exercises
- Related concepts
- Required prerequisites
- Suggested next topics

The learner always understands what to learn next.

---

# Personalized Recommendations

The Knowledge Mastery Map enables intelligent recommendations.

Examples:

If Collections are incomplete:

> Before learning Streams, we recommend strengthening your understanding of Java Collections.

If Arrays are mastered quickly:

> You have demonstrated strong understanding of Arrays. Consider attempting advanced coding challenges.

Recommendations become knowledge-driven rather than course-driven.

---

# Business Rules

**BR-1**

Every educational resource must be associated with one or more knowledge nodes.

**BR-2**

Knowledge mastery is determined by demonstrated competency rather than lesson completion alone.

**BR-3**

Advanced knowledge nodes require prerequisite skills to be mastered.

**BR-4**

Learners may revisit previously mastered concepts at any time.

**BR-5**

Knowledge mastery contributes toward achievements, experience points, and learning personalities.

**BR-6**

Administrators may modify knowledge dependencies without changing application code.

---

# Technical Implementation

## Architecture

The Knowledge Mastery Map should remain independent from the User model.

```text
User
 │
 ├── KnowledgeNode
 │
 ├── UserKnowledgeProgress
 │
 ├── LearningResources
 │
 └── Assessments
```

---

## KnowledgeNode Collection

```javascript
{
    title: "Java Collections",

    category: "Java",

    description: "...",

    prerequisites: [
        ObjectId("Arrays"),
        ObjectId("Objects")
    ],

    difficulty: "Intermediate",

    estimatedHours: 6
}
```

---

## UserKnowledgeProgress Collection

```javascript
{
    user: ObjectId,

    knowledgeNode: ObjectId,

    status: "MASTERED",

    masteryScore: 94,

    completedAt: Date,

    attempts: 3
}
```

---

# Event Processing

Whenever a learner completes an educational activity, the platform evaluates whether knowledge mastery has been achieved.

```text
Quiz Completed
        │
        ▼
Assessment Service
        │
        ▼
Knowledge Evaluation Engine
        │
        ▼
Update Mastery Score
        │
        ▼
Unlock New Knowledge Nodes
        │
        ▼
Generate Recommendations
```

The learner receives immediate feedback when new concepts become available.

---

# Future Expansion

The Knowledge Mastery Map serves as the foundation for a personalized learning ecosystem.

Future enhancements may include:

- AI-generated learning paths.
- Personalized revision recommendations.
- Employer-facing skill profiles.
- Adaptive assessments.
- Skill gap analysis for specific careers.
- Integration with certification programs.
- Dynamic roadmaps similar to NeetCode and roadmap.sh.

Instead of asking **"Which course should I take next?"**, learners begin asking **"Which skill should I master next?"**

This shifts the platform from being course-centric to knowledge-centric, creating a more meaningful representation of learner progress while supporting personalized education and long-term skill development.

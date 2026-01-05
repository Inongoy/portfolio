---
layout: project
type: project
image: img/life os/os_1.png
title: "Life Operating System"
date: 2025
published: true
labels:
  - TypeScript
  - JavaScript
  - HTML
  - React native
summary: "Life OS is a personal operating system built to help structure daily life through habits, goals, and intentional routines. Built with React Native, Expo, and TypeScript, it uses a modular, cross platform architecture to model personal growth as an evolving system rather than a collection of tasks."
---

<div class="text-center p-4">
  <img width="400px" src="../img/life os/os_3.png" class="img-thumbnail" >
  <img width="400px" src="../img/life os/os_5.png" class="img-thumbnail" >
  <img width="400px" src="../img/life os/os_8.png" class="img-thumbnail" >
</div>

Life OS is a personal operating system designed to help individuals structure their daily lives through intentional systems rather than isolated tasks. The application brings together habit tracking, goal management, and daily energy logging into a unified experience that emphasizes consistency, self awareness, and long term growth. Instead of focusing on productivity shortcuts, Life OS models personal routines as evolving data, allowing users to better understand their behaviors and build sustainable momentum over time.

From a technical perspective, Life OS is built using React Native with Expo, leveraging a cross platform architecture to ensure consistent behavior across iOS, Android, and web. The application uses TypeScript to enforce strong typing and improve maintainability as the project scales. State and persistence are handled through a modular storage layer, enabling habits, goals, and logs to be treated as reusable data models rather than hard coded features. Navigation is managed with Expo Router, supporting a clean, file based routing structure and predictable screen organization.

The project is designed with extensibility in mind, allowing new modules such as analytics, reflections, or integrations to be added without restructuring the core system. Life OS serves both as a functional personal tool and as an exploration of how software engineering principles such as modularity, data modeling, and system design can be applied to everyday life management.

Life OS explores how thoughtful software design can turn personal growth into a structured, adaptable system rather than a set of disconnected habits
<hr>
This code powers the core habit tracking logic in Life OS:

```cpp

const toggleHabit = (habitId: string) => {
  setHabits(prev => prev.map(habit => {
    if (habit.id === habitId) {
      const completedDates = habit.completedDates.includes(today)
        ? habit.completedDates.filter(d => d !== today)
        : [...habit.completedDates, today];
      return { ...habit, completedDates };
    }
    return habit;
  }));
};

const getStreakCount = (habit: Habit): number => {
  let streak = 0;
  const sortedDates = [...habit.completedDates].sort().reverse();
  let currentDate = new Date();

  for (const dateStr of sortedDates) {
    const expectedDate = formatDate(currentDate);

    if (dateStr === expectedDate) {
      streak++;
      currentDate.setDate(currentDate.getDate() - 1);
    } else {
      break;
    }
  }

  return streak;
};

```
<hr>

Here is the deployed application [Life Operating System](https://life-ops--plftoqbad2.expo.app/dashboard).
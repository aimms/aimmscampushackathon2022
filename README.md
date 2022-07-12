# aimmscampushackathon2022

This repository contains all information on the AIMMS 2022 Campus Hackathon

## The problem

The problem we selected is based on the [ITC 2021: International Timetabling Competition on Sports Timetabling](https://www.sportscheduling.ugent.be/ITC2021/index.php).

We will plan one-on-one matches between sports teams that belong to a single league. We call the complete set of matches a tournament. This tournament follows a double round-robin (2RR). Every team plays against every other team two times: once at home, once away. As a result we have (N - 1) x 2 matches per team, where N is the total number of teams.

The planning horizon is divided into slots ((N - 1) x 2). We assume that each team plays exactly once per slot. We also assume an even number of teams.
There are several types of constraints that we briefly present here. 

**The challenge can be very hard! We do not expect you to implement all constraints. We will have a growing level of difficulties, so don’t worry to get them all done!**

### Constraints

There are both soft and hard constraints. SOFT and HARD tags are included with each one. A PENALTY is also included for each unit of violation. The unit of violation depends on the constraint. A HARD constraint should always be satisfied (although this is sometimes very difficult).

### Objective function

We want to minimize the sum of penalized soft constraints violations.

### Structure

If the timetable instance is "phased", then the first half of slots in the tournament is a complete round-robin and the second half is another complete round-robin. That is, each pair of teams only sees each other once in each half, with their home-away status inverted between halves.

### Capacity Constraints


> <CA2 teams1="0" min="0" max="1" mode1="HA" mode2="GLOBAL" teams2="1;2“ slots ="0;1;2" type="SOFT"/>

> <CA1 teams="0" max="0" mode="H" slots="0" type="HARD"/>

Each team from teams plays at most max home/away games (mode = "H“ or “A”) during time slots in slots. Penalty is number of games over max.

Ex.: Team 0 cannot play at home on time slot 0.


> <CA2 teams1="0" min="0" max="1" mode1="HA" mode2="GLOBAL" teams2="1;2“ slots ="0;1;2" type="SOFT"/>

Each team in teams1 plays at most max home/away/any games (mode1 = "H“, “A” or “HA”), against teams in teams2 during time slots in slots. Mode2 will always be “GLOBAL”.

Penalty is number of games over max.

Ex.: Team 0 plays at most one game against teams 1 and 2 during the first three time slots. 

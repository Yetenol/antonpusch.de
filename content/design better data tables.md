---
title: "Design better data tables"
dg-publish: true
---
> Good user interface design is based on human goals and behavior. The user interface in-turn affects behavior, which drives further design decisions. In subtle and unconscious ways, user experience alters how humans make decisions. What is seen, where it is presented, and how interactions are afforded, influence actions. It is important we make design decisions that lead to a better world, one data table design at a time.

# Fixed Header

Fixing the row header as a user scrolls provides context on what column the user is on.
![1_kXEEaxvKP_9xRT0HuqScTQ.gif](./attachments/1_kxeeaxvkp_9xrt0huqsctq.gif)

# Horizontal Scroll

Horizontal scrolling is inevitable when presenting large datasets. It is good practice to place identifier data in the first column. As an advanced feature, enable individual locking of columns so users can compare data with multiple anchoring identifiers.
![1_Mp9kJSIlLyn5qjX-vD56iA.gif](./attachments/1_mp9kjsillyn5qjx-vd56ia.gif)

# Resizable columns

Resizing columns allows users to see abbreviated data in full.
![1_3Mjvd1N9OlQC-aMWXEVtBQ.gif](./attachments/1_3mjvd1n9olqc-amwxevtbq.gif)

# Row Style - Zebra Stripes, Line Divisions, Free Form.

The row style helps users scan data. Reducing visual noise by removing row lines or zebra stripes works well for small datasets. Users may lose their place when parsing larger datasets. Line divisions help users keep their place. Alternating rows (aka zebra stripes) help users keep their place when scanning long horizontal datasets. Although they cause usability problems when there is a small number of rows because users may ascribe meaning to the highlighted rows.
![1_yDwqntdUINCNJJTV7BXKzQ.gif](./attachments/1_ydwqntduincnjjtv7bxkzq.gif)

# Display Density

Smaller row height enables the user to view more data without the need for scrolling. However, it affects scannability leading to parsing errors. That is why many successful data table designs incorporate the ability to control display density.
![1_68Gj3oI6z0ssNSqX3sSQbw.gif](./attachments/1_68gj3oi6z0ssnsqx3ssqbw.gif)

# Visual Table Summary

A visual data summary provides an overview of the accompanying table. It allows the user to spot patterns and issues in aggregate before actioning summary insights.
![1_xhD2-Xa-jn1ve-jT0PLKTw.webp](./attachments/1_xhd2-xa-jn1ve-jt0plktw.webp)

# Pagination

Pagination works by presenting a set number of rows in a view, with the ability to navigate to another set. The above example provides the ability to customize the row count per view. Infinite scroll often replaces this pattern. Infinite scroll progressively loads results as a user scrolls. Infinite scroll works well for discovery websites but is usually disastrous for prioritization apps.
![1_yLNoP3bNRc37jHn28Mqucg.webp](./attachments/1_ylnop3bnrc37jhn28mqucg.webp)

# Hover Actions

Presenting additional action when a user hovers reduces visual clutter. However, it can cause discoverability issues because the user needs to interact with the table to expose the presentation of actions.
![1_dCPE8gp5tbaVouGODN5bRQ.gif](./attachments/1_dcpe8gp5tbavougodn5brq.gif)

# Inline Editing

Inline editing allows the user to change data without navigating to a separate details view.
![1_Sy9hS1AMycj5Uzo4VvckmQ.gif](./attachments/1_sy9hs1amycj5uzo4vvckmq.gif)

# Expandable Rows

Expandable rows allow the user to evaluate additional information without losing their context.
![1_0E1UPRzvK4gaV8sZEwOxLQ.gif](./attachments/1_0e1uprzvk4gav8szewoxlq.gif)

# Quick View

Much like expandable rows, quick view enables a user to view additional information while staying in context.
![1_Tt2x8SRugOlJQNsMdidF_g.gif](./attachments/1_tt2x8srugoljqnsmdidf_g.gif)

# Modal

Modals allow the user to stay within the table view but provides more focus on the additional information and actions.
![1_NSGIPqQ5nnFhunR8Osiunw.gif](./attachments/1_nsgipqq5nnfhunr8osiunw.gif)

# Multi-Modal

A multi-modal feature is powerful for active use users to crank through many actions or compare details of different items.
![1_Bu6hCcWjrXR0k_F5jEJO8g.gif](./attachments/1_bu6hccwjrxr0k_f5jejo8g.gif)

# Row to Details

Clicking on a row link transforms the table into a view with list items on the left and additional details on the right. It enables a user to parse large datasets, as well as reference many items without losing their place.
![1_HAkPMgQhO-0kFgh-ITT5qA.gif](./attachments/1_hakpmgqho-0kfgh-itt5qa.gif)

# Sortable Columns

Column sorting allows users to organize rows alphabetically and numerically.
![1_ViE5_uxbbU6LEfnV8GrQtA.webp](./attachments/1_vie5_uxbbu6lefnv8grqta.webp)

# Basic Filtering

Basic filtering allows users to manipulate the data presented in the table.
![1_TJJAdrX7xwlhuyLBmD37pg.webp](./attachments/1_tjjadrx7xwlhuylbmd37pg.webp)

# Filter Columns

This design pattern allows users to assign filtering parameters to specific columns.
![1_TKej8krSFjNDHoN43tOTkg.gif](./attachments/1_tkej8krsfjndhon43totkg.gif)

# Searchable Columns
This design pattern allows a user to search specific values within each column.
![1_jnENY_7hvq7iYlXayoQV3w.webp](./attachments/1_jneny_7hvq7iylxayoqv3w.webp)

# Add Columns
This pattern allows users to add columns from a dataset. It is a way to keep the table’s data limited to essential information and enables the user to add additional columns based on their use case.
![1_mFs9KK1VADJbN4hAtjLX1w.webp](./attachments/1_mfs9kk1vadjbn4hatjlx1w.webp)

# Customizable Columns
The customizable columns feature enables users to pick the columns they want to see and sort accordingly. The feature may include the ability to save presets for later use.
![1_0NZs7HZtRrB_TukLjxInIQ.webp](./attachments/1_0nzs7hztrrb_tukljxiniq.webp)


---
Sources:
- [Design better data tables. The ingredients of a successful data… | by Andrew Coyle | Medium](https://coyleandrew.medium.com/design-better-data-tables-4ecc99d23356)

Related:

Tags:
[User interface](User%20interface.md)
[Web design](Web%20design.md)
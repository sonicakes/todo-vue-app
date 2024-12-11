# Task List
Live URL: https://task-cakes.netlify.app/

## About This Project
This app was made following this challenge in Front End Mentor: https://www.frontendmentor.io/challenges/todo-app-Su1_KokOW

I've used the original design, adding a few tweaks here and there.

Main functionality of the app:

- Add new todos to the list
- Mark todos as complete
- Delete todos from the list
- Filter by all/active/complete todos
- Clear all completed todos
- Toggle light and dark mode
- View the optimal layout for the app depending on their device's screen size
- See hover states for all interactive elements on the page

Here are some of the deviations from the original brief:

1. Added a choice between a shopping list or a todo list. On start, there is a modal which contains those 2 choices. Depending on your choice, the background image changes. Also in shopping list, there is one item that cannot be deleted: it is called 'Bisto' which is my household's nickname for milk. Weird, I know.
2. Experiment with vue-draggable to implement drag and reorder functionality, but it broke on build when trying to deploy. Need to investigate the issue. Alternatively, would be great to learn drag/re-order from scratch!
3. Hiding how many items left when sorting by 'Completed', instead showing 'number of items completed'.
4. Contents of the list are stored in local storage for convenience.

### Tech stack
Vue 3, using Vue CLI this time, Sass.

### Potential improvements
- Add re-order functionality
- Add more accessibility
- Potentially connect to Back-End and make into full-stack app
- Commit theme selection (dark/light) to local storage as well
- Generate icon/image of the product on entering list item
- Add animation on checking/crossing the item off the list
- Add message 'congratulations! all is complete!' if all the items have been crossed off
- Ability to create multiple list and save them to the Back-End



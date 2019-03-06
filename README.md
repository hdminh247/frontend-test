# Front-end test

> Test for the front-end job position at My Cuistot.

At My Cuistot, we're hiring front-end developers to work with our lead developer on the My Cuistot platform.

This test aims to know if you know:

- Git
- HTML
- CSS
- Javascript
- VueJS

After performing the test ourselves, we estimate that it will take you up to 30 minutes to complete. If you take more time, it's okay!

## Instructions

To perform this test, we ask you to fork this into your Github account. You will perform the exercises in the order. Once finished, push your work in your fork and send us the link of it. Your fork must be public so we can see it.

If you can not do all the exercises it does not matter. Also, do not spend time on the design. Go straight to the code.

## Test
Run those commands
`
npm i &&
npm start
`
Web is served at port  8080

We are going to ask you to create a simple VueJS application so that our chefs can manage the food they have in their fridge.

### Exercise 1

Create a simple VueJS application.
In this Vue app, we want:

1) A page where the cook can add several foods via a form:
    - This form must consist of a text field for the name of the food, a numeric field for the quantity available and a button to submit this form.
2) When the cook submits this form, we want the food information to be added to a food list.

| Food         | Quantity |
|-----------------|----------|
| Tomatoes         | 12       |
| Potatoes | 3        |
| Asparagus        | 5        |

### Exercise 2

Now the chef can add foods to his list. However, after cooking for our clients, he has less tomatoes and no more asparagus.

So we want to be able to edit & delete the foods in this list.

For this we want:

1) For each element of the list, associate two actions "Edit" and "Delete".
2) When I click on "Edit", I want to have a modal with a form to be able to edit the name and the quantity of food for this item.
3) When I click on "Delete", it completely removes the food from the list

### Exercise 3

Oh darn! The chef closed his page by mistake. By reopening it, he discovers that he no longer has his list of foods!

We now want to be able to save the cook's food list locally.

For this we want:

1) That when performing any action, the list is saved in localStorage
2) When it closes and reopens its application, it finds the same list and can interact again

## What will be taken in consideration

The test is very simple so we will focus mainly on the quality of the code and the logic implemented to solve the problems.

Good luck and see you soon.

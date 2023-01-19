# Wolt Summer 2023 Engineering Internships

Preliminary Assignment for Engineering Positions

Welcome! We are delighted to see you applying. Now it's your time to shine.

**NOTE! Please do only *one* of backend OR frontend OR mobile implementation.**

**Please take your time, use the entire time available to complete this to the best of your ability - we do not prioritise submissions by speed!** 
<p align="center" border="none">
  <img alt="Yuho, the Wolt mascot" src="./yuhos.png" align="center">
</p>

## Delivery Fee Calculator

The goal of the assignment is to showcase your coding skills and ability to develop features. We DON'T expect you to build production quality code. This is a highly important part of the hiring process so it's crucial to put effort into this without making it too bloated. Reviewers will put weight on three main aspects: code quality, maintainability, and testing. Based on the results of the assignment review, we will make the decision on proceeding to the technical interview.

Your task is to write a delivery fee calculator. This code is needed when a customer is ready with their shopping cart and we’d like to show them how much the delivery will cost. The delivery price depends on the cart value, the number of items in the cart, the time of the order, and the delivery distance.


### Specification
Rules for calculating a delivery fee
* If the cart value is less than 10€, a small order surcharge is added to the delivery price. The surcharge is the difference between the cart value and 10€. For example if the cart value is 8.90€, the surcharge will be 1.10€.
* A delivery fee for the first 1000 meters (=1km) is 2€. If the delivery distance is longer than that, 1€ is added for every additional 500 meters that the courier needs to travel before reaching the destination. Even if the distance would be shorter than 500 meters, the minimum fee is always 1€.
  * Example 1: If the delivery distance is 1499 meters, the delivery fee is: 2€ base fee + 1€ for the additional 500 m => 3€
  * Example 2: If the delivery distance is 1500 meters, the delivery fee is: 2€ base fee + 1€ for the additional 500 m => 3€
  * Example 3: If the delivery distance is 1501 meters, the delivery fee is: 2€ base fee + 1€ for the first 500 m + 1€ for the second 500 m => 4€
* If the number of items is five or more, an additional 50 cent surcharge is added for each item above and including the fifth item. An extra "bulk" fee applies for more than 12 items of 1,20€
  * Example 1: If the number of items is 4, no extra surcharge
  * Example 2: If the number of items is 5, 50 cents surcharge is added
  * Example 3: If the number of items is 10, 3€ surcharge (6 x 50 cents) is added
  * Example 4: If the number of items is 13, 5,70€ surcharge is added ((9 * 50 cents) + 1,20€)
* The delivery fee can __never__ be more than 15€, including possible surcharges.
* The delivery is free (0€) when the cart value is equal or more than 100€. 
* During the Friday rush (3 - 7 PM UTC), the delivery fee (the total fee including possible surcharges) will be multiplied by 1.2x. However, the fee still cannot be more than the max (15€).

### Expectations
When reviewing your code, we will focus on the part that fulfils the requirements explained above. We would love to see a well-tested and readable solution.

Pro tip: When you think you are ready with the assignment, take at least a few hours break, and then go through the code one more time before returning it.

### Submitting the assignment
Bundle everything into a Zip archive and upload it to Google Drive, Dropbox or similar and include the link in the application. Remember to check permissions! If we cannot access the file, we cannot review your code. Please don’t store your solution in a public GitHub repository during the application period.

A good check before sending your task is to unzip the Zip archive into a new folder and check that building and running the project works, using the steps you define in readme.md. Forgotten dependencies and instructions can sometimes happen even to the best of us.

## Backend specifics

### Your task
Your task is to build an HTTP API which could be used for calculating the delivery fee.

Please implement your solution in either **Python, Kotlin or Scala**. Feel free to use libraries / frameworks.

**Note that your technology choice here defines the scope the possible technical interview and your focus area if starting to work at Wolt 😊**


### Specification
Implement an HTTP API (single endpoint) which calculates the delivery fee based on the information in the request payload (JSON) and includes the calculated delivery fee in the response payload (JSON).

#### Request
Example: 
```json
{"cart_value": 790, "delivery_distance": 2235, "number_of_items": 4, "time": "2021-10-12T13:00:00Z"}
```

##### Field details

| Field             | Type  | Description                                                           | Example value                             |
|:---               |:---   |:---                                                                   |:---                                       |
|cart_value         |Integer|Value of the shopping cart __in cents__.                               |__790__ (790 cents = 7.90€)                |
|delivery_distance  |Integer|The distance between the store and customer’s location __in meters__.  |__2235__ (2235 meters = 2.235 km)          |
|number_of_items    |Integer|The __number of items__ in the customer's shopping cart.               |__4__ (customer has 4 items in the cart)   |
|time               |String |Order time in [ISO format](https://en.wikipedia.org/wiki/ISO_8601).    |__2021-01-16T13:00:00Z__                   |

#### Response
Example:
```json
{"delivery_fee": 710}
```

##### Field details

| Field         | Type  | Description                           | Example value             |
|:---           |:---   |:---                                   |:---                       |
|delivery_fee   |Integer|Calculated delivery fee __in cents__.  |__710__ (710 cents = 7.10€)|

## Frontend specifics

### Your task

Build a delivery fee calculator web app using **React and TypeScript**.

### Specification

Build a delivery fee calculator app which calculates a delivery fee based on user input and shows the calculated delivery fee to the user.

#### Input fields

| Field             | Type      | Description                                                                                             | Example value                             |
|:---               |:---       |:---                                                                                                     |:---                                       |
|Cart value         |Float      |Value of the shopping cart in euros.                                                                     |__20__                                     |
|Delivery distance  |Integer    |The distance between the store and customer’s location __in meters__.                                    |__2235__ (2235 meters = 2.235 km)          |
|Number of items    |Integer    |The __number of items__ in the customer's shopping cart.                                                 |__4__ (customer has 4 items in the cart)   |
|Order time         |Date + Time|The date/time when the order is being made (see rules-section how rush hours affect the delivery price)  |You can choose the most suitable format    |


#### Output example

Feel free to design and implement the user interface how you want. Below is an example of what it could look like.

When reviewing the assignment we are focusing on the code quality and structure of your app. However, good UX & design will definitely give you bonus points.

![Example user interface](./example-ui.png)

## Mobile specifics

### Concept

A user is walking around Helsinki city centre looking for a place to eat.

### Input

* Coordinates that represent the user's location on a timeline. 
* Wolt API endpoint that accepts a location and returns a list of venues next to it.

## Task

Build an app that displays a list of venues for the user's current location. The list should contain a maximum of <u>15</u> venues. If the server response has more then use the first <u>15</u>. 

Each venue also has a "Favorite" action next to it. "Favorite" works as a toggle (true/false) and changes the icon depending on the state. Your app should remember these states and reapply them to venues when the app is opened again.

## Platform-specific requirements

For Android you should be following the Google guidelines on how to develop an Android application. Specifically, it should use Kotlin as the language, MVVM as the UI architectural pattern and Clean architecture as the data access pattern.

For iOS we would be looking for Swift using UIKit.

## Example of design

You can see the following example design in more detail in this [Figma project](https://www.figma.com/file/T8lq53pR8etMduzjlTU3Qh/Android-Engineering-assignment-assets?node-id=0%3A1&t=DZ8XHrLrUt5j6wU4-1). Information such as typeface, font size, margin and padding of views, etc. should be accessible after login in to your personal Figma account.

The password to access this Figma project is `Y2MeWWOLBi`.

![Example user interface](./example-mobile-ui.png)

## Actual input 

### API Endpoint
GET https://restaurant-api.wolt.com/v1/pages/restaurants?lat=60.170187&lon=24.930599

### Important fields in response (JSON): 
| Path / Key                                      | Meaning                  |
|-------------------------------------------------|--------------------------|
| sections -> items -> venue -> id                | Unique id of the venue   |
| sections -> items -> venue -> name              | Name of the venue        |
| sections -> items -> venue -> short_description | Description of the venue |
| sections -> items -> image -> url               | Image URL for the venue  |

| Example coordinates (latitude / longitude)  |
|----------------------|
| 60.170187, 24.930599 |
| 60.169418, 24.931618 |
| 60.169818, 24.932906 |
| 60.170005, 24.935105 |
| 60.169108, 24.936210 |
| 60.168355, 24.934869 |
| 60.167560, 24.932562 |
| 60.168254, 24.931532 |
| 60.169012, 24.930341 |
| 60.170085, 24.929569 |

| Assets           |                                                                      |
|------------------|----------------------------------------------------------------------|
| Favorite (true)  | https://material.io/tools/icons/?icon=favorite&style=baseline        |
| Favorite (false) | https://material.io/tools/icons/?icon=favorite_border&style=baseline |


## FAQ
### How much time should I spend on this task?
We expect you to be pragmatic and not overcomplicate things. You can take shortcuts where it makes sense to you.

### Do I need to build any animations?
This is a creative task and we would love to see your approach. At Wolt we love good user experiences, so any animation that brings delights would be appreciated. One good example would be the favourite button.

### Does my app need to support different screen orientations?
No, portrait mode is good with us.

### Do I need to strictly follow the design example?
If you have a good idea of how to improve the user experience here, we would love to see it. This is however not a requirement, so if you don’t have any ideas, try to stick closely to the given design.

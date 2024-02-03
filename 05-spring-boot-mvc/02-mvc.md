# MVC Pattern

## Controller:

- In Spring MVC, a Controller is responsible for handling user requests, processing them, and returning an appropriate response.
- Controllers are Java classes annotated with @Controller and are typically responsible for handling a specific set of URLs or request mappings.
- They process user input, interact with the model, and determine the view to be rendered.
## Model:

- The Model represents the data of the application. It holds the business logic and state information.
- In Spring MVC, the model is often represented by a POJO (Plain Old Java Object) annotated with @ModelAttribute.
- The controller manipulates the model, and the data is then passed to the view for rendering.
## View:

- The View is responsible for rendering the data provided by the model.
- In Spring MVC, the view is usually a JSP (JavaServer Pages), Thymeleaf template, or other template engines.
- The view receives data from the model and displays it to the user. It is not responsible for business logic.

## How they work together

- When a user sends a request, the controller processes it. The controller may update the model based on the request parameters.
- The controller then selects the appropriate view based on the requested URL and updates the model attributes.
- The view receives the model data and renders the HTML or other content to be sent back to the user.
- The response is sent to the user's browser.
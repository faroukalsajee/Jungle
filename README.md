# Jungle
A mini e-commerce application built with Ruby (-v2.3.5) on Rails (-v4.2) as a student assignment for Lighhouse Labs full-stack web development program. TDD (test-driven development) practices are followed using RSpec library. Stripe platform is used for payments.

# Functional Requirements
## Feature: Sold Out Badge
* When a product has 0 quantity, a sold out badge should be displayed on the product list page
* Should ideally be implemented as a question/boolean method in view helper and/or Product model

## Feature: Admin Categories
* Admin users can list and create new categories
* Admins can add new products using the new category
* Restful routes (resources) should be used, and there should be no extra, unused routes exposed
* All admin controllers inherit from Admin::BaseController (or similarly named) abstract controller, containing the authentication filter

## Feature: User Authentication
* As a Visitor I can go to the registration page from any page in order to create an account
* As a Visitor I can sign up for a user account with my e-mail, password, first name and last name
* As a Visitor I can sign in using my e-mail and password
* As a User I can log out from any page
* As a User I cannot sign up with an existing e-mail address (uniqueness validation)
* Passwords are not stored as plain text in the database. Instead, has_secure_password is used in the User model, leveraging the bcrypt gem

## Enhancement: Order Details Page
* The order page contains items, their image, name, description, quantities and line item totals
* The final amount for the order is displayed
* The email that was used to place the order is displayed
* As a Visitor I can place an order (i.e. without logging in and therefore without an e-mail address). The original functionality from the inherited code (even though it is not realistic) should therefore not be suppressed.

## Bug: Missing Admin Security
* User must enter HTTP auth login/password to access admin functionality
* Should ideally be implemented in an abstract top-level class for admin controllers (e.g., Admin::BaseController which the other concrete admin controllers inherit)

## Bug: Checking Out with Empty Cart
* When the cart is empty and the user goes to the carts#show page, instead of displaying the contents and a stripe checkout button, display a friendly message about how it is empty and link to the home page

## Git
* The git commit history should have multiple commits and reasonable commit messages. There should be good use of branching and merging for each feature.

## Additional Steps for Apple M1 Machines

1. Make sure that you are runnning Ruby 2.6.6 (`ruby -v`)
1. Install ImageMagick `brew install imagemagick imagemagick@6 --build-from-source`
2. Remove Gemfile.lock
3. Replace Gemfile with version provided [here](https://gist.githubusercontent.com/FrancisBourgouin/831795ae12c4704687a0c2496d91a727/raw/ce8e2104f725f43e56650d404169c7b11c33a5c5/Gemfile)

## Setup

1. Run `bundle install` to install dependencies
2. Create `config/database.yml` by copying `config/database.example.yml`
3. Create `config/secrets.yml` by copying `config/secrets.example.yml`
4. Run `bin/rake db:reset` to create, load and seed db
5. Create .env file based on .env.example
6. Sign up for a Stripe account
7. Put Stripe (test) keys into appropriate .env vars
8. Run `bin/rails s -b 0.0.0.0` to start the server

## Stripe Testing

Use Credit Card # 4111 1111 1111 1111 for testing success scenarios.

More information in their docs: <https://stripe.com/docs/testing#cards>

## Dependencies

* Rails 4.2 [Rails Guide](http://guides.rubyonrails.org/v4.2/)
* PostgreSQL 9.x
* Stripe

# 🧠 Assignment: Interactive Web Pages with JavaScript

Welcome to the exciting world of interactivity! This assignment is all about **making your web pages feel alive**. You’ll learn how to respond to user actions, build engaging components, and validate form input—without reloading the page. This is where JavaScript gets fun, practical, and powerful. 🚀

---

## 🎉 Part 1: JavaScript Event Handling and Interactive Elements

Let’s start with the basics of **event handling**. You'll set up JavaScript to listen for user actions like clicks, mouseovers, keyboard input, and more—and respond to them in meaningful ways.

**Goal:** Use event listeners to react to user behavior and trigger changes on the page (e.g., showing messages, toggling classes, hiding/showing content).

---

## 🎮 Part 2: Building Interactive Elements

Now it’s time to apply what you’ve learned by creating your own mini interactive features. You can build things like:

* A light/dark mode toggle
* A counter or button game
* A collapsible FAQ section
* A simple dropdown menu
* A tabbed interface

**Goal:** Use DOM manipulation + events to make the page dynamic and engaging. Be creative!

---

## 📋✅ Part 3: Form Validation with JavaScript

Forms are essential to the web—and validating them properly is key to good user experience. You’ll build a form with multiple input fields (name, email, password, etc.) and write JavaScript to validate each field when the user submits or types.

**Goal:** Prevent incorrect form submissions by writing custom validation logic using conditions and regular expressions. Show user-friendly error messages and success feedback.

---

## Deliverables

* `index.html`: Your structured web page with at least one form and several interactive sections
* `script.js`: Your JavaScript file with:

  * Event handling for buttons, inputs, or links
  * At least 2 interactive features created from scratch
  * A fully functioning custom form validation (no HTML5-only validation)
* `style.css` (optional but encouraged): To style your interactive elements

Each section of your JavaScript should be commented to explain its purpose.

---

## Outcome

* Use of event listeners and appropriate event types
* Creativity and functionality of interactive elements
* Form validation accuracy and helpfulness of feedback
* Clear, modular, and well-commented JavaScript code
* A clean and functional user experience


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Interactive Form & Page</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>Interactive Web Page Demo</h1>
  </header>

  <main>
    <!-- Section 1: Form -->
    <section id="form-section">
      <h2>Contact Us Form</h2>
      <form id="contactForm" novalidate>
        <div>
          <label for="username">Name:</label>
          <input type="text" id="username" name="username">
          <div class="error" id="error-username"></div>
        </div>
        <div>
          <label for="email">Email:</label>
          <input type="text" id="email" name="email">
          <div class="error" id="error-email"></div>
        </div>
        <div>
          <label for="message">Message:</label>
          <textarea id="message" name="message"></textarea>
          <div class="error" id="error-message"></div>
        </div>
        <button type="submit" id="submitBtn">Send Message</button>
      </form>
      <div id="formSuccess" class="success"></div>
    </section>

    <!-- Section 2: Interactive Feature A -->
    <section id="featureA">
      <h2>Interactive Feature: Random Quote</h2>
      <button id="btnQuote">Get a Quote</button>
      <p id="quoteDisplay"></p>
    </section>

    <!-- Section 3: Interactive Feature B -->
    <section id="featureB">
      <h2>Interactive Feature: Toggle Color Theme</h2>
      <button id="btnTheme">Toggle Theme</button>
    </section>
  </main>

  <script src="script.js"></script>
</body>
</html>

script.js
/* -----------------------------
   Event Handling & Organization
-------------------------------*/

/* Part 1: Form Validation Logic */

// Grab form & related elements
const contactForm = document.getElementById('contactForm');
const usernameInput = document.getElementById('username');
const emailInput    = document.getElementById('email');
const messageInput  = document.getElementById('message');
const errorUsername = document.getElementById('error-username');
const errorEmail    = document.getElementById('error-email');
const errorMessage  = document.getElementById('error-message');
const formSuccess   = document.getElementById('formSuccess');

// Custom validation function
function validateForm() {
  let isValid = true;

  // Clear previous errors
  errorUsername.textContent = '';
  errorEmail.textContent = '';
  errorMessage.textContent = '';
  formSuccess.textContent = '';

  // Name validation: not empty
  if (!usernameInput.value.trim()) {
    errorUsername.textContent = 'Name is required.';
    isValid = false;
  }

  // Email validation: basic pattern
  const emailPattern = /^[^@\s]+@[^@\s]+\.[^@\s]+$/;
  if (!emailInput.value.trim()) {
    errorEmail.textContent = 'Email is required.';
    isValid = false;
  } else if (!emailPattern.test(emailInput.value.trim())) {
    errorEmail.textContent = 'Please enter a valid email address.';
    isValid = false;
  }

  // Message validation: minimum length
  if (!messageInput.value.trim()) {
    errorMessage.textContent = 'Message cannot be empty.';
    isValid = false;
  } else if (messageInput.value.trim().length < 10) {
    errorMessage.textContent = 'Message must be at least 10 characters.';
    isValid = false;
  }

  return isValid;
}

// Form submit handler
contactForm.addEventListener('submit', event => {
  event.preventDefault();
  if (validateForm()) {
    formSuccess.textContent = 'Form submitted successfully!';
    contactForm.reset();
  }
});


/* Part 2: Interactive Feature A — Random Quote Generator */

const quotes = [
  "The journey of a thousand miles begins with one step.",
  "Knowledge is power.",
  "Be yourself; everyone else is already taken."
];
const btnQuote = document.getElementById('btnQuote');
const quoteDisplay = document.getElementById('quoteDisplay');

btnQuote.addEventListener('click', () => {
  const randomIndex = Math.floor(Math.random() * quotes.length);
  quoteDisplay.textContent = quotes[randomIndex];
});


/* Part 3: Interactive Feature B — Theme Toggle */

const btnTheme = document.getElementById('btnTheme');
let darkMode = false;

btnTheme.addEventListener('click', () => {
  darkMode = !darkMode;
  document.body.classList.toggle('dark-theme', darkMode);
  btnTheme.textContent = darkMode ? 'Switch to Light Theme' : 'Switch to Dark Theme';
});


/* Part 4: Additional Event Handling (for demonstration) */

// Clear error message when typing in username
usernameInput.addEventListener('input', () => errorUsername.textContent = '');

// Clear error message when typing in email
emailInput.addEventListener('input', () => errorEmail.textContent = '');

// Clear error when typing in message
messageInput.addEventListener('input', () => errorMessage.textContent = '');


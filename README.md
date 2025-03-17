Here's a sample `README.md` file for your **Dev Detective** app that includes the relevant information and also uses emojis to make it more engaging:

---

# Dev Detective 🕵️‍♂️💻

Welcome to **Dev Detective**, an interactive app where you can search for GitHub user profiles and explore details like repositories, followers, bio, and more! 🚀

### Features
- 🔍 **Search GitHub Profiles**: Enter a username to view details like repositories, followers, bio, and more.
- 🌑 **Dark Mode & Light Mode**: Switch between dark and light themes based on your preference.
- 👥 **Profile Details**: View a user's avatar, name, username, joined date, and more.
- 📅 **GitHub Stats**: See stats like number of repositories, followers, following, and user location.

### How to Use

1. **Search for a User**:
   - Enter a GitHub username in the search bar.
   - Hit the `Enter` key or click the search button 🔍 to load their profile.
   - If the username is not found, you'll see a `No Results` message.

2. **Toggle Dark Mode**:
   - Click the 🌙 icon to switch to Dark Mode or click the 🌞 icon to return to Light Mode.
   - The app will remember your theme preference using local storage, so you don't need to switch it every time you visit.

### How It Works
- The app fetches data using the [GitHub API](https://api.github.com/users/).
- It dynamically updates the UI based on the fetched data.
- You can explore a GitHub user's repositories, followers, following, and other relevant information.

### Technologies Used
- **HTML**: Structure of the app
- **CSS**: Styling and theming (light/dark mode)
- **JavaScript**: API calls, dynamic data rendering, and theme toggling

### Code Overview

Here's a breakdown of the important code sections in your app:

#### Variables & DOM Elements:
```javascript
const searchbar = document.querySelector(".searchbar-container");
const profilecontainer = document.querySelector(".profile-container");
const root = document.documentElement.style;
const get = (param) => document.getElementById(`${param}`);
const url = "https://api.github.com/users/";
const btnsubmit = get("submit");
const input = get("input");
// Other variables for profile elements like avatar, name, date, etc.
```

#### Event Listeners:
- When the search button is clicked or the `Enter` key is pressed, it triggers an API call to fetch the user data:
```javascript
btnsubmit.addEventListener("click", function () {
  if (input.value !== "") {
    getUserData(url + input.value);
  } else {
    alert("Enter some input to search");
  }
});
```

#### Fetching GitHub User Data:
- The `getUserData` function makes an API call to GitHub's user endpoint:
```javascript
function getUserData(gitUrl) {
  fetch(gitUrl)
    .then((response) => response.json())
    .then((data) => {
      updateProfile(data);
    })
    .catch((error) => {
      throw error;
    });
}
```

#### Dark Mode and Light Mode:
- Functions to switch between dark and light modes based on user preference:
```javascript
function darkModeProperties() {
  root.setProperty("--lm-bg", "#141D2F");
  root.setProperty("--lm-bg-content", "#1E2A47");
  root.setProperty("--lm-text", "white");
  // More CSS properties for dark mode
  localStorage.setItem("dark-mode", true);
}

function lightModeProperties() {
  root.setProperty("--lm-bg", "#F6F8FF");
  root.setProperty("--lm-bg-content", "#FEFEFE");
  root.setProperty("--lm-text", "#4B6A9B");
  // More CSS properties for light mode
  localStorage.setItem("dark-mode", false);
}
```

#### Initializing the App:
- The app loads a default profile when it initializes:
```javascript
function init() {
  const value = localStorage.getItem("dark-mode");
  if (value === null) {
    lightModeProperties();
  } else if (value === "true") {
    darkModeProperties();
  } else {
    lightModeProperties();
  }

  // Default user: Pranay Gupta
  getUserData(url + "hussain-2025");
}
init();
```

### Screenshot
![Dev Detective](./images/screenshot.png)

### Demo
You can view a live demo of the app here: [Dev Detective Demo](https://yourdemo.com).

### License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Feel free to adjust the content to match any additional features or changes you've made!

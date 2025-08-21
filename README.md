# GitHub Website Template

This repository provides a template for creating a personal academic website using GitHub Pages.

---

## How to Use This Template

1. **Fork the repository**  
   Click the **Fork** button, and in the **Repository name** field, enter:  
   `your-github-username.github.io`

2. **Enable GitHub Pages**  
   - Go to your repository **Settings → Pages**  
   - Set the **Branch** to `master/root` or `main/root`  
   - Click **Save**  
   After a short wait, you will see a **Visit site** button under the **GitHub Pages** section. Click it to view your website.

---

## Quick Start Example: Add a New Page

Suppose you want to add an **News** page:

1. Create a new file named `news.md` in the main directory with the following content:

    ```yaml
    ---
    layout: normal
    title: News
    ---
    ```

    Add any content you like below the header.

2. Open `_includes/navbar.html` and add:

    ```html
    <div class="menu-item">
    <a href="news.html" {% if page.url == "/news.html" %}class="current"{% endif %}>News</a>
    </div>
    ```

3. Commit your changes.
   You should now see the **News** item in the navigation bar.

---

## File and Folder Overview

### `_includes/navbar.html`
- Controls the **left navigation bar**.  
- To add a new item:
  1. Create a new file `ABC.md` in the main directory.  
  2. Add the following code inside `navbar.html`:  

     ```html
     <div class="menu-item">
       <a href="ABC.html" {% if page.url == "/ABC.html" %}class="current"{% endif %}>XXX</a>
     </div>
     ```

  - `ABC` must match the name of your `.md` file (without extension).  
  - `XXX` is the text displayed on the navigation bar.  


### `_layouts/homepage.html`
- Controls the **homepage layout**, including profile photo and personal information (on the right of the photo).  
- To adjust photo size, edit the following line:  

  ```html
  <a href="index.html"><img src="{{site.avatar}}" alt="alt text" height="180px" /></a>
  ```
- Information fields such as **position**, **department**, and **affiliation** are displayed using conditional blocks like:

  ```liquid
  {% if site.position %}…{% endif %}
  {% if site.department %}…{% endif %}
  {% if site.affiliation %}…{% endif %}
  ```
- The actual text and links are configured in `_config.yml`.
- If a field is empty, it will not be shown.
  
### `_layouts/normal.html`
- Controls the layout for other pages (e.g., **Publications**, **People**).

### `assets/css/jemdocCustom.css`
- Defines custom styles for homepage and other pages.
- Used by both `homepage.html` and `normal.html`.

### `assets/css/style.css`
- Contains **default styles**.
- Generally no modification is needed.
- Not used in `homepage.html` and `normal.html`.


### `img/`
- Stores image files (e.g., profile photo, figures).

### `publication/`
- Stores PDF files of conference and journal papers.

### `_config.yml`
- Defines (examples):
  - Website title (shown at the top of the homepage).
  - Profile information (displayed next to the right of the photo).
  - Link to the profile photo.

### `index.md`
- Defines **homepage content**.
- Uses the `homepage` layout:
    ```yaml
    ---
    layout: homepage
    ---
    ```

### `publications.md`
- Defines **Publications** page content.
- Uses the `normal` layout and sets the title:
    ```yaml
    ---
    layout: normal
    title: Publications
    ---
    ```
- The `title` value will be displayed at the top of this page.

### `people.md`
- Defines **People** page content.
- Uses the `normal` layout and sets the title:
    ```yaml
    ---
    layout: normal
    title: People
    ---
    ```
- The `title` value will be displayed at the top of this page.
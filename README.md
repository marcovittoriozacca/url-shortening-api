# URL shortening API landing page

This was one of my first attempts at using the Tailwind CSS library and Vue3 with the Composition API, as I've previously only used the Option API with Bootstrap.

It's a straightforward exercise I found on[Frontend Mentor](https://www.frontendmentor.io/challenges/url-shortening-api-landing-page-2ce3ob-G) (click to view the challenge)

The challenge involves creating a website for shortening URLs using the [CleanURI](https://cleanuri.com/) API.

Unfortunately, the API provided by the challenge seems to not be functioning properly, so I've replaced CleanURI with the free and accessible TinyURL API, which doesn't require any registration.

## Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow
- [Vue.js](https://vuejs.org/) - JS library - Composition
- [VueUse](https://vueuse.org/) - Utilities
- [TailwindCSS](https://tailwindcss.com/) - CSS library



## Milestones

- View the optimal layout for the site depending on their device's screen size
- Shorten any valid URL
- See a list of their shortened links, even after refreshing the browser
- Copy the shortened link to their clipboard in a single click
- Receive an error message when the `form` is submitted if:
  - The `input` field is empty

## Screenshots

#### Views
<div style="display: flex;">
    <div style="flex: 1; text-align: center;">
    <h2>Desktop</h2>
        <img src="/public/screenshots/desktop-view.png">
    </div>
</div>
<div style="display: flex;">
    <div style="flex: 1; text-align: center;">
    <h2>Mobile</h2>
        <img src="/public/screenshots/mobile-view.png">
    </div>
</div>

<div style="display: flex;">
    <div style="flex: 1; text-align: center;">
    <h2>Mobile Menu</h2>
        <img src="/public/screenshots/mobile-menu.png">
    </div>
</div>

<h2 style="text-align: center;">Input Error</h2>
<div style="display: flex;">
    <div style="flex: 1;">
        <img src="/public/screenshots/mobile-error.png">
    </div>
    <div style="flex: 1; margin-top: 15px">
        <img src="/public/screenshots/desktop-error.png">
    </div>
</div>

<h2 style="text-align: center;">Copied Button State</h2>
<div style="display: flex;">
    <div style="flex: 1;">
        <img src="/public/screenshots/active-copied-mobile-button.png">
    </div>
    <div style="flex: 1; margin-top: 15px">
        <img src="/public/screenshots/active-copied-desktop-button.png">
    </div>
</div>

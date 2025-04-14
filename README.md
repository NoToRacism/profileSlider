# React Image/Quote Slider

This project is a simple and responsive image or quote slider component built with React. It allows you to display a list of items (in this case, people with images, names, titles, and quotes) in a rotating carousel with both manual and automatic navigation.

## Features

* **Automatic Sliding:** The slider automatically transitions to the next item after a set interval (5 seconds by default).
* **Manual Navigation:** Users can manually navigate through the items using "previous" and "next" buttons.
* **Infinite Loop:** The slider loops back to the beginning or end seamlessly.
* **Responsive Design:** The basic structure is responsive, though you might need to add your own CSS for specific layout adjustments.
* **Uses React Icons:** Leverages `react-icons` for the navigation arrows and quote icon.

## Technologies Used

* **React:** A JavaScript library for building user interfaces.
* **React Hooks:** Utilizes `useState` and `useEffect` for managing component state and side effects.
* **CSS:** For styling the slider component.
* **React Icons:** A library of popular icon sets.

## Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/NoToRacism/profileSlider
    ```
    
2.  **Navigate to the project directory:**
    ```bash
    cd your-slider-project
    ```

3.  **Install dependencies:**
    ```bash
    npm install  # or yarn install
    ```

## How It Works

1.  **Data Initialization (`Carousel.jsx`):**
    * The `Carousel` component imports the `longList` array from `./data` which contains the data for each slide.
    * This data is set as the initial state for the `people` state variable using the `useState` hook.

2.  **Current Person State (`Carousel.jsx`):**
    * The `currentPerson` state variable, initialized to `0`, keeps track of the index of the currently visible slide.

3.  **Rendering Slides (`Carousel.jsx`):**
    * In the `return` statement, a `slider-container` section is set up to hold all the slides.
    * The `people` array is mapped over to create each individual slide (`<article className='slide'>`).
    * For each person in the array, their `id`, `image`, `name`, `title`, and `quote` are extracted and rendered within the `<article>`.

4.  **Slide Positioning and Visibility (`Carousel.jsx`):**
    * Each slide's position is controlled by inline styles using the `transform: translateX()` property. The value is calculated based on the `personIndex` and the `currentPerson` state. This ensures that only the current slide is visible in the center.
    * The `opacity` and `visibility` styles are also conditionally applied to ensure only the current slide is fully visible.

5.  **Previous Slide Functionality (`Carousel.jsx`):**
    * The `prevSlide` function updates the `currentPerson` state. It subtracts 1 from the current index.
    * The `(+ people.length)` and `% people.length` ensure that when the user is at the first slide, clicking "previous" will loop them to the last slide.

6.  **Next Slide Functionality (`Carousel.jsx`):**
    * The `nextSlide` function updates the `currentPerson` state by adding 1 to the current index.
    * The `% people.length` ensures that when the user is at the last slide, clicking "next" will loop them back to the first slide.

7.  **Manual Navigation Buttons (`Carousel.jsx`):**
    * Two buttons, "prev" and "next", are rendered with `FiChevronLeft` and `FiChevronRight` icons respectively.
    * Their `onClick` handlers are connected to the `prevSlide` and `nextSlide` functions, allowing users to manually navigate the slider.

8.  **Automatic Sliding (`Carousel.jsx`):**
    * The `useEffect` hook is used to implement the automatic sliding functionality.
    * `setInterval` is called when the component mounts (and re-renders if `currentPerson` changes). It calls the `nextSlide` function every 5000 milliseconds (5 seconds).
    * The `return` function within `useEffect` is a cleanup function. It calls `clearInterval` to stop the automatic sliding when the component unmounts or before the effect runs again due to a change in `currentPerson`.

9.  **App Component (`App.jsx`):**
    * The `App` component simply imports and renders the `Carousel` component within its `main` section.

## Customization

* **Data:** Modify the `longList` array in `data.js` to include your own images, names, titles, and quotes.
* **Styling:** Customize the appearance of the slider by modifying the CSS rules.
* **Automatic Slide Interval:** Change the `5000` value in the `useEffect` hook in `Carousel.jsx` to adjust the automatic slide interval (in milliseconds).
* **Transition Speed:** Modify the `transition` property in the `.slide` CSS rule to change the speed of the slide animation.

## Contributing

If you'd like to contribute to this project, feel free to open issues or submit pull requests.

## License

[Your License Information Here (e.g., MIT License)]
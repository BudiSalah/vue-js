<template>
  <footer class="footer section">
    <div class="container">
      <h2 class="footer__headline text-rtl">Explore More</h2>

      <hr class="hr hr--gray" />

      <div class="footer__row row">
        <!-- vertical menu goes here! -->
        <VerticalMenu menuTitle="Quick Links" :menuItems="quickMenu" />
        <VerticalMenu menuTitle="Our Hospitals" :menuItems="hospitalsMenu" />

        <div class="footer__item footer__newsletter col-12 col-lg-6 text-rtl">
          <div class="footer__title">New Letter</div>
          <form class="form">
            <div class="form-group form__group direction-rtl">
              <input
                type="email"
                class="form-control form__input"
                aria-describedby="emailHelp"
              />
              <button type="submit" class="btn btn--form">Subscribe Now</button>
            </div>
          </form>

          <h5 class="footer__copyrights">
            Copyright © <span class="footer__num">2018</span> - ANDALUSIA GROUP
          </h5>

          <div class="social social--footer">
            <div class="social__item social__item--footer">
              <a href="#" class="social__icon social_icon--facebook">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  id="Bold"
                  enable-background="new 0 0 24 24"
                  height="512"
                  viewBox="0 0 24 24"
                  width="512"
                >
                  <path
                    d="m15.997 3.985h2.191v-3.816c-.378-.052-1.678-.169-3.192-.169-3.159 0-5.323 1.987-5.323 5.639v3.361h-3.486v4.266h3.486v10.734h4.274v-10.733h3.345l.531-4.266h-3.877v-2.939c.001-1.233.333-2.077 2.051-2.077z"
                  />
                </svg>
              </a>
            </div>
            <div class="social__item social__item--footer">
              <a href="#" class="social__icon social_icon--twitter">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink"
                  version="1.1"
                  id="Capa_1"
                  x="0px"
                  y="0px"
                  viewBox="0 0 512 512"
                  style="enable-background: new 0 0 512 512"
                  xml:space="preserve"
                >
                  <path
                    d="M512,97.248c-19.04,8.352-39.328,13.888-60.48,16.576c21.76-12.992,38.368-33.408,46.176-58.016  c-20.288,12.096-42.688,20.64-66.56,25.408C411.872,60.704,384.416,48,354.464,48c-58.112,0-104.896,47.168-104.896,104.992  c0,8.32,0.704,16.32,2.432,23.936c-87.264-4.256-164.48-46.08-216.352-109.792c-9.056,15.712-14.368,33.696-14.368,53.056  c0,36.352,18.72,68.576,46.624,87.232c-16.864-0.32-33.408-5.216-47.424-12.928c0,0.32,0,0.736,0,1.152  c0,51.008,36.384,93.376,84.096,103.136c-8.544,2.336-17.856,3.456-27.52,3.456c-6.72,0-13.504-0.384-19.872-1.792  c13.6,41.568,52.192,72.128,98.08,73.12c-35.712,27.936-81.056,44.768-130.144,44.768c-8.608,0-16.864-0.384-25.12-1.44  C46.496,446.88,101.6,464,161.024,464c193.152,0,298.752-160,298.752-298.688c0-4.64-0.16-9.12-0.384-13.568  C480.224,136.96,497.728,118.496,512,97.248z"
                  />
                </svg>
              </a>
            </div>
            <div class="social__item social__item--footer">
              <a href="#" class="social__icon social_icon--linkedin">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  height="512pt"
                  viewBox="0 0 512 512"
                  width="512pt"
                >
                  <path
                    d="m475.074219 0h-438.148438c-20.394531 0-36.925781 16.53125-36.925781 36.925781v438.148438c0 20.394531 16.53125 36.925781 36.925781 36.925781h438.148438c20.394531 0 36.925781-16.53125 36.925781-36.925781v-438.148438c0-20.394531-16.53125-36.925781-36.925781-36.925781zm-293.464844 387h-62.347656v-187.574219h62.347656zm-31.171875-213.1875h-.40625c-20.921875 0-34.453125-14.402344-34.453125-32.402344 0-18.40625 13.945313-32.410156 35.273437-32.410156 21.328126 0 34.453126 14.003906 34.859376 32.410156 0 18-13.53125 32.402344-35.273438 32.402344zm255.984375 213.1875h-62.339844v-100.347656c0-25.21875-9.027343-42.417969-31.585937-42.417969-17.222656 0-27.480469 11.601563-31.988282 22.800781-1.648437 4.007813-2.050781 9.609375-2.050781 15.214844v104.75h-62.34375s.816407-169.976562 0-187.574219h62.34375v26.558594c8.285157-12.78125 23.109375-30.960937 56.1875-30.960937 41.019531 0 71.777344 26.808593 71.777344 84.421874zm0 0"
                  />
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import VerticalMenu from "./unites/VerticalMenu";

export default {
  name: "Footer",
  components: {
    VerticalMenu,
  },
  data: () => {
    return {
      quickMenu: [
        {
          id: 1,
          name: "home",
          url: "/",
        },
        {
          id: 2,
          name: "about us",
          url: "/about",
        },
        {
          id: 3,
          name: "careers",
          url: "/careers",
        },
        {
          id: 4,
          name: "events",
          url: "/media-events",
        },
        {
          id: 5,
          name: "news",
          url: "/news",
        },
        {
          id: 6,
          name: "contact",
          url: "/contact",
        },
      ],
      hospitalsMenu: [
          {
          id: 1,
          name: "al shalalatat",
          url: "",
        },
        {
          id: 2,
          name: "semouha",
          url: "",
        },
        {
          id: 3,
          name: "antoniades",
          url: "",
        },
        {
          id: 4,
          name: "maadi",
          url: "",
        },
        {
          id: 5,
          name: "hai el jamaaa",
          url: "",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
</style>
<template>
    <div class="container">
      <header>
        <h1>Personal Profile Web Page</h1>
      </header>
      <main>
        <section class="main-content">
          <div class="about">
            <h1>About Me</h1>
            <p>Hello, I'm <span class="highlight">Reanna Lofamia</span></p>
            <p>
              I am a Computer Science student specializing in Cyber Security and
              Forensics at Asia Pacific College.
            </p>
            <a href="https://www.linkedin.com/in/reannalofamia/" target="_blank">LinkedIn</a> |
            <a href="https://instagram.com/reignlofamia" target="_blank">Instagram</a>
          </div>
  
          <div class="education">
            <h1>Education and Achievements</h1>
            <h3>Asia Pacific College (2023 - Present)</h3>
            <ul>
              <li>Dean's Lister (2023-2024)</li>
            </ul>
            <h3>Immaculate Heart of Mary College (2021 - 2023)</h3>
            <ul>
              <li>Consistent Honor Student</li>
              <li>Participant in 15th DLSU Arts Congress</li>
              <li>STEM Society Social Media Manager (2022-2023)</li>
            </ul>
          </div>
  
          <div class="skills">
            <h1>Skills</h1>
            <ul>
              <li>Java</li>
              <li>Figma</li>
              <li>Python</li>
              <li>Adobe Photoshop</li>
            </ul>
          </div>
  
          <div class="hobbies">
            <h1>Hobbies and Interests</h1>
            <ul>
              <li>Gaming</li>
              <li>Graphic Design</li>
              <li>Painting</li>
            </ul>
          </div>
        </section>
  
        <h1>Vue Example</h1>
  
        <div id="app">
          {{ message }}
          <div v-bind:class="vueClass">This element is bound to the "pinkBG" class.</div>
        </div>
  
        <div id="app2">
          <div>
            <figure v-for="x in manyFoods" :key="x.name">
              <img :src="x.url" alt="">
              <figcaption>{{ x.name }}</figcaption>
            </figure>
          </div>
        </div>
  
        <div id="app3">
          <form @submit.prevent="addItem">
            <p>
              What do you need? <br />
              <input type="text" required placeholder="item name.." v-model="itemName" />
            </p>
            <p>
              How many? <br />
              <input type="number" placeholder="number of items.." v-model="itemNumber" />
            </p>
            <p>
              Important?
              <label>
                <input type="checkbox" v-model="itemImportant" />
                {{ itemImportant }}
              </label>
            </p>
            <button type="submit">Add item</button>
          </form>
          <br />
          <hr />
  
          <div>
            <p><strong>Shopping list:</strong></p>
            <ul id="ulToFind">
              <li
                v-for="item in shoppingList"
                :key="item.name"
                :class="{ impClass: item.important }"
                @click="item.found = !item.found"
                v-show="!item.found"
              >
                {{ item.name }}, {{ item.number }}
              </li>
            </ul>
            <ul id="ulFound">
              <li
                v-for="item in shoppingList"
                :key="item.name + '-found'"
                :class="{ impClass: item.important }"
                @click="item.found = !item.found"
                v-show="item.found"
              >
                {{ item.name }}, {{ item.number }}
              </li>
            </ul>
          </div>
        </div>
      </main>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        message: "Hello Vue!",
        vueClass: "pinkBG",
        manyFoods: [
          { name: "Pizza", url: "pizza.jpg" },
          { name: "Burger", url: "burger.jpg" },
        ],
        itemName: "",
        itemNumber: 1,
        itemImportant: false,
        shoppingList: [],
      };
    },
    methods: {
      addItem() {
        this.shoppingList.push({
          name: this.itemName,
          number: this.itemNumber,
          important: this.itemImportant,
          found: false,
        });
        this.itemName = "";
        this.itemNumber = 1;
        this.itemImportant = false;
      },
    },
  };
  </script>
  
  <style scoped>
  .container {
    font-family: Arial, sans-serif;
    color: #333;
  }
  
  .highlight {
    color: red;
  }
  
  .pinkBG {
    background-color: pink;
  }
  
  .impClass {
    font-weight: bold;
  }
  
  #ulToFind li {
    cursor: pointer;
  }
  
  #ulFound li {
    text-decoration: line-through;
    cursor: pointer;
  }
  </style>
  
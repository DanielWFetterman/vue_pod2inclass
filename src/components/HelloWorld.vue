<template>
  
  <div class="wrapper">

    <div class="card">

      <title>This card has a button and a image</title>
    
      <p>The image is a meme and says "I know HTML How to meet ladies"</p>
    
      <img id="HTML img" src="https://images.fineartamerica.com/images/artworkimages/mediumlarge/3/i-know-html-how-to-meet-ladies-funny-web-designer-print-noirty-designs.jpg" alt="HTML is fun"/>

      <a href="http://hax.psu.edu" target="http://hax.psu.edu">
        <button class="button"> Details </button> 
      </a>  

    </div>

      <button class="dup-btn"> Duplicate </button>
      <button class="change-name-btn"> Change Name </button>
      <button class="change-color-btn"> Change Color </button>
      <button class="del-btn"> Delete </button>

  </div>
        
  <!-- <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <div class="card">
    <img alt="real estate logo" src="./housepic.jpg">
    <div class="card-content"> 
      <h2>Two Pod Realty</h2> 
      <p id="description">Real Estate Company Focused on delivering the best properties in the State College Area</p> 
      <button class="details-button" id="detailsBtn">Details</button>
    </div> 
  </div> 
  
  <button id="btn">Duplicator</button>
  <button id="colorBtn">BGColorChanger</button>
  <button id="Headingbtn">HeadingChanger</button>
  <button id="dltbtn">DeleteCard</button> -->
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted() {
    document.querySelector('#btn').addEventListener('click', () => {
      const clone = document.querySelector('.card').cloneNode(true); // Clone the whole card
      document.body.appendChild(clone);
    });
    
    var numbers = ["1", "2", "3", "4", "5", "6", "7", "8", "9"];
    var letters = ["A", "B", "C", "D", "E", "F"];
    
    function randomColor() {
      var color = "";
      for (var i = 0; i < 3; i++) {
        var index = Math.floor(Math.random() * (numbers.length + letters.length));
        color += (index < numbers.length) ? numbers[index] : letters[index - numbers.length];
      }
      return color;
    }
    
    document.querySelector('#colorBtn').addEventListener('click', () => {
      const card = document.querySelector('.card');
      // Change background color
      card.style.backgroundColor = '#' + randomColor();
    });
    
    // HEADING CHANGER
    document.querySelector('#Headingbtn').addEventListener('click', () => {
      const title = document.querySelector('h2');
      title.innerText = "Super Pod 2 Realty";
    });
    
    // Card delete
    document.querySelector('#dltbtn').addEventListener('click', () => {
      const cards = document.querySelectorAll('.card');
      // Check if there are cards to delete
      if (cards.length > 1) {
        const lastCard = cards[cards.length - 1];
        lastCard.parentNode.removeChild(lastCard);
      }
    });
    
    var original = document.querySelector('#description').innerText;
    
    document.querySelector('#detailsBtn').addEventListener('click', () => {
      const description = document.querySelector('#description');
      // Toggle the visibility of the description
      if (description.innerText === 'none' || description.innerText === '') {
        description.innerText = original; // Show the description
      } else {
        description.innerText = ''; // Hide the description
      }
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.card {
  max-width: 400px;
  margin: 0 auto;
  border: 1px solid #0C0B0B;
  background-color: #0C0B0B;
  padding: 16px;
  display: flex;
  flex-direction: column;
  text-align: center;
}

.card img {
  max-width: 100%;
  height: auto;
}

.card-content {
  flex: 1;
}

/* Style for the Title label */
h2 {
  font-size: 24px;
  margin: -10px 0;
  /* Background color and border */
  background-color: #F8471B;
  /* Background color */
  color: #fff;
  /* Text color on the background */
  padding: 8px 16px;
  border-radius: 4px;
}

p {
  font-size: 16px;
  margin: 8px 0;
  color: #fff;
}

a.details-button {
  background-color: #EA5F0A;
  color: #fff;
  padding: 8px 16px;
  text-decoration: none;
  border-radius: 4px;
}
</style>

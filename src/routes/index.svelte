<script>
     import axios from 'axios';
     import { Circle3 } from 'svelte-loading-spinners'
     let url = '';
     let shorturl = "https://trim-url.vercel.app/";
     let start = false;
     let loading = false;
     async function sendReq() {
          loading = true;
          const response = await axios.post("https://url-shortener-manitej66.azurewebsites.net/api/shorten?code=USDsXCIeE0UKKJTi9pMWHTyQOFWIu2zAOmWmzcAW7PorrkqDeOcnHQ==",{"url":url});
          shorturl = shorturl + response.data.shortUrl;
          start = true;
          loading = false;
     }
</script>


<div class = "navbar">
     <h1>URL shortner</h1>
</div>
<div class = "container">
     <div class = imagediv>
          <!-- svelte-ignore a11y-img-redundant-alt -->
          <img src = ".\src\images.jpg" alt="image">
     </div>
     <div class = box>
          <input bind:value ={url} placeholder = "enter url">
          <button on:click="{sendReq}">Shorten</button>
          {#if loading}
          <div class = "load"><Circle3 size="50" color="#FF3E00" unit="px" duration="1s" ></Circle3></div>
          {/if} 
          {#if start == true}
               <h4>Click Here 👇</h4> 
               <a href = "{url}">{shorturl}</a>
          {/if}
     </div>
</div>
<style>
     @import url('https://fonts.googleapis.com/css2?family=Lato&display=swap');
     .navbar {
          background-color: #384259;
          text-align: center;
          color: white;
          margin: -8px;
          padding: 2px;
          font-family: 'Lato', sans-serif;
     }
     img {
          width: 500px;
          height: 560px;
     }
     .container {
          display: flex;
          justify-content: space-around;
          flex-direction: row;
     }
     .imagediv {
          width: 40%;
          margin-top: 20px;
          text-align: center;
     }
     .box {
          width: 50%;
          display: flex;
          flex-direction: column;
          align-items: center;
          padding: 10px;
          margin-top: 150px;
     }
     input {
          width: 60%;
          padding: 7px;
          text-align: center;
          border-bottom-right-radius: 15px;
          border-top-left-radius: 15px;
          outline: none;
          border: 3px solid #f73859;
          color: #384259;
          font-weight: bold;
          font-family: 'Lato', sans-serif;
     }
     button {
          width: 25%;
          padding: 10px;
          text-align: center;
          border-radius: 100px;
          outline: none;
          border: none;
          background-color: #f73859;
          color: white;
          margin-top: 25px;
          cursor: pointer;
          font-weight: bold;
          font-family: 'Lato', sans-serif;
     }
     h4 {
          text-align: center;
          margin-top: 100px;
          font-family: 'Lato', sans-serif;
     }
     a {
          text-align: center;
          text-decoration: none;
          margin-top: 5px;
          color: #521262;
          font-weight: bold;
          font-size: 25px;
          font-family: 'Lato', sans-serif;
     }
     .load {
          margin-top: 120px;
     }
     @media (max-width: 375px) and (min-width: 320px) {
          .navbar {
               padding: 2px;
               font-size: 10px;
               margin-top: -10px;
          }
          .container {
               display: flex;
               justify-content: space-around;
               flex-direction: column;
               align-items: center;
          }
          .imagediv {
               width: 90%;
          }
     
          img {
               width: 250px;
               height: 200px;
          }

          .box {
               width: 92%; 
               margin: 0px;
          }

          input {
               width: 90%;
               padding: 7px;
          }

          button {
               width: 40%;
               padding: 7px;
               margin-top: 10px;
               text-align: center;
          }
          .load {
               margin-top: 30px;
          }
          h4 {
               margin-top: 30px;
          }
          a {
               margin-top: 0px;
               font-size: 15px;
          }

     }
     @media (max-width: 600px) and (min-width: 425px) {
          .navbar {
               padding: 2px;
               font-size: 10px;
               margin-top: -10px;
          }
          .container {
               display: flex;
               justify-content: space-around;
               flex-direction: column;
               align-items: center;
          }
          .imagediv {
               width: 90%;
          }
     
          img {
               width: 300px;
               height: 250px;
          }

          .box {
               width: 92%; 
               margin: 0px;
          }

          input {
               width: 95%;
               padding: 7px;
          }

          button {
               width: 40%;
               padding: 7px;
               margin-top: 10px;
               text-align: center;
          }
          .load {
               margin-top: 30px;
          }
          h4 {
               margin-top: 25px;
          }
          a {
               margin-top: 0px;
               font-size: 15px;
          }


     }
     @media (max-width: 900px) and (min-width: 768px) {
          .navbar {
               padding: 5px;
               font-size: 15px;
               margin-top: -10px;
          }
          img {
               width: 350px;
               height: 400px;
               margin-top: 70px;
          }
          
          input {
               width: 85%;
               padding: 7px;
          }
          button {
               width: 30%;
               padding: 7px;
               margin-top: 20px; 
          }
          .load {
               margin-top: 70px;
          }
          h4 {
               margin-top: 65px;
          }
          a {
               margin-top: 0px;
               font-size: 15px;
          }



     }

</style>
<!-- src/routes/about.svelte -->
<svelte:head>
   <title>About</title>
</svelte:head>

<div class="main_container">
   <section>
       <div class="inner-container">
         <div class="about-subtitle">
            <p>
                Visual Intuition Trainer is a simple game that helps you to see better. Guess a height and width between 0 and 5 inches and receive a score normalized to 100. In practice, the floor is ~75 and the maximum score is 200 - Keep playing until your scores consistently get better.
            </p>
            <br>
            <p>
                Ping on Twitter if anything doesn't work: <a href="https://twitter.com/bertgodel" target="_blank">@bertgodel</a>
            </p>
         </div>
       </div>
     </section>
</div>

<style>
   .main_container {
       margin: 0 80px 0 65px;
   }

   .about-subtitle {
       margin-top: -2rem;
   }

   .about-subtitle >p {
       width: 60%;
       font-weight: normal;
       font-size: 1rem;
       line-height: 2rem;
   }
</style>
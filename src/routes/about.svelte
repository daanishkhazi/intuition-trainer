<!-- src/routes/about.svelte -->
<svelte:head>
   <title>About</title>
</svelte:head>

<div class="main_container">
   <section>
       <div class="inner-container">
         <div class="about-subtitle">
            <p>
                Guess a height and width in inches – Between 0 and 5.
            </p>
            <br>
            <p>
               The scoring mechanism reflects how human's processes spatial information. We are good at judging relative proportions, we are less precise with absolute measurements. This game challenges that limitation, helping you improve your ability to estimate dimensions accurately. By practicing, you engage your brain's visual processing system, training it to make finer distinctions in size and proportion—skills that improve with consistent use.

               The score is based on how close your guesses are to the actual width and height of the square. For each dimension, the error is calculated as a percentage of the actual size. The average of these percentage errors gives the mean error. An exponential decay function then converts the mean error into a score out of 100, with perfect guesses earning 100. The decay function penalizes larger errors proportionally, halving the score for approximately every 50% increase in mean error.
               
               This system ties naturally to how we perceive and refine visual accuracy.
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

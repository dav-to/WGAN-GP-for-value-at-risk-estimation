# Value at Risk Estimation with WGAN-GP

This is repository contains code to estimate Value at risk for a financial portfolio using a generative adverserail network of the WGAN-GP type.
The code is based on some of the code that I used in my master's thesis on the subject [1].

WGAN-GP is used to simulate returns for a financial portfoilio, the 95% VaR can then be estimated as the 5th percentile times -1 (as VaR is in terms of loss).
To get a updated VaR estimate that reflects the current market condition a pretrained model is updated by training the model for a number of additional epochs on recent data.

## Files

**vargan_model.ipynb** - This file creates the WGAN-GP model and gives a pretrained model.  
Here the modification of keras.model and overriding the Model.train_step is based on example code by A_K_Nain [2].  
**backtesting.ipynb** - This file updates the pretrained model to get new estimates for a backtesting period. For each update of the model the model is updated using recent historical data prior to the day the VaR is estimated for.

## References

[1] D. Tobjörk, "Value at risk estimation with generative adversarial networks", M.S. thesis, Dept. of Statistics, Lund Univ., Lund, 2021. Accesed on: December 12, 2021. [Online].
Available: https://lup.lub.lu.se/student-papers/search/publication/9042741 

[2] A.K. Nain, <em>WGAN-GP overriding Model.train_step</em>, May 9, 2020. Accesed on: December 12, 2021. [Online].
Available: https://keras.io/examples/generative/wgan_gp/

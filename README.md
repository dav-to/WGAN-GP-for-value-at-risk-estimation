# Value at Risk Estimation with WGAN-GP

This repository contains code to estimate Value at risk for a financial portfolio using a generative adversarial network [1] of the WGAN-GP type [2].
The code is based on some of the code that I used in my master's thesis on the subject [3].

WGAN-GP is used to simulate returns for a financial portfolio, the 95% VaR can then be estimated as the 5th percentile times -1 (as VaR is in terms of loss).
To get an updated VaR estimate that reflect current market conditions a pretrained model is updated by training the model for a number of additional epochs on recent data.

For comparison 95% VaR is also estimated for the backtesting period using the classical variance-covariance method. 

## Files

**vargan_model.ipynb** - This file creates the WGAN-GP model and gives a pretrained model.  
Some code here is based on example code by A_K_Nain [4], such as the modification of keras.model and overriding the Model.train_step.  
**backtesting.ipynb** - This file updates the pretrained model to get new estimates for a backtesting period. For each update of the model the model is updated using recent historical data prior to the day the VaR is estimated for.

## References
[1] I. Goodfellow et al., “Generative adversarial nets”, in Advances in Neural Information Processing Systems, 2014, vol 27.
Accesed on: December 13, 2021. [Online]. Available: https://papers.nips.cc/paper/2014/hash/5ca3e9b122f61f8f06494c97b1afccf3-Abstract.html

[2] I. Gulrajani, F. Ahmed, M. Arjovsky, V. Dumoulin, en A. C. Courville, “Improved training of wasserstein GANs”, in Advances in Neural Information Processing Systems, 2017, vol 30.
Accesed on: December 13, 2021. [Online]. Available: https://papers.nips.cc/paper/2017/hash/892c3b1c6dccd52936e27cbd0ff683d6-Abstract.html

[3] D. Tobjörk, "Value at risk estimation with generative adversarial networks", M.S. thesis, Dept. of Statistics, Lund Univ., Lund, 2021. Accesed on: December 12, 2021. [Online].
Available: https://lup.lub.lu.se/student-papers/search/publication/9042741 

[4] A.K. Nain, <em>WGAN-GP overriding Model.train_step</em>, May 9, 2020. Accesed on: December 12, 2021. [Online].
Available: https://keras.io/examples/generative/wgan_gp/

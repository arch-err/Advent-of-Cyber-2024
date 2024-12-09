# Day_5
*An XXE challenge, but it quickly evolved into an exercise for me to learn [caido](https://docs.caido.io/) better =)*


## Questions
1. ***What is the flag discovered after navigating through the wishes?***
- **Answer:** `THM{Brut3f0rc1n6_mY_w4y}`

> ### Solution
> 1. Start off by following the guide by THM
> 2. Open the site and proxy through caido
> 3. Intercept → Send to replay
> 4. Mess around a bit → realize I've gotta bruteforce this → Send to Automate
> 5. Follow [this guide](https://docs.caido.io/guides/automate.html) to automate the XXE-attack.
> 6. Step through the responses and get the flag


2. ***What is the flag seen on the possible proof of sabotage?***
- **Answer:** `THM{m4y0r_m4lw4r3_b4ckd00rs}`

> ### Solution
> 1. Literally just follow the guide by THM, look at the changelog at `/CHANGELOG`...

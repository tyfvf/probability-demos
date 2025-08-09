# What is the Birthday Problem?

The Birthday Problem is a famous problem in probability theory that asks
how likely it is that in a group of people, at least two will share the
same birthday. The problem is counterintuitive because it suggests that
a relatively small group of people can have a high probability of
sharing a birthday.

### The question is: How many people do you need in a room for there to be a better than even chance that at least two people share a birthday?

``` r
tries <- 10000
verbose <- FALSE
```

``` r
# Simulate with 2 people only
same_birthday <- 0
people <- 2

for (i in 1:tries) {

  people_vector <- c()

  for (j in 1:people) {

    birthday <- sample(1:365, 1)
    people_vector <- c(people_vector, birthday)

    if (verbose) {
      cat("Try", i, ":", j, "person's birthday is", birthday, "\n")
    }

  }

  if (length(unique(people_vector)) < length(people_vector)) {
    same_birthday <- same_birthday + 1
  }

}

cat("Days with same birthday:", same_birthday, "out of", tries, "\n")
```

    ## Days with same birthday: 27 out of 10000

``` r
cat("Probability of two people sharing a birthday",
    same_birthday / tries,
    "(", (same_birthday / tries) * 100, "% chance)\n")
```

    ## Probability of two people sharing a birthday 0.0027 ( 0.27 % chance)

``` r
cat("Probability of two people not sharing a birthday",
    1 - (same_birthday / tries),
    "(", (1 - (same_birthday / tries)) * 100, "% chance)\n")
```

    ## Probability of two people not sharing a birthday 0.9973 ( 99.73 % chance)

``` r
# Simulate from 2 to 30 people
for (i in 2:30) {

  same_birthday <- 0

  for (j in 1:tries) {

    people_vector <- c()

    for (k in 1:i) {

      birthday <- sample(1:365, 1)
      people_vector <- c(people_vector, birthday)

      if (verbose) {
        cat("Try", j, ":", k, "person's birthday is", birthday, "\n")
      }

    }

    if (length(unique(people_vector)) < length(people_vector)) {
      same_birthday <- same_birthday + 1
    }
  }

  cat("Days with same birthday for", i, "people:",
      same_birthday, "out of", tries, "\n")

  cat("Probability of in", i, "people someone sharing a birthday",
      same_birthday / tries,
      "(", (same_birthday / tries) * 100, "% chance)\n")

  cat("Probability of in", i, "people no one sharing a birthday",
      1 - (same_birthday / tries),
      "(", (1 - (same_birthday / tries)) * 100, "% chance)\n")

  cat("----------------------------------------------------------------\n")
}
```

    ## Days with same birthday for 2 people: 27 out of 10000 
    ## Probability of in 2 people someone sharing a birthday 0.0027 ( 0.27 % chance)
    ## Probability of in 2 people no one sharing a birthday 0.9973 ( 99.73 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 3 people: 85 out of 10000 
    ## Probability of in 3 people someone sharing a birthday 0.0085 ( 0.85 % chance)
    ## Probability of in 3 people no one sharing a birthday 0.9915 ( 99.15 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 4 people: 178 out of 10000 
    ## Probability of in 4 people someone sharing a birthday 0.0178 ( 1.78 % chance)
    ## Probability of in 4 people no one sharing a birthday 0.9822 ( 98.22 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 5 people: 281 out of 10000 
    ## Probability of in 5 people someone sharing a birthday 0.0281 ( 2.81 % chance)
    ## Probability of in 5 people no one sharing a birthday 0.9719 ( 97.19 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 6 people: 419 out of 10000 
    ## Probability of in 6 people someone sharing a birthday 0.0419 ( 4.19 % chance)
    ## Probability of in 6 people no one sharing a birthday 0.9581 ( 95.81 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 7 people: 575 out of 10000 
    ## Probability of in 7 people someone sharing a birthday 0.0575 ( 5.75 % chance)
    ## Probability of in 7 people no one sharing a birthday 0.9425 ( 94.25 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 8 people: 743 out of 10000 
    ## Probability of in 8 people someone sharing a birthday 0.0743 ( 7.43 % chance)
    ## Probability of in 8 people no one sharing a birthday 0.9257 ( 92.57 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 9 people: 885 out of 10000 
    ## Probability of in 9 people someone sharing a birthday 0.0885 ( 8.85 % chance)
    ## Probability of in 9 people no one sharing a birthday 0.9115 ( 91.15 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 10 people: 1205 out of 10000 
    ## Probability of in 10 people someone sharing a birthday 0.1205 ( 12.05 % chance)
    ## Probability of in 10 people no one sharing a birthday 0.8795 ( 87.95 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 11 people: 1432 out of 10000 
    ## Probability of in 11 people someone sharing a birthday 0.1432 ( 14.32 % chance)
    ## Probability of in 11 people no one sharing a birthday 0.8568 ( 85.68 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 12 people: 1651 out of 10000 
    ## Probability of in 12 people someone sharing a birthday 0.1651 ( 16.51 % chance)
    ## Probability of in 12 people no one sharing a birthday 0.8349 ( 83.49 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 13 people: 1895 out of 10000 
    ## Probability of in 13 people someone sharing a birthday 0.1895 ( 18.95 % chance)
    ## Probability of in 13 people no one sharing a birthday 0.8105 ( 81.05 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 14 people: 2236 out of 10000 
    ## Probability of in 14 people someone sharing a birthday 0.2236 ( 22.36 % chance)
    ## Probability of in 14 people no one sharing a birthday 0.7764 ( 77.64 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 15 people: 2511 out of 10000 
    ## Probability of in 15 people someone sharing a birthday 0.2511 ( 25.11 % chance)
    ## Probability of in 15 people no one sharing a birthday 0.7489 ( 74.89 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 16 people: 2823 out of 10000 
    ## Probability of in 16 people someone sharing a birthday 0.2823 ( 28.23 % chance)
    ## Probability of in 16 people no one sharing a birthday 0.7177 ( 71.77 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 17 people: 3179 out of 10000 
    ## Probability of in 17 people someone sharing a birthday 0.3179 ( 31.79 % chance)
    ## Probability of in 17 people no one sharing a birthday 0.6821 ( 68.21 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 18 people: 3454 out of 10000 
    ## Probability of in 18 people someone sharing a birthday 0.3454 ( 34.54 % chance)
    ## Probability of in 18 people no one sharing a birthday 0.6546 ( 65.46 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 19 people: 3793 out of 10000 
    ## Probability of in 19 people someone sharing a birthday 0.3793 ( 37.93 % chance)
    ## Probability of in 19 people no one sharing a birthday 0.6207 ( 62.07 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 20 people: 4139 out of 10000 
    ## Probability of in 20 people someone sharing a birthday 0.4139 ( 41.39 % chance)
    ## Probability of in 20 people no one sharing a birthday 0.5861 ( 58.61 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 21 people: 4434 out of 10000 
    ## Probability of in 21 people someone sharing a birthday 0.4434 ( 44.34 % chance)
    ## Probability of in 21 people no one sharing a birthday 0.5566 ( 55.66 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 22 people: 4735 out of 10000 
    ## Probability of in 22 people someone sharing a birthday 0.4735 ( 47.35 % chance)
    ## Probability of in 22 people no one sharing a birthday 0.5265 ( 52.65 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 23 people: 5147 out of 10000 
    ## Probability of in 23 people someone sharing a birthday 0.5147 ( 51.47 % chance)
    ## Probability of in 23 people no one sharing a birthday 0.4853 ( 48.53 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 24 people: 5347 out of 10000 
    ## Probability of in 24 people someone sharing a birthday 0.5347 ( 53.47 % chance)
    ## Probability of in 24 people no one sharing a birthday 0.4653 ( 46.53 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 25 people: 5664 out of 10000 
    ## Probability of in 25 people someone sharing a birthday 0.5664 ( 56.64 % chance)
    ## Probability of in 25 people no one sharing a birthday 0.4336 ( 43.36 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 26 people: 5958 out of 10000 
    ## Probability of in 26 people someone sharing a birthday 0.5958 ( 59.58 % chance)
    ## Probability of in 26 people no one sharing a birthday 0.4042 ( 40.42 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 27 people: 6257 out of 10000 
    ## Probability of in 27 people someone sharing a birthday 0.6257 ( 62.57 % chance)
    ## Probability of in 27 people no one sharing a birthday 0.3743 ( 37.43 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 28 people: 6512 out of 10000 
    ## Probability of in 28 people someone sharing a birthday 0.6512 ( 65.12 % chance)
    ## Probability of in 28 people no one sharing a birthday 0.3488 ( 34.88 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 29 people: 6810 out of 10000 
    ## Probability of in 29 people someone sharing a birthday 0.681 ( 68.1 % chance)
    ## Probability of in 29 people no one sharing a birthday 0.319 ( 31.9 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 30 people: 7063 out of 10000 
    ## Probability of in 30 people someone sharing a birthday 0.7063 ( 70.63 % chance)
    ## Probability of in 30 people no one sharing a birthday 0.2937 ( 29.37 % chance)
    ## ----------------------------------------------------------------

# Conclusion

The simulation shows that as the number of people in a group increases,
the probability of at least two people sharing a birthday also increases
significantly. In fact, with just 23 people, there is over a 50% chance
that at least two people share a birthday. This counterintuitive result
highlights the surpring nature of probability and how out intuition can
often lead us astray.

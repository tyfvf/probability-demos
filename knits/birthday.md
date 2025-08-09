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

    ## Days with same birthday: 31 out of 10000

``` r
cat("Probability of two people sharing a birthday:",
    same_birthday / tries,
    "(", (same_birthday / tries) * 100, "% chance)\n")
```

    ## Probability of two people sharing a birthday: 0.0031 ( 0.31 % chance)

``` r
cat("Probability of two people not sharing a birthday:",
    1 - (same_birthday / tries),
    "(", (1 - (same_birthday / tries)) * 100, "% chance)\n")
```

    ## Probability of two people not sharing a birthday: 0.9969 ( 99.69 % chance)

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

  cat("Probability of in", i, "people someone sharing a birthday:",
      same_birthday / tries,
      "(", (same_birthday / tries) * 100, "% chance)\n")

  cat("Probability of in", i, "people no one sharing a birthday:",
      1 - (same_birthday / tries),
      "(", (1 - (same_birthday / tries)) * 100, "% chance)\n")

  cat("----------------------------------------------------------------\n")
}
```

    ## Days with same birthday for 2 people: 30 out of 10000 
    ## Probability of in 2 people someone sharing a birthday: 0.003 ( 0.3 % chance)
    ## Probability of in 2 people no one sharing a birthday: 0.997 ( 99.7 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 3 people: 69 out of 10000 
    ## Probability of in 3 people someone sharing a birthday: 0.0069 ( 0.69 % chance)
    ## Probability of in 3 people no one sharing a birthday: 0.9931 ( 99.31 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 4 people: 164 out of 10000 
    ## Probability of in 4 people someone sharing a birthday: 0.0164 ( 1.64 % chance)
    ## Probability of in 4 people no one sharing a birthday: 0.9836 ( 98.36 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 5 people: 269 out of 10000 
    ## Probability of in 5 people someone sharing a birthday: 0.0269 ( 2.69 % chance)
    ## Probability of in 5 people no one sharing a birthday: 0.9731 ( 97.31 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 6 people: 418 out of 10000 
    ## Probability of in 6 people someone sharing a birthday: 0.0418 ( 4.18 % chance)
    ## Probability of in 6 people no one sharing a birthday: 0.9582 ( 95.82 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 7 people: 569 out of 10000 
    ## Probability of in 7 people someone sharing a birthday: 0.0569 ( 5.69 % chance)
    ## Probability of in 7 people no one sharing a birthday: 0.9431 ( 94.31 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 8 people: 744 out of 10000 
    ## Probability of in 8 people someone sharing a birthday: 0.0744 ( 7.44 % chance)
    ## Probability of in 8 people no one sharing a birthday: 0.9256 ( 92.56 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 9 people: 958 out of 10000 
    ## Probability of in 9 people someone sharing a birthday: 0.0958 ( 9.58 % chance)
    ## Probability of in 9 people no one sharing a birthday: 0.9042 ( 90.42 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 10 people: 1175 out of 10000 
    ## Probability of in 10 people someone sharing a birthday: 0.1175 ( 11.75 % chance)
    ## Probability of in 10 people no one sharing a birthday: 0.8825 ( 88.25 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 11 people: 1401 out of 10000 
    ## Probability of in 11 people someone sharing a birthday: 0.1401 ( 14.01 % chance)
    ## Probability of in 11 people no one sharing a birthday: 0.8599 ( 85.99 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 12 people: 1646 out of 10000 
    ## Probability of in 12 people someone sharing a birthday: 0.1646 ( 16.46 % chance)
    ## Probability of in 12 people no one sharing a birthday: 0.8354 ( 83.54 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 13 people: 1924 out of 10000 
    ## Probability of in 13 people someone sharing a birthday: 0.1924 ( 19.24 % chance)
    ## Probability of in 13 people no one sharing a birthday: 0.8076 ( 80.76 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 14 people: 2195 out of 10000 
    ## Probability of in 14 people someone sharing a birthday: 0.2195 ( 21.95 % chance)
    ## Probability of in 14 people no one sharing a birthday: 0.7805 ( 78.05 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 15 people: 2481 out of 10000 
    ## Probability of in 15 people someone sharing a birthday: 0.2481 ( 24.81 % chance)
    ## Probability of in 15 people no one sharing a birthday: 0.7519 ( 75.19 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 16 people: 2913 out of 10000 
    ## Probability of in 16 people someone sharing a birthday: 0.2913 ( 29.13 % chance)
    ## Probability of in 16 people no one sharing a birthday: 0.7087 ( 70.87 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 17 people: 3210 out of 10000 
    ## Probability of in 17 people someone sharing a birthday: 0.321 ( 32.1 % chance)
    ## Probability of in 17 people no one sharing a birthday: 0.679 ( 67.9 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 18 people: 3443 out of 10000 
    ## Probability of in 18 people someone sharing a birthday: 0.3443 ( 34.43 % chance)
    ## Probability of in 18 people no one sharing a birthday: 0.6557 ( 65.57 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 19 people: 3842 out of 10000 
    ## Probability of in 19 people someone sharing a birthday: 0.3842 ( 38.42 % chance)
    ## Probability of in 19 people no one sharing a birthday: 0.6158 ( 61.58 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 20 people: 4021 out of 10000 
    ## Probability of in 20 people someone sharing a birthday: 0.4021 ( 40.21 % chance)
    ## Probability of in 20 people no one sharing a birthday: 0.5979 ( 59.79 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 21 people: 4443 out of 10000 
    ## Probability of in 21 people someone sharing a birthday: 0.4443 ( 44.43 % chance)
    ## Probability of in 21 people no one sharing a birthday: 0.5557 ( 55.57 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 22 people: 4743 out of 10000 
    ## Probability of in 22 people someone sharing a birthday: 0.4743 ( 47.43 % chance)
    ## Probability of in 22 people no one sharing a birthday: 0.5257 ( 52.57 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 23 people: 4981 out of 10000 
    ## Probability of in 23 people someone sharing a birthday: 0.4981 ( 49.81 % chance)
    ## Probability of in 23 people no one sharing a birthday: 0.5019 ( 50.19 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 24 people: 5393 out of 10000 
    ## Probability of in 24 people someone sharing a birthday: 0.5393 ( 53.93 % chance)
    ## Probability of in 24 people no one sharing a birthday: 0.4607 ( 46.07 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 25 people: 5713 out of 10000 
    ## Probability of in 25 people someone sharing a birthday: 0.5713 ( 57.13 % chance)
    ## Probability of in 25 people no one sharing a birthday: 0.4287 ( 42.87 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 26 people: 5925 out of 10000 
    ## Probability of in 26 people someone sharing a birthday: 0.5925 ( 59.25 % chance)
    ## Probability of in 26 people no one sharing a birthday: 0.4075 ( 40.75 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 27 people: 6275 out of 10000 
    ## Probability of in 27 people someone sharing a birthday: 0.6275 ( 62.75 % chance)
    ## Probability of in 27 people no one sharing a birthday: 0.3725 ( 37.25 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 28 people: 6537 out of 10000 
    ## Probability of in 28 people someone sharing a birthday: 0.6537 ( 65.37 % chance)
    ## Probability of in 28 people no one sharing a birthday: 0.3463 ( 34.63 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 29 people: 6808 out of 10000 
    ## Probability of in 29 people someone sharing a birthday: 0.6808 ( 68.08 % chance)
    ## Probability of in 29 people no one sharing a birthday: 0.3192 ( 31.92 % chance)
    ## ----------------------------------------------------------------
    ## Days with same birthday for 30 people: 7088 out of 10000 
    ## Probability of in 30 people someone sharing a birthday: 0.7088 ( 70.88 % chance)
    ## Probability of in 30 people no one sharing a birthday: 0.2912 ( 29.12 % chance)
    ## ----------------------------------------------------------------

# Conclusion

The simulation shows that as the number of people in a group increases,
the probability of at least two people sharing a birthday also increases
significantly. In fact, with just 23 people, there is over a 50% chance
that at least two people share a birthday. This counterintuitive result
highlights the surpring nature of probability and how out intuition can
often lead us astray.

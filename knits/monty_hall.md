# What is the Monty Hall Problem?

The Monty Hall problem is a famous probability puzzle based on a game
show scenario. The problem is name after Monty Hall, the original host
of the American television game show Let’s Make a Deal. In the game, a
contestant is presented with three doors. Behind one door is a car (the
prize), and behind the other two doors are goats. The contestant picks
one door, then the host, who knows what is behind each door, opens
another door that has a goat behind it. The contestant is then given the
option to either stick with their original choice or switch to the other
unopened door.

### The question is: Is it better to switch or to stay with the original choice?

``` r
tries <- 1000
verbose <- TRUE
```

``` r
# First strategy: stay with the original choice
correct <- 0
for (i in 1:tries) {
  prize <- sample(1:3, 1) # Randomly place the car behind one of the doors
  choice <- sample(1:3, 1) # Contestant makes an initial choice

  if (verbose) {
    cat("Try", i,
        "- Prize is behind door", prize,
        ", contestant chose door", choice, "\n")
  }

  if (choice == prize) {
    correct <- correct + 1 # Contestant wins if they stay with their choice
  }
}
```

    ## Try 1 - Prize is behind door 2 , contestant chose door 3 
    ## Try 2 - Prize is behind door 3 , contestant chose door 2 
    ## Try 3 - Prize is behind door 3 , contestant chose door 3 
    ## Try 4 - Prize is behind door 2 , contestant chose door 3 
    ## Try 5 - Prize is behind door 3 , contestant chose door 3 
    ## Try 6 - Prize is behind door 2 , contestant chose door 1 
    ## Try 7 - Prize is behind door 3 , contestant chose door 3 
    ## Try 8 - Prize is behind door 2 , contestant chose door 2 
    ## Try 9 - Prize is behind door 2 , contestant chose door 3 
    ## Try 10 - Prize is behind door 3 , contestant chose door 3 
    ## Try 11 - Prize is behind door 3 , contestant chose door 3 
    ## Try 12 - Prize is behind door 1 , contestant chose door 1 
    ## Try 13 - Prize is behind door 2 , contestant chose door 1 
    ## Try 14 - Prize is behind door 3 , contestant chose door 3 
    ## Try 15 - Prize is behind door 1 , contestant chose door 2 
    ## Try 16 - Prize is behind door 2 , contestant chose door 2 
    ## Try 17 - Prize is behind door 2 , contestant chose door 3 
    ## Try 18 - Prize is behind door 3 , contestant chose door 2 
    ## Try 19 - Prize is behind door 1 , contestant chose door 3 
    ## Try 20 - Prize is behind door 3 , contestant chose door 1 
    ## Try 21 - Prize is behind door 3 , contestant chose door 3 
    ## Try 22 - Prize is behind door 1 , contestant chose door 3 
    ## Try 23 - Prize is behind door 1 , contestant chose door 3 
    ## Try 24 - Prize is behind door 3 , contestant chose door 1 
    ## Try 25 - Prize is behind door 1 , contestant chose door 2 
    ## Try 26 - Prize is behind door 2 , contestant chose door 3 
    ## Try 27 - Prize is behind door 1 , contestant chose door 3 
    ## Try 28 - Prize is behind door 1 , contestant chose door 2 
    ## Try 29 - Prize is behind door 3 , contestant chose door 1 
    ## Try 30 - Prize is behind door 2 , contestant chose door 2 
    ## Try 31 - Prize is behind door 1 , contestant chose door 2 
    ## Try 32 - Prize is behind door 1 , contestant chose door 2 
    ## Try 33 - Prize is behind door 1 , contestant chose door 2 
    ## Try 34 - Prize is behind door 3 , contestant chose door 3 
    ## Try 35 - Prize is behind door 2 , contestant chose door 2 
    ## Try 36 - Prize is behind door 2 , contestant chose door 1 
    ## Try 37 - Prize is behind door 1 , contestant chose door 1 
    ## Try 38 - Prize is behind door 3 , contestant chose door 3 
    ## Try 39 - Prize is behind door 2 , contestant chose door 2 
    ## Try 40 - Prize is behind door 1 , contestant chose door 2 
    ## Try 41 - Prize is behind door 1 , contestant chose door 3 
    ## Try 42 - Prize is behind door 3 , contestant chose door 2 
    ## Try 43 - Prize is behind door 1 , contestant chose door 2 
    ## Try 44 - Prize is behind door 2 , contestant chose door 1 
    ## Try 45 - Prize is behind door 1 , contestant chose door 1 
    ## Try 46 - Prize is behind door 1 , contestant chose door 1 
    ## Try 47 - Prize is behind door 2 , contestant chose door 1 
    ## Try 48 - Prize is behind door 1 , contestant chose door 1 
    ## Try 49 - Prize is behind door 3 , contestant chose door 1 
    ## Try 50 - Prize is behind door 2 , contestant chose door 1 
    ## Try 51 - Prize is behind door 2 , contestant chose door 2 
    ## Try 52 - Prize is behind door 3 , contestant chose door 1 
    ## Try 53 - Prize is behind door 1 , contestant chose door 1 
    ## Try 54 - Prize is behind door 3 , contestant chose door 2 
    ## Try 55 - Prize is behind door 1 , contestant chose door 1 
    ## Try 56 - Prize is behind door 1 , contestant chose door 1 
    ## Try 57 - Prize is behind door 3 , contestant chose door 1 
    ## Try 58 - Prize is behind door 1 , contestant chose door 2 
    ## Try 59 - Prize is behind door 1 , contestant chose door 2 
    ## Try 60 - Prize is behind door 1 , contestant chose door 3 
    ## Try 61 - Prize is behind door 1 , contestant chose door 1 
    ## Try 62 - Prize is behind door 3 , contestant chose door 2 
    ## Try 63 - Prize is behind door 3 , contestant chose door 2 
    ## Try 64 - Prize is behind door 3 , contestant chose door 3 
    ## Try 65 - Prize is behind door 2 , contestant chose door 3 
    ## Try 66 - Prize is behind door 2 , contestant chose door 1 
    ## Try 67 - Prize is behind door 3 , contestant chose door 3 
    ## Try 68 - Prize is behind door 3 , contestant chose door 2 
    ## Try 69 - Prize is behind door 3 , contestant chose door 2 
    ## Try 70 - Prize is behind door 2 , contestant chose door 1 
    ## Try 71 - Prize is behind door 2 , contestant chose door 2 
    ## Try 72 - Prize is behind door 1 , contestant chose door 3 
    ## Try 73 - Prize is behind door 1 , contestant chose door 2 
    ## Try 74 - Prize is behind door 3 , contestant chose door 3 
    ## Try 75 - Prize is behind door 2 , contestant chose door 1 
    ## Try 76 - Prize is behind door 3 , contestant chose door 2 
    ## Try 77 - Prize is behind door 1 , contestant chose door 2 
    ## Try 78 - Prize is behind door 3 , contestant chose door 2 
    ## Try 79 - Prize is behind door 2 , contestant chose door 3 
    ## Try 80 - Prize is behind door 3 , contestant chose door 1 
    ## Try 81 - Prize is behind door 2 , contestant chose door 3 
    ## Try 82 - Prize is behind door 3 , contestant chose door 1 
    ## Try 83 - Prize is behind door 2 , contestant chose door 2 
    ## Try 84 - Prize is behind door 3 , contestant chose door 3 
    ## Try 85 - Prize is behind door 3 , contestant chose door 3 
    ## Try 86 - Prize is behind door 2 , contestant chose door 3 
    ## Try 87 - Prize is behind door 1 , contestant chose door 3 
    ## Try 88 - Prize is behind door 1 , contestant chose door 3 
    ## Try 89 - Prize is behind door 2 , contestant chose door 1 
    ## Try 90 - Prize is behind door 3 , contestant chose door 1 
    ## Try 91 - Prize is behind door 2 , contestant chose door 1 
    ## Try 92 - Prize is behind door 2 , contestant chose door 1 
    ## Try 93 - Prize is behind door 2 , contestant chose door 1 
    ## Try 94 - Prize is behind door 2 , contestant chose door 3 
    ## Try 95 - Prize is behind door 2 , contestant chose door 1 
    ## Try 96 - Prize is behind door 1 , contestant chose door 3 
    ## Try 97 - Prize is behind door 3 , contestant chose door 1 
    ## Try 98 - Prize is behind door 2 , contestant chose door 2 
    ## Try 99 - Prize is behind door 3 , contestant chose door 3 
    ## Try 100 - Prize is behind door 1 , contestant chose door 2 
    ## Try 101 - Prize is behind door 1 , contestant chose door 1 
    ## Try 102 - Prize is behind door 2 , contestant chose door 1 
    ## Try 103 - Prize is behind door 2 , contestant chose door 1 
    ## Try 104 - Prize is behind door 1 , contestant chose door 2 
    ## Try 105 - Prize is behind door 3 , contestant chose door 1 
    ## Try 106 - Prize is behind door 2 , contestant chose door 2 
    ## Try 107 - Prize is behind door 3 , contestant chose door 1 
    ## Try 108 - Prize is behind door 3 , contestant chose door 1 
    ## Try 109 - Prize is behind door 3 , contestant chose door 2 
    ## Try 110 - Prize is behind door 3 , contestant chose door 3 
    ## Try 111 - Prize is behind door 2 , contestant chose door 1 
    ## Try 112 - Prize is behind door 2 , contestant chose door 2 
    ## Try 113 - Prize is behind door 3 , contestant chose door 2 
    ## Try 114 - Prize is behind door 2 , contestant chose door 3 
    ## Try 115 - Prize is behind door 3 , contestant chose door 2 
    ## Try 116 - Prize is behind door 3 , contestant chose door 2 
    ## Try 117 - Prize is behind door 1 , contestant chose door 2 
    ## Try 118 - Prize is behind door 2 , contestant chose door 3 
    ## Try 119 - Prize is behind door 3 , contestant chose door 2 
    ## Try 120 - Prize is behind door 2 , contestant chose door 3 
    ## Try 121 - Prize is behind door 3 , contestant chose door 2 
    ## Try 122 - Prize is behind door 2 , contestant chose door 1 
    ## Try 123 - Prize is behind door 3 , contestant chose door 1 
    ## Try 124 - Prize is behind door 2 , contestant chose door 2 
    ## Try 125 - Prize is behind door 3 , contestant chose door 1 
    ## Try 126 - Prize is behind door 2 , contestant chose door 3 
    ## Try 127 - Prize is behind door 1 , contestant chose door 2 
    ## Try 128 - Prize is behind door 3 , contestant chose door 2 
    ## Try 129 - Prize is behind door 1 , contestant chose door 2 
    ## Try 130 - Prize is behind door 1 , contestant chose door 2 
    ## Try 131 - Prize is behind door 1 , contestant chose door 1 
    ## Try 132 - Prize is behind door 3 , contestant chose door 2 
    ## Try 133 - Prize is behind door 3 , contestant chose door 1 
    ## Try 134 - Prize is behind door 1 , contestant chose door 3 
    ## Try 135 - Prize is behind door 3 , contestant chose door 2 
    ## Try 136 - Prize is behind door 2 , contestant chose door 2 
    ## Try 137 - Prize is behind door 1 , contestant chose door 3 
    ## Try 138 - Prize is behind door 3 , contestant chose door 3 
    ## Try 139 - Prize is behind door 2 , contestant chose door 2 
    ## Try 140 - Prize is behind door 1 , contestant chose door 1 
    ## Try 141 - Prize is behind door 3 , contestant chose door 2 
    ## Try 142 - Prize is behind door 1 , contestant chose door 2 
    ## Try 143 - Prize is behind door 2 , contestant chose door 2 
    ## Try 144 - Prize is behind door 3 , contestant chose door 1 
    ## Try 145 - Prize is behind door 1 , contestant chose door 1 
    ## Try 146 - Prize is behind door 2 , contestant chose door 1 
    ## Try 147 - Prize is behind door 2 , contestant chose door 2 
    ## Try 148 - Prize is behind door 3 , contestant chose door 1 
    ## Try 149 - Prize is behind door 2 , contestant chose door 1 
    ## Try 150 - Prize is behind door 3 , contestant chose door 2 
    ## Try 151 - Prize is behind door 1 , contestant chose door 3 
    ## Try 152 - Prize is behind door 3 , contestant chose door 3 
    ## Try 153 - Prize is behind door 2 , contestant chose door 2 
    ## Try 154 - Prize is behind door 1 , contestant chose door 3 
    ## Try 155 - Prize is behind door 3 , contestant chose door 3 
    ## Try 156 - Prize is behind door 1 , contestant chose door 1 
    ## Try 157 - Prize is behind door 3 , contestant chose door 2 
    ## Try 158 - Prize is behind door 1 , contestant chose door 2 
    ## Try 159 - Prize is behind door 1 , contestant chose door 2 
    ## Try 160 - Prize is behind door 3 , contestant chose door 3 
    ## Try 161 - Prize is behind door 1 , contestant chose door 2 
    ## Try 162 - Prize is behind door 3 , contestant chose door 2 
    ## Try 163 - Prize is behind door 2 , contestant chose door 1 
    ## Try 164 - Prize is behind door 3 , contestant chose door 1 
    ## Try 165 - Prize is behind door 3 , contestant chose door 1 
    ## Try 166 - Prize is behind door 1 , contestant chose door 1 
    ## Try 167 - Prize is behind door 2 , contestant chose door 2 
    ## Try 168 - Prize is behind door 3 , contestant chose door 3 
    ## Try 169 - Prize is behind door 2 , contestant chose door 3 
    ## Try 170 - Prize is behind door 2 , contestant chose door 3 
    ## Try 171 - Prize is behind door 3 , contestant chose door 2 
    ## Try 172 - Prize is behind door 1 , contestant chose door 1 
    ## Try 173 - Prize is behind door 3 , contestant chose door 2 
    ## Try 174 - Prize is behind door 3 , contestant chose door 3 
    ## Try 175 - Prize is behind door 1 , contestant chose door 1 
    ## Try 176 - Prize is behind door 3 , contestant chose door 1 
    ## Try 177 - Prize is behind door 3 , contestant chose door 3 
    ## Try 178 - Prize is behind door 1 , contestant chose door 1 
    ## Try 179 - Prize is behind door 2 , contestant chose door 1 
    ## Try 180 - Prize is behind door 2 , contestant chose door 2 
    ## Try 181 - Prize is behind door 2 , contestant chose door 2 
    ## Try 182 - Prize is behind door 2 , contestant chose door 1 
    ## Try 183 - Prize is behind door 3 , contestant chose door 1 
    ## Try 184 - Prize is behind door 2 , contestant chose door 2 
    ## Try 185 - Prize is behind door 1 , contestant chose door 3 
    ## Try 186 - Prize is behind door 2 , contestant chose door 3 
    ## Try 187 - Prize is behind door 2 , contestant chose door 3 
    ## Try 188 - Prize is behind door 2 , contestant chose door 2 
    ## Try 189 - Prize is behind door 2 , contestant chose door 3 
    ## Try 190 - Prize is behind door 1 , contestant chose door 3 
    ## Try 191 - Prize is behind door 3 , contestant chose door 3 
    ## Try 192 - Prize is behind door 2 , contestant chose door 2 
    ## Try 193 - Prize is behind door 1 , contestant chose door 2 
    ## Try 194 - Prize is behind door 1 , contestant chose door 1 
    ## Try 195 - Prize is behind door 3 , contestant chose door 1 
    ## Try 196 - Prize is behind door 3 , contestant chose door 1 
    ## Try 197 - Prize is behind door 1 , contestant chose door 2 
    ## Try 198 - Prize is behind door 1 , contestant chose door 1 
    ## Try 199 - Prize is behind door 1 , contestant chose door 1 
    ## Try 200 - Prize is behind door 2 , contestant chose door 1 
    ## Try 201 - Prize is behind door 1 , contestant chose door 2 
    ## Try 202 - Prize is behind door 2 , contestant chose door 2 
    ## Try 203 - Prize is behind door 3 , contestant chose door 1 
    ## Try 204 - Prize is behind door 1 , contestant chose door 3 
    ## Try 205 - Prize is behind door 3 , contestant chose door 1 
    ## Try 206 - Prize is behind door 2 , contestant chose door 2 
    ## Try 207 - Prize is behind door 2 , contestant chose door 1 
    ## Try 208 - Prize is behind door 2 , contestant chose door 3 
    ## Try 209 - Prize is behind door 3 , contestant chose door 1 
    ## Try 210 - Prize is behind door 2 , contestant chose door 2 
    ## Try 211 - Prize is behind door 1 , contestant chose door 1 
    ## Try 212 - Prize is behind door 2 , contestant chose door 3 
    ## Try 213 - Prize is behind door 1 , contestant chose door 1 
    ## Try 214 - Prize is behind door 3 , contestant chose door 3 
    ## Try 215 - Prize is behind door 3 , contestant chose door 1 
    ## Try 216 - Prize is behind door 3 , contestant chose door 1 
    ## Try 217 - Prize is behind door 2 , contestant chose door 2 
    ## Try 218 - Prize is behind door 1 , contestant chose door 2 
    ## Try 219 - Prize is behind door 1 , contestant chose door 2 
    ## Try 220 - Prize is behind door 2 , contestant chose door 1 
    ## Try 221 - Prize is behind door 2 , contestant chose door 2 
    ## Try 222 - Prize is behind door 2 , contestant chose door 1 
    ## Try 223 - Prize is behind door 3 , contestant chose door 3 
    ## Try 224 - Prize is behind door 1 , contestant chose door 1 
    ## Try 225 - Prize is behind door 3 , contestant chose door 3 
    ## Try 226 - Prize is behind door 3 , contestant chose door 3 
    ## Try 227 - Prize is behind door 1 , contestant chose door 1 
    ## Try 228 - Prize is behind door 2 , contestant chose door 1 
    ## Try 229 - Prize is behind door 1 , contestant chose door 2 
    ## Try 230 - Prize is behind door 1 , contestant chose door 2 
    ## Try 231 - Prize is behind door 1 , contestant chose door 3 
    ## Try 232 - Prize is behind door 1 , contestant chose door 3 
    ## Try 233 - Prize is behind door 3 , contestant chose door 2 
    ## Try 234 - Prize is behind door 3 , contestant chose door 2 
    ## Try 235 - Prize is behind door 1 , contestant chose door 1 
    ## Try 236 - Prize is behind door 1 , contestant chose door 3 
    ## Try 237 - Prize is behind door 1 , contestant chose door 1 
    ## Try 238 - Prize is behind door 3 , contestant chose door 3 
    ## Try 239 - Prize is behind door 2 , contestant chose door 2 
    ## Try 240 - Prize is behind door 2 , contestant chose door 3 
    ## Try 241 - Prize is behind door 2 , contestant chose door 3 
    ## Try 242 - Prize is behind door 2 , contestant chose door 1 
    ## Try 243 - Prize is behind door 2 , contestant chose door 1 
    ## Try 244 - Prize is behind door 3 , contestant chose door 3 
    ## Try 245 - Prize is behind door 3 , contestant chose door 1 
    ## Try 246 - Prize is behind door 3 , contestant chose door 3 
    ## Try 247 - Prize is behind door 1 , contestant chose door 1 
    ## Try 248 - Prize is behind door 2 , contestant chose door 2 
    ## Try 249 - Prize is behind door 2 , contestant chose door 1 
    ## Try 250 - Prize is behind door 3 , contestant chose door 3 
    ## Try 251 - Prize is behind door 3 , contestant chose door 2 
    ## Try 252 - Prize is behind door 2 , contestant chose door 3 
    ## Try 253 - Prize is behind door 1 , contestant chose door 3 
    ## Try 254 - Prize is behind door 3 , contestant chose door 2 
    ## Try 255 - Prize is behind door 2 , contestant chose door 1 
    ## Try 256 - Prize is behind door 2 , contestant chose door 1 
    ## Try 257 - Prize is behind door 3 , contestant chose door 3 
    ## Try 258 - Prize is behind door 1 , contestant chose door 2 
    ## Try 259 - Prize is behind door 2 , contestant chose door 2 
    ## Try 260 - Prize is behind door 1 , contestant chose door 1 
    ## Try 261 - Prize is behind door 1 , contestant chose door 3 
    ## Try 262 - Prize is behind door 3 , contestant chose door 3 
    ## Try 263 - Prize is behind door 2 , contestant chose door 1 
    ## Try 264 - Prize is behind door 2 , contestant chose door 1 
    ## Try 265 - Prize is behind door 3 , contestant chose door 3 
    ## Try 266 - Prize is behind door 3 , contestant chose door 3 
    ## Try 267 - Prize is behind door 3 , contestant chose door 1 
    ## Try 268 - Prize is behind door 1 , contestant chose door 1 
    ## Try 269 - Prize is behind door 2 , contestant chose door 1 
    ## Try 270 - Prize is behind door 1 , contestant chose door 3 
    ## Try 271 - Prize is behind door 3 , contestant chose door 3 
    ## Try 272 - Prize is behind door 3 , contestant chose door 1 
    ## Try 273 - Prize is behind door 1 , contestant chose door 2 
    ## Try 274 - Prize is behind door 2 , contestant chose door 1 
    ## Try 275 - Prize is behind door 2 , contestant chose door 1 
    ## Try 276 - Prize is behind door 1 , contestant chose door 2 
    ## Try 277 - Prize is behind door 1 , contestant chose door 1 
    ## Try 278 - Prize is behind door 2 , contestant chose door 1 
    ## Try 279 - Prize is behind door 3 , contestant chose door 2 
    ## Try 280 - Prize is behind door 2 , contestant chose door 3 
    ## Try 281 - Prize is behind door 2 , contestant chose door 1 
    ## Try 282 - Prize is behind door 1 , contestant chose door 3 
    ## Try 283 - Prize is behind door 1 , contestant chose door 3 
    ## Try 284 - Prize is behind door 1 , contestant chose door 3 
    ## Try 285 - Prize is behind door 2 , contestant chose door 1 
    ## Try 286 - Prize is behind door 3 , contestant chose door 3 
    ## Try 287 - Prize is behind door 2 , contestant chose door 2 
    ## Try 288 - Prize is behind door 3 , contestant chose door 2 
    ## Try 289 - Prize is behind door 2 , contestant chose door 1 
    ## Try 290 - Prize is behind door 3 , contestant chose door 2 
    ## Try 291 - Prize is behind door 1 , contestant chose door 3 
    ## Try 292 - Prize is behind door 3 , contestant chose door 3 
    ## Try 293 - Prize is behind door 3 , contestant chose door 1 
    ## Try 294 - Prize is behind door 3 , contestant chose door 2 
    ## Try 295 - Prize is behind door 3 , contestant chose door 3 
    ## Try 296 - Prize is behind door 3 , contestant chose door 3 
    ## Try 297 - Prize is behind door 3 , contestant chose door 1 
    ## Try 298 - Prize is behind door 1 , contestant chose door 2 
    ## Try 299 - Prize is behind door 3 , contestant chose door 2 
    ## Try 300 - Prize is behind door 1 , contestant chose door 2 
    ## Try 301 - Prize is behind door 2 , contestant chose door 2 
    ## Try 302 - Prize is behind door 2 , contestant chose door 3 
    ## Try 303 - Prize is behind door 2 , contestant chose door 1 
    ## Try 304 - Prize is behind door 3 , contestant chose door 2 
    ## Try 305 - Prize is behind door 2 , contestant chose door 1 
    ## Try 306 - Prize is behind door 2 , contestant chose door 1 
    ## Try 307 - Prize is behind door 2 , contestant chose door 3 
    ## Try 308 - Prize is behind door 3 , contestant chose door 2 
    ## Try 309 - Prize is behind door 3 , contestant chose door 3 
    ## Try 310 - Prize is behind door 1 , contestant chose door 1 
    ## Try 311 - Prize is behind door 1 , contestant chose door 2 
    ## Try 312 - Prize is behind door 2 , contestant chose door 2 
    ## Try 313 - Prize is behind door 2 , contestant chose door 3 
    ## Try 314 - Prize is behind door 1 , contestant chose door 2 
    ## Try 315 - Prize is behind door 2 , contestant chose door 1 
    ## Try 316 - Prize is behind door 1 , contestant chose door 2 
    ## Try 317 - Prize is behind door 1 , contestant chose door 3 
    ## Try 318 - Prize is behind door 2 , contestant chose door 3 
    ## Try 319 - Prize is behind door 3 , contestant chose door 2 
    ## Try 320 - Prize is behind door 2 , contestant chose door 1 
    ## Try 321 - Prize is behind door 1 , contestant chose door 3 
    ## Try 322 - Prize is behind door 3 , contestant chose door 1 
    ## Try 323 - Prize is behind door 3 , contestant chose door 2 
    ## Try 324 - Prize is behind door 3 , contestant chose door 2 
    ## Try 325 - Prize is behind door 2 , contestant chose door 3 
    ## Try 326 - Prize is behind door 2 , contestant chose door 1 
    ## Try 327 - Prize is behind door 3 , contestant chose door 1 
    ## Try 328 - Prize is behind door 3 , contestant chose door 3 
    ## Try 329 - Prize is behind door 2 , contestant chose door 3 
    ## Try 330 - Prize is behind door 2 , contestant chose door 2 
    ## Try 331 - Prize is behind door 3 , contestant chose door 2 
    ## Try 332 - Prize is behind door 3 , contestant chose door 2 
    ## Try 333 - Prize is behind door 1 , contestant chose door 3 
    ## Try 334 - Prize is behind door 2 , contestant chose door 3 
    ## Try 335 - Prize is behind door 3 , contestant chose door 2 
    ## Try 336 - Prize is behind door 3 , contestant chose door 1 
    ## Try 337 - Prize is behind door 2 , contestant chose door 2 
    ## Try 338 - Prize is behind door 1 , contestant chose door 2 
    ## Try 339 - Prize is behind door 3 , contestant chose door 3 
    ## Try 340 - Prize is behind door 1 , contestant chose door 1 
    ## Try 341 - Prize is behind door 3 , contestant chose door 2 
    ## Try 342 - Prize is behind door 2 , contestant chose door 1 
    ## Try 343 - Prize is behind door 2 , contestant chose door 2 
    ## Try 344 - Prize is behind door 3 , contestant chose door 2 
    ## Try 345 - Prize is behind door 1 , contestant chose door 3 
    ## Try 346 - Prize is behind door 2 , contestant chose door 1 
    ## Try 347 - Prize is behind door 1 , contestant chose door 2 
    ## Try 348 - Prize is behind door 2 , contestant chose door 2 
    ## Try 349 - Prize is behind door 1 , contestant chose door 2 
    ## Try 350 - Prize is behind door 1 , contestant chose door 1 
    ## Try 351 - Prize is behind door 3 , contestant chose door 3 
    ## Try 352 - Prize is behind door 2 , contestant chose door 1 
    ## Try 353 - Prize is behind door 3 , contestant chose door 1 
    ## Try 354 - Prize is behind door 2 , contestant chose door 3 
    ## Try 355 - Prize is behind door 1 , contestant chose door 3 
    ## Try 356 - Prize is behind door 1 , contestant chose door 2 
    ## Try 357 - Prize is behind door 1 , contestant chose door 3 
    ## Try 358 - Prize is behind door 3 , contestant chose door 1 
    ## Try 359 - Prize is behind door 3 , contestant chose door 3 
    ## Try 360 - Prize is behind door 3 , contestant chose door 1 
    ## Try 361 - Prize is behind door 1 , contestant chose door 3 
    ## Try 362 - Prize is behind door 3 , contestant chose door 1 
    ## Try 363 - Prize is behind door 2 , contestant chose door 3 
    ## Try 364 - Prize is behind door 1 , contestant chose door 2 
    ## Try 365 - Prize is behind door 1 , contestant chose door 2 
    ## Try 366 - Prize is behind door 3 , contestant chose door 3 
    ## Try 367 - Prize is behind door 2 , contestant chose door 1 
    ## Try 368 - Prize is behind door 2 , contestant chose door 1 
    ## Try 369 - Prize is behind door 1 , contestant chose door 2 
    ## Try 370 - Prize is behind door 2 , contestant chose door 1 
    ## Try 371 - Prize is behind door 2 , contestant chose door 2 
    ## Try 372 - Prize is behind door 1 , contestant chose door 2 
    ## Try 373 - Prize is behind door 1 , contestant chose door 3 
    ## Try 374 - Prize is behind door 2 , contestant chose door 2 
    ## Try 375 - Prize is behind door 2 , contestant chose door 3 
    ## Try 376 - Prize is behind door 3 , contestant chose door 3 
    ## Try 377 - Prize is behind door 3 , contestant chose door 3 
    ## Try 378 - Prize is behind door 3 , contestant chose door 1 
    ## Try 379 - Prize is behind door 2 , contestant chose door 2 
    ## Try 380 - Prize is behind door 3 , contestant chose door 1 
    ## Try 381 - Prize is behind door 2 , contestant chose door 2 
    ## Try 382 - Prize is behind door 1 , contestant chose door 2 
    ## Try 383 - Prize is behind door 2 , contestant chose door 3 
    ## Try 384 - Prize is behind door 3 , contestant chose door 1 
    ## Try 385 - Prize is behind door 3 , contestant chose door 2 
    ## Try 386 - Prize is behind door 1 , contestant chose door 1 
    ## Try 387 - Prize is behind door 1 , contestant chose door 3 
    ## Try 388 - Prize is behind door 1 , contestant chose door 1 
    ## Try 389 - Prize is behind door 3 , contestant chose door 2 
    ## Try 390 - Prize is behind door 3 , contestant chose door 1 
    ## Try 391 - Prize is behind door 2 , contestant chose door 1 
    ## Try 392 - Prize is behind door 2 , contestant chose door 1 
    ## Try 393 - Prize is behind door 1 , contestant chose door 3 
    ## Try 394 - Prize is behind door 1 , contestant chose door 2 
    ## Try 395 - Prize is behind door 2 , contestant chose door 2 
    ## Try 396 - Prize is behind door 3 , contestant chose door 1 
    ## Try 397 - Prize is behind door 2 , contestant chose door 1 
    ## Try 398 - Prize is behind door 3 , contestant chose door 3 
    ## Try 399 - Prize is behind door 2 , contestant chose door 2 
    ## Try 400 - Prize is behind door 1 , contestant chose door 1 
    ## Try 401 - Prize is behind door 3 , contestant chose door 1 
    ## Try 402 - Prize is behind door 3 , contestant chose door 2 
    ## Try 403 - Prize is behind door 2 , contestant chose door 3 
    ## Try 404 - Prize is behind door 3 , contestant chose door 1 
    ## Try 405 - Prize is behind door 2 , contestant chose door 1 
    ## Try 406 - Prize is behind door 3 , contestant chose door 3 
    ## Try 407 - Prize is behind door 1 , contestant chose door 3 
    ## Try 408 - Prize is behind door 3 , contestant chose door 2 
    ## Try 409 - Prize is behind door 3 , contestant chose door 2 
    ## Try 410 - Prize is behind door 1 , contestant chose door 1 
    ## Try 411 - Prize is behind door 2 , contestant chose door 1 
    ## Try 412 - Prize is behind door 3 , contestant chose door 1 
    ## Try 413 - Prize is behind door 3 , contestant chose door 2 
    ## Try 414 - Prize is behind door 2 , contestant chose door 2 
    ## Try 415 - Prize is behind door 3 , contestant chose door 3 
    ## Try 416 - Prize is behind door 3 , contestant chose door 2 
    ## Try 417 - Prize is behind door 3 , contestant chose door 1 
    ## Try 418 - Prize is behind door 1 , contestant chose door 3 
    ## Try 419 - Prize is behind door 1 , contestant chose door 2 
    ## Try 420 - Prize is behind door 3 , contestant chose door 3 
    ## Try 421 - Prize is behind door 3 , contestant chose door 2 
    ## Try 422 - Prize is behind door 3 , contestant chose door 2 
    ## Try 423 - Prize is behind door 1 , contestant chose door 3 
    ## Try 424 - Prize is behind door 1 , contestant chose door 2 
    ## Try 425 - Prize is behind door 1 , contestant chose door 2 
    ## Try 426 - Prize is behind door 3 , contestant chose door 2 
    ## Try 427 - Prize is behind door 3 , contestant chose door 1 
    ## Try 428 - Prize is behind door 3 , contestant chose door 2 
    ## Try 429 - Prize is behind door 3 , contestant chose door 2 
    ## Try 430 - Prize is behind door 3 , contestant chose door 2 
    ## Try 431 - Prize is behind door 2 , contestant chose door 1 
    ## Try 432 - Prize is behind door 1 , contestant chose door 2 
    ## Try 433 - Prize is behind door 3 , contestant chose door 1 
    ## Try 434 - Prize is behind door 2 , contestant chose door 1 
    ## Try 435 - Prize is behind door 2 , contestant chose door 2 
    ## Try 436 - Prize is behind door 2 , contestant chose door 3 
    ## Try 437 - Prize is behind door 1 , contestant chose door 3 
    ## Try 438 - Prize is behind door 2 , contestant chose door 2 
    ## Try 439 - Prize is behind door 3 , contestant chose door 3 
    ## Try 440 - Prize is behind door 3 , contestant chose door 2 
    ## Try 441 - Prize is behind door 3 , contestant chose door 2 
    ## Try 442 - Prize is behind door 1 , contestant chose door 2 
    ## Try 443 - Prize is behind door 1 , contestant chose door 1 
    ## Try 444 - Prize is behind door 1 , contestant chose door 1 
    ## Try 445 - Prize is behind door 3 , contestant chose door 3 
    ## Try 446 - Prize is behind door 3 , contestant chose door 2 
    ## Try 447 - Prize is behind door 3 , contestant chose door 3 
    ## Try 448 - Prize is behind door 1 , contestant chose door 3 
    ## Try 449 - Prize is behind door 2 , contestant chose door 3 
    ## Try 450 - Prize is behind door 3 , contestant chose door 1 
    ## Try 451 - Prize is behind door 3 , contestant chose door 3 
    ## Try 452 - Prize is behind door 1 , contestant chose door 1 
    ## Try 453 - Prize is behind door 2 , contestant chose door 1 
    ## Try 454 - Prize is behind door 1 , contestant chose door 1 
    ## Try 455 - Prize is behind door 3 , contestant chose door 3 
    ## Try 456 - Prize is behind door 3 , contestant chose door 3 
    ## Try 457 - Prize is behind door 2 , contestant chose door 1 
    ## Try 458 - Prize is behind door 1 , contestant chose door 3 
    ## Try 459 - Prize is behind door 3 , contestant chose door 1 
    ## Try 460 - Prize is behind door 3 , contestant chose door 1 
    ## Try 461 - Prize is behind door 2 , contestant chose door 2 
    ## Try 462 - Prize is behind door 3 , contestant chose door 2 
    ## Try 463 - Prize is behind door 1 , contestant chose door 1 
    ## Try 464 - Prize is behind door 1 , contestant chose door 2 
    ## Try 465 - Prize is behind door 1 , contestant chose door 2 
    ## Try 466 - Prize is behind door 3 , contestant chose door 3 
    ## Try 467 - Prize is behind door 3 , contestant chose door 1 
    ## Try 468 - Prize is behind door 3 , contestant chose door 3 
    ## Try 469 - Prize is behind door 2 , contestant chose door 1 
    ## Try 470 - Prize is behind door 1 , contestant chose door 3 
    ## Try 471 - Prize is behind door 2 , contestant chose door 3 
    ## Try 472 - Prize is behind door 3 , contestant chose door 2 
    ## Try 473 - Prize is behind door 1 , contestant chose door 1 
    ## Try 474 - Prize is behind door 2 , contestant chose door 3 
    ## Try 475 - Prize is behind door 2 , contestant chose door 2 
    ## Try 476 - Prize is behind door 1 , contestant chose door 2 
    ## Try 477 - Prize is behind door 1 , contestant chose door 1 
    ## Try 478 - Prize is behind door 1 , contestant chose door 1 
    ## Try 479 - Prize is behind door 1 , contestant chose door 2 
    ## Try 480 - Prize is behind door 2 , contestant chose door 3 
    ## Try 481 - Prize is behind door 3 , contestant chose door 3 
    ## Try 482 - Prize is behind door 3 , contestant chose door 3 
    ## Try 483 - Prize is behind door 1 , contestant chose door 1 
    ## Try 484 - Prize is behind door 2 , contestant chose door 3 
    ## Try 485 - Prize is behind door 3 , contestant chose door 1 
    ## Try 486 - Prize is behind door 3 , contestant chose door 3 
    ## Try 487 - Prize is behind door 1 , contestant chose door 3 
    ## Try 488 - Prize is behind door 1 , contestant chose door 3 
    ## Try 489 - Prize is behind door 3 , contestant chose door 2 
    ## Try 490 - Prize is behind door 3 , contestant chose door 3 
    ## Try 491 - Prize is behind door 2 , contestant chose door 1 
    ## Try 492 - Prize is behind door 1 , contestant chose door 3 
    ## Try 493 - Prize is behind door 1 , contestant chose door 3 
    ## Try 494 - Prize is behind door 2 , contestant chose door 1 
    ## Try 495 - Prize is behind door 3 , contestant chose door 2 
    ## Try 496 - Prize is behind door 3 , contestant chose door 1 
    ## Try 497 - Prize is behind door 1 , contestant chose door 2 
    ## Try 498 - Prize is behind door 1 , contestant chose door 1 
    ## Try 499 - Prize is behind door 2 , contestant chose door 3 
    ## Try 500 - Prize is behind door 3 , contestant chose door 1 
    ## Try 501 - Prize is behind door 2 , contestant chose door 3 
    ## Try 502 - Prize is behind door 2 , contestant chose door 3 
    ## Try 503 - Prize is behind door 2 , contestant chose door 2 
    ## Try 504 - Prize is behind door 2 , contestant chose door 3 
    ## Try 505 - Prize is behind door 1 , contestant chose door 2 
    ## Try 506 - Prize is behind door 1 , contestant chose door 2 
    ## Try 507 - Prize is behind door 3 , contestant chose door 3 
    ## Try 508 - Prize is behind door 1 , contestant chose door 1 
    ## Try 509 - Prize is behind door 3 , contestant chose door 2 
    ## Try 510 - Prize is behind door 1 , contestant chose door 2 
    ## Try 511 - Prize is behind door 3 , contestant chose door 2 
    ## Try 512 - Prize is behind door 2 , contestant chose door 1 
    ## Try 513 - Prize is behind door 2 , contestant chose door 2 
    ## Try 514 - Prize is behind door 2 , contestant chose door 1 
    ## Try 515 - Prize is behind door 2 , contestant chose door 1 
    ## Try 516 - Prize is behind door 1 , contestant chose door 3 
    ## Try 517 - Prize is behind door 2 , contestant chose door 3 
    ## Try 518 - Prize is behind door 3 , contestant chose door 3 
    ## Try 519 - Prize is behind door 2 , contestant chose door 2 
    ## Try 520 - Prize is behind door 1 , contestant chose door 3 
    ## Try 521 - Prize is behind door 3 , contestant chose door 2 
    ## Try 522 - Prize is behind door 1 , contestant chose door 2 
    ## Try 523 - Prize is behind door 2 , contestant chose door 3 
    ## Try 524 - Prize is behind door 3 , contestant chose door 1 
    ## Try 525 - Prize is behind door 2 , contestant chose door 3 
    ## Try 526 - Prize is behind door 2 , contestant chose door 1 
    ## Try 527 - Prize is behind door 1 , contestant chose door 3 
    ## Try 528 - Prize is behind door 2 , contestant chose door 2 
    ## Try 529 - Prize is behind door 3 , contestant chose door 1 
    ## Try 530 - Prize is behind door 2 , contestant chose door 3 
    ## Try 531 - Prize is behind door 3 , contestant chose door 1 
    ## Try 532 - Prize is behind door 2 , contestant chose door 1 
    ## Try 533 - Prize is behind door 2 , contestant chose door 1 
    ## Try 534 - Prize is behind door 1 , contestant chose door 3 
    ## Try 535 - Prize is behind door 3 , contestant chose door 3 
    ## Try 536 - Prize is behind door 2 , contestant chose door 3 
    ## Try 537 - Prize is behind door 1 , contestant chose door 1 
    ## Try 538 - Prize is behind door 1 , contestant chose door 3 
    ## Try 539 - Prize is behind door 3 , contestant chose door 1 
    ## Try 540 - Prize is behind door 1 , contestant chose door 3 
    ## Try 541 - Prize is behind door 2 , contestant chose door 3 
    ## Try 542 - Prize is behind door 2 , contestant chose door 3 
    ## Try 543 - Prize is behind door 2 , contestant chose door 3 
    ## Try 544 - Prize is behind door 2 , contestant chose door 1 
    ## Try 545 - Prize is behind door 1 , contestant chose door 2 
    ## Try 546 - Prize is behind door 1 , contestant chose door 1 
    ## Try 547 - Prize is behind door 1 , contestant chose door 3 
    ## Try 548 - Prize is behind door 1 , contestant chose door 3 
    ## Try 549 - Prize is behind door 3 , contestant chose door 1 
    ## Try 550 - Prize is behind door 1 , contestant chose door 1 
    ## Try 551 - Prize is behind door 1 , contestant chose door 3 
    ## Try 552 - Prize is behind door 2 , contestant chose door 1 
    ## Try 553 - Prize is behind door 3 , contestant chose door 3 
    ## Try 554 - Prize is behind door 3 , contestant chose door 2 
    ## Try 555 - Prize is behind door 1 , contestant chose door 1 
    ## Try 556 - Prize is behind door 2 , contestant chose door 3 
    ## Try 557 - Prize is behind door 1 , contestant chose door 3 
    ## Try 558 - Prize is behind door 2 , contestant chose door 1 
    ## Try 559 - Prize is behind door 3 , contestant chose door 1 
    ## Try 560 - Prize is behind door 2 , contestant chose door 1 
    ## Try 561 - Prize is behind door 1 , contestant chose door 3 
    ## Try 562 - Prize is behind door 3 , contestant chose door 2 
    ## Try 563 - Prize is behind door 1 , contestant chose door 1 
    ## Try 564 - Prize is behind door 3 , contestant chose door 1 
    ## Try 565 - Prize is behind door 3 , contestant chose door 2 
    ## Try 566 - Prize is behind door 3 , contestant chose door 1 
    ## Try 567 - Prize is behind door 3 , contestant chose door 2 
    ## Try 568 - Prize is behind door 1 , contestant chose door 2 
    ## Try 569 - Prize is behind door 1 , contestant chose door 2 
    ## Try 570 - Prize is behind door 2 , contestant chose door 3 
    ## Try 571 - Prize is behind door 3 , contestant chose door 3 
    ## Try 572 - Prize is behind door 1 , contestant chose door 3 
    ## Try 573 - Prize is behind door 2 , contestant chose door 3 
    ## Try 574 - Prize is behind door 1 , contestant chose door 2 
    ## Try 575 - Prize is behind door 3 , contestant chose door 2 
    ## Try 576 - Prize is behind door 2 , contestant chose door 1 
    ## Try 577 - Prize is behind door 2 , contestant chose door 3 
    ## Try 578 - Prize is behind door 3 , contestant chose door 1 
    ## Try 579 - Prize is behind door 2 , contestant chose door 1 
    ## Try 580 - Prize is behind door 3 , contestant chose door 1 
    ## Try 581 - Prize is behind door 1 , contestant chose door 2 
    ## Try 582 - Prize is behind door 3 , contestant chose door 1 
    ## Try 583 - Prize is behind door 3 , contestant chose door 1 
    ## Try 584 - Prize is behind door 1 , contestant chose door 3 
    ## Try 585 - Prize is behind door 1 , contestant chose door 2 
    ## Try 586 - Prize is behind door 2 , contestant chose door 2 
    ## Try 587 - Prize is behind door 1 , contestant chose door 2 
    ## Try 588 - Prize is behind door 3 , contestant chose door 1 
    ## Try 589 - Prize is behind door 2 , contestant chose door 3 
    ## Try 590 - Prize is behind door 3 , contestant chose door 2 
    ## Try 591 - Prize is behind door 2 , contestant chose door 1 
    ## Try 592 - Prize is behind door 2 , contestant chose door 2 
    ## Try 593 - Prize is behind door 1 , contestant chose door 1 
    ## Try 594 - Prize is behind door 3 , contestant chose door 3 
    ## Try 595 - Prize is behind door 3 , contestant chose door 3 
    ## Try 596 - Prize is behind door 1 , contestant chose door 1 
    ## Try 597 - Prize is behind door 2 , contestant chose door 1 
    ## Try 598 - Prize is behind door 3 , contestant chose door 3 
    ## Try 599 - Prize is behind door 2 , contestant chose door 2 
    ## Try 600 - Prize is behind door 1 , contestant chose door 1 
    ## Try 601 - Prize is behind door 3 , contestant chose door 2 
    ## Try 602 - Prize is behind door 1 , contestant chose door 1 
    ## Try 603 - Prize is behind door 2 , contestant chose door 1 
    ## Try 604 - Prize is behind door 1 , contestant chose door 3 
    ## Try 605 - Prize is behind door 3 , contestant chose door 2 
    ## Try 606 - Prize is behind door 3 , contestant chose door 2 
    ## Try 607 - Prize is behind door 3 , contestant chose door 3 
    ## Try 608 - Prize is behind door 2 , contestant chose door 3 
    ## Try 609 - Prize is behind door 1 , contestant chose door 2 
    ## Try 610 - Prize is behind door 1 , contestant chose door 1 
    ## Try 611 - Prize is behind door 3 , contestant chose door 3 
    ## Try 612 - Prize is behind door 1 , contestant chose door 2 
    ## Try 613 - Prize is behind door 2 , contestant chose door 1 
    ## Try 614 - Prize is behind door 1 , contestant chose door 3 
    ## Try 615 - Prize is behind door 3 , contestant chose door 1 
    ## Try 616 - Prize is behind door 3 , contestant chose door 1 
    ## Try 617 - Prize is behind door 1 , contestant chose door 3 
    ## Try 618 - Prize is behind door 1 , contestant chose door 1 
    ## Try 619 - Prize is behind door 1 , contestant chose door 3 
    ## Try 620 - Prize is behind door 3 , contestant chose door 3 
    ## Try 621 - Prize is behind door 2 , contestant chose door 3 
    ## Try 622 - Prize is behind door 3 , contestant chose door 1 
    ## Try 623 - Prize is behind door 1 , contestant chose door 1 
    ## Try 624 - Prize is behind door 2 , contestant chose door 1 
    ## Try 625 - Prize is behind door 3 , contestant chose door 1 
    ## Try 626 - Prize is behind door 1 , contestant chose door 2 
    ## Try 627 - Prize is behind door 3 , contestant chose door 3 
    ## Try 628 - Prize is behind door 3 , contestant chose door 3 
    ## Try 629 - Prize is behind door 2 , contestant chose door 3 
    ## Try 630 - Prize is behind door 3 , contestant chose door 2 
    ## Try 631 - Prize is behind door 1 , contestant chose door 1 
    ## Try 632 - Prize is behind door 1 , contestant chose door 2 
    ## Try 633 - Prize is behind door 1 , contestant chose door 1 
    ## Try 634 - Prize is behind door 3 , contestant chose door 1 
    ## Try 635 - Prize is behind door 2 , contestant chose door 3 
    ## Try 636 - Prize is behind door 2 , contestant chose door 3 
    ## Try 637 - Prize is behind door 1 , contestant chose door 3 
    ## Try 638 - Prize is behind door 1 , contestant chose door 3 
    ## Try 639 - Prize is behind door 2 , contestant chose door 3 
    ## Try 640 - Prize is behind door 3 , contestant chose door 3 
    ## Try 641 - Prize is behind door 3 , contestant chose door 2 
    ## Try 642 - Prize is behind door 1 , contestant chose door 1 
    ## Try 643 - Prize is behind door 1 , contestant chose door 3 
    ## Try 644 - Prize is behind door 1 , contestant chose door 1 
    ## Try 645 - Prize is behind door 2 , contestant chose door 2 
    ## Try 646 - Prize is behind door 3 , contestant chose door 2 
    ## Try 647 - Prize is behind door 3 , contestant chose door 3 
    ## Try 648 - Prize is behind door 1 , contestant chose door 2 
    ## Try 649 - Prize is behind door 1 , contestant chose door 1 
    ## Try 650 - Prize is behind door 2 , contestant chose door 3 
    ## Try 651 - Prize is behind door 1 , contestant chose door 1 
    ## Try 652 - Prize is behind door 3 , contestant chose door 1 
    ## Try 653 - Prize is behind door 1 , contestant chose door 3 
    ## Try 654 - Prize is behind door 2 , contestant chose door 2 
    ## Try 655 - Prize is behind door 3 , contestant chose door 1 
    ## Try 656 - Prize is behind door 3 , contestant chose door 3 
    ## Try 657 - Prize is behind door 3 , contestant chose door 3 
    ## Try 658 - Prize is behind door 3 , contestant chose door 1 
    ## Try 659 - Prize is behind door 2 , contestant chose door 3 
    ## Try 660 - Prize is behind door 3 , contestant chose door 2 
    ## Try 661 - Prize is behind door 1 , contestant chose door 1 
    ## Try 662 - Prize is behind door 2 , contestant chose door 3 
    ## Try 663 - Prize is behind door 2 , contestant chose door 2 
    ## Try 664 - Prize is behind door 3 , contestant chose door 1 
    ## Try 665 - Prize is behind door 1 , contestant chose door 3 
    ## Try 666 - Prize is behind door 2 , contestant chose door 3 
    ## Try 667 - Prize is behind door 2 , contestant chose door 1 
    ## Try 668 - Prize is behind door 3 , contestant chose door 1 
    ## Try 669 - Prize is behind door 3 , contestant chose door 1 
    ## Try 670 - Prize is behind door 1 , contestant chose door 1 
    ## Try 671 - Prize is behind door 3 , contestant chose door 3 
    ## Try 672 - Prize is behind door 3 , contestant chose door 3 
    ## Try 673 - Prize is behind door 3 , contestant chose door 3 
    ## Try 674 - Prize is behind door 2 , contestant chose door 2 
    ## Try 675 - Prize is behind door 2 , contestant chose door 3 
    ## Try 676 - Prize is behind door 3 , contestant chose door 1 
    ## Try 677 - Prize is behind door 2 , contestant chose door 3 
    ## Try 678 - Prize is behind door 3 , contestant chose door 3 
    ## Try 679 - Prize is behind door 3 , contestant chose door 2 
    ## Try 680 - Prize is behind door 3 , contestant chose door 1 
    ## Try 681 - Prize is behind door 1 , contestant chose door 1 
    ## Try 682 - Prize is behind door 3 , contestant chose door 1 
    ## Try 683 - Prize is behind door 2 , contestant chose door 2 
    ## Try 684 - Prize is behind door 1 , contestant chose door 3 
    ## Try 685 - Prize is behind door 1 , contestant chose door 3 
    ## Try 686 - Prize is behind door 1 , contestant chose door 1 
    ## Try 687 - Prize is behind door 1 , contestant chose door 1 
    ## Try 688 - Prize is behind door 3 , contestant chose door 2 
    ## Try 689 - Prize is behind door 3 , contestant chose door 3 
    ## Try 690 - Prize is behind door 2 , contestant chose door 1 
    ## Try 691 - Prize is behind door 3 , contestant chose door 1 
    ## Try 692 - Prize is behind door 1 , contestant chose door 1 
    ## Try 693 - Prize is behind door 2 , contestant chose door 1 
    ## Try 694 - Prize is behind door 1 , contestant chose door 3 
    ## Try 695 - Prize is behind door 1 , contestant chose door 1 
    ## Try 696 - Prize is behind door 2 , contestant chose door 2 
    ## Try 697 - Prize is behind door 1 , contestant chose door 2 
    ## Try 698 - Prize is behind door 1 , contestant chose door 2 
    ## Try 699 - Prize is behind door 1 , contestant chose door 1 
    ## Try 700 - Prize is behind door 3 , contestant chose door 3 
    ## Try 701 - Prize is behind door 1 , contestant chose door 2 
    ## Try 702 - Prize is behind door 2 , contestant chose door 2 
    ## Try 703 - Prize is behind door 1 , contestant chose door 2 
    ## Try 704 - Prize is behind door 3 , contestant chose door 1 
    ## Try 705 - Prize is behind door 3 , contestant chose door 1 
    ## Try 706 - Prize is behind door 3 , contestant chose door 2 
    ## Try 707 - Prize is behind door 3 , contestant chose door 1 
    ## Try 708 - Prize is behind door 1 , contestant chose door 2 
    ## Try 709 - Prize is behind door 1 , contestant chose door 3 
    ## Try 710 - Prize is behind door 2 , contestant chose door 3 
    ## Try 711 - Prize is behind door 1 , contestant chose door 3 
    ## Try 712 - Prize is behind door 1 , contestant chose door 1 
    ## Try 713 - Prize is behind door 1 , contestant chose door 3 
    ## Try 714 - Prize is behind door 1 , contestant chose door 3 
    ## Try 715 - Prize is behind door 2 , contestant chose door 1 
    ## Try 716 - Prize is behind door 3 , contestant chose door 2 
    ## Try 717 - Prize is behind door 1 , contestant chose door 3 
    ## Try 718 - Prize is behind door 1 , contestant chose door 3 
    ## Try 719 - Prize is behind door 2 , contestant chose door 1 
    ## Try 720 - Prize is behind door 2 , contestant chose door 1 
    ## Try 721 - Prize is behind door 1 , contestant chose door 2 
    ## Try 722 - Prize is behind door 1 , contestant chose door 3 
    ## Try 723 - Prize is behind door 2 , contestant chose door 3 
    ## Try 724 - Prize is behind door 3 , contestant chose door 2 
    ## Try 725 - Prize is behind door 1 , contestant chose door 3 
    ## Try 726 - Prize is behind door 1 , contestant chose door 2 
    ## Try 727 - Prize is behind door 3 , contestant chose door 1 
    ## Try 728 - Prize is behind door 2 , contestant chose door 1 
    ## Try 729 - Prize is behind door 2 , contestant chose door 3 
    ## Try 730 - Prize is behind door 2 , contestant chose door 1 
    ## Try 731 - Prize is behind door 2 , contestant chose door 1 
    ## Try 732 - Prize is behind door 2 , contestant chose door 3 
    ## Try 733 - Prize is behind door 3 , contestant chose door 2 
    ## Try 734 - Prize is behind door 3 , contestant chose door 3 
    ## Try 735 - Prize is behind door 1 , contestant chose door 2 
    ## Try 736 - Prize is behind door 2 , contestant chose door 1 
    ## Try 737 - Prize is behind door 1 , contestant chose door 1 
    ## Try 738 - Prize is behind door 3 , contestant chose door 1 
    ## Try 739 - Prize is behind door 1 , contestant chose door 3 
    ## Try 740 - Prize is behind door 3 , contestant chose door 3 
    ## Try 741 - Prize is behind door 2 , contestant chose door 3 
    ## Try 742 - Prize is behind door 2 , contestant chose door 1 
    ## Try 743 - Prize is behind door 3 , contestant chose door 2 
    ## Try 744 - Prize is behind door 2 , contestant chose door 1 
    ## Try 745 - Prize is behind door 1 , contestant chose door 2 
    ## Try 746 - Prize is behind door 1 , contestant chose door 1 
    ## Try 747 - Prize is behind door 3 , contestant chose door 3 
    ## Try 748 - Prize is behind door 1 , contestant chose door 3 
    ## Try 749 - Prize is behind door 1 , contestant chose door 3 
    ## Try 750 - Prize is behind door 1 , contestant chose door 3 
    ## Try 751 - Prize is behind door 2 , contestant chose door 2 
    ## Try 752 - Prize is behind door 2 , contestant chose door 3 
    ## Try 753 - Prize is behind door 2 , contestant chose door 3 
    ## Try 754 - Prize is behind door 1 , contestant chose door 1 
    ## Try 755 - Prize is behind door 1 , contestant chose door 2 
    ## Try 756 - Prize is behind door 1 , contestant chose door 1 
    ## Try 757 - Prize is behind door 2 , contestant chose door 3 
    ## Try 758 - Prize is behind door 2 , contestant chose door 1 
    ## Try 759 - Prize is behind door 1 , contestant chose door 1 
    ## Try 760 - Prize is behind door 2 , contestant chose door 1 
    ## Try 761 - Prize is behind door 3 , contestant chose door 1 
    ## Try 762 - Prize is behind door 2 , contestant chose door 2 
    ## Try 763 - Prize is behind door 3 , contestant chose door 3 
    ## Try 764 - Prize is behind door 2 , contestant chose door 2 
    ## Try 765 - Prize is behind door 3 , contestant chose door 2 
    ## Try 766 - Prize is behind door 3 , contestant chose door 1 
    ## Try 767 - Prize is behind door 1 , contestant chose door 2 
    ## Try 768 - Prize is behind door 2 , contestant chose door 3 
    ## Try 769 - Prize is behind door 1 , contestant chose door 2 
    ## Try 770 - Prize is behind door 2 , contestant chose door 3 
    ## Try 771 - Prize is behind door 1 , contestant chose door 2 
    ## Try 772 - Prize is behind door 3 , contestant chose door 2 
    ## Try 773 - Prize is behind door 3 , contestant chose door 2 
    ## Try 774 - Prize is behind door 2 , contestant chose door 2 
    ## Try 775 - Prize is behind door 3 , contestant chose door 3 
    ## Try 776 - Prize is behind door 1 , contestant chose door 1 
    ## Try 777 - Prize is behind door 3 , contestant chose door 1 
    ## Try 778 - Prize is behind door 2 , contestant chose door 3 
    ## Try 779 - Prize is behind door 2 , contestant chose door 1 
    ## Try 780 - Prize is behind door 3 , contestant chose door 2 
    ## Try 781 - Prize is behind door 1 , contestant chose door 1 
    ## Try 782 - Prize is behind door 1 , contestant chose door 1 
    ## Try 783 - Prize is behind door 2 , contestant chose door 2 
    ## Try 784 - Prize is behind door 2 , contestant chose door 2 
    ## Try 785 - Prize is behind door 2 , contestant chose door 2 
    ## Try 786 - Prize is behind door 3 , contestant chose door 1 
    ## Try 787 - Prize is behind door 1 , contestant chose door 3 
    ## Try 788 - Prize is behind door 3 , contestant chose door 1 
    ## Try 789 - Prize is behind door 1 , contestant chose door 3 
    ## Try 790 - Prize is behind door 2 , contestant chose door 3 
    ## Try 791 - Prize is behind door 3 , contestant chose door 1 
    ## Try 792 - Prize is behind door 3 , contestant chose door 3 
    ## Try 793 - Prize is behind door 3 , contestant chose door 2 
    ## Try 794 - Prize is behind door 3 , contestant chose door 2 
    ## Try 795 - Prize is behind door 3 , contestant chose door 1 
    ## Try 796 - Prize is behind door 3 , contestant chose door 3 
    ## Try 797 - Prize is behind door 1 , contestant chose door 3 
    ## Try 798 - Prize is behind door 3 , contestant chose door 2 
    ## Try 799 - Prize is behind door 1 , contestant chose door 2 
    ## Try 800 - Prize is behind door 3 , contestant chose door 3 
    ## Try 801 - Prize is behind door 2 , contestant chose door 2 
    ## Try 802 - Prize is behind door 1 , contestant chose door 2 
    ## Try 803 - Prize is behind door 3 , contestant chose door 3 
    ## Try 804 - Prize is behind door 1 , contestant chose door 1 
    ## Try 805 - Prize is behind door 2 , contestant chose door 3 
    ## Try 806 - Prize is behind door 1 , contestant chose door 1 
    ## Try 807 - Prize is behind door 3 , contestant chose door 1 
    ## Try 808 - Prize is behind door 3 , contestant chose door 2 
    ## Try 809 - Prize is behind door 3 , contestant chose door 3 
    ## Try 810 - Prize is behind door 2 , contestant chose door 2 
    ## Try 811 - Prize is behind door 2 , contestant chose door 3 
    ## Try 812 - Prize is behind door 2 , contestant chose door 3 
    ## Try 813 - Prize is behind door 1 , contestant chose door 3 
    ## Try 814 - Prize is behind door 1 , contestant chose door 3 
    ## Try 815 - Prize is behind door 2 , contestant chose door 2 
    ## Try 816 - Prize is behind door 1 , contestant chose door 2 
    ## Try 817 - Prize is behind door 2 , contestant chose door 1 
    ## Try 818 - Prize is behind door 1 , contestant chose door 3 
    ## Try 819 - Prize is behind door 3 , contestant chose door 1 
    ## Try 820 - Prize is behind door 1 , contestant chose door 2 
    ## Try 821 - Prize is behind door 2 , contestant chose door 3 
    ## Try 822 - Prize is behind door 3 , contestant chose door 3 
    ## Try 823 - Prize is behind door 2 , contestant chose door 2 
    ## Try 824 - Prize is behind door 3 , contestant chose door 1 
    ## Try 825 - Prize is behind door 3 , contestant chose door 2 
    ## Try 826 - Prize is behind door 3 , contestant chose door 3 
    ## Try 827 - Prize is behind door 1 , contestant chose door 3 
    ## Try 828 - Prize is behind door 3 , contestant chose door 2 
    ## Try 829 - Prize is behind door 3 , contestant chose door 3 
    ## Try 830 - Prize is behind door 3 , contestant chose door 3 
    ## Try 831 - Prize is behind door 3 , contestant chose door 1 
    ## Try 832 - Prize is behind door 3 , contestant chose door 1 
    ## Try 833 - Prize is behind door 3 , contestant chose door 2 
    ## Try 834 - Prize is behind door 2 , contestant chose door 2 
    ## Try 835 - Prize is behind door 3 , contestant chose door 3 
    ## Try 836 - Prize is behind door 2 , contestant chose door 2 
    ## Try 837 - Prize is behind door 2 , contestant chose door 2 
    ## Try 838 - Prize is behind door 3 , contestant chose door 2 
    ## Try 839 - Prize is behind door 3 , contestant chose door 1 
    ## Try 840 - Prize is behind door 1 , contestant chose door 3 
    ## Try 841 - Prize is behind door 3 , contestant chose door 2 
    ## Try 842 - Prize is behind door 3 , contestant chose door 1 
    ## Try 843 - Prize is behind door 3 , contestant chose door 2 
    ## Try 844 - Prize is behind door 1 , contestant chose door 2 
    ## Try 845 - Prize is behind door 2 , contestant chose door 1 
    ## Try 846 - Prize is behind door 3 , contestant chose door 3 
    ## Try 847 - Prize is behind door 2 , contestant chose door 2 
    ## Try 848 - Prize is behind door 3 , contestant chose door 1 
    ## Try 849 - Prize is behind door 1 , contestant chose door 1 
    ## Try 850 - Prize is behind door 2 , contestant chose door 2 
    ## Try 851 - Prize is behind door 2 , contestant chose door 3 
    ## Try 852 - Prize is behind door 1 , contestant chose door 2 
    ## Try 853 - Prize is behind door 1 , contestant chose door 1 
    ## Try 854 - Prize is behind door 2 , contestant chose door 1 
    ## Try 855 - Prize is behind door 1 , contestant chose door 2 
    ## Try 856 - Prize is behind door 3 , contestant chose door 1 
    ## Try 857 - Prize is behind door 3 , contestant chose door 3 
    ## Try 858 - Prize is behind door 3 , contestant chose door 1 
    ## Try 859 - Prize is behind door 1 , contestant chose door 2 
    ## Try 860 - Prize is behind door 3 , contestant chose door 1 
    ## Try 861 - Prize is behind door 3 , contestant chose door 3 
    ## Try 862 - Prize is behind door 3 , contestant chose door 2 
    ## Try 863 - Prize is behind door 2 , contestant chose door 3 
    ## Try 864 - Prize is behind door 1 , contestant chose door 1 
    ## Try 865 - Prize is behind door 2 , contestant chose door 2 
    ## Try 866 - Prize is behind door 1 , contestant chose door 2 
    ## Try 867 - Prize is behind door 2 , contestant chose door 2 
    ## Try 868 - Prize is behind door 2 , contestant chose door 2 
    ## Try 869 - Prize is behind door 2 , contestant chose door 3 
    ## Try 870 - Prize is behind door 2 , contestant chose door 3 
    ## Try 871 - Prize is behind door 1 , contestant chose door 3 
    ## Try 872 - Prize is behind door 3 , contestant chose door 3 
    ## Try 873 - Prize is behind door 1 , contestant chose door 2 
    ## Try 874 - Prize is behind door 3 , contestant chose door 3 
    ## Try 875 - Prize is behind door 2 , contestant chose door 1 
    ## Try 876 - Prize is behind door 3 , contestant chose door 3 
    ## Try 877 - Prize is behind door 2 , contestant chose door 1 
    ## Try 878 - Prize is behind door 2 , contestant chose door 3 
    ## Try 879 - Prize is behind door 3 , contestant chose door 1 
    ## Try 880 - Prize is behind door 2 , contestant chose door 2 
    ## Try 881 - Prize is behind door 3 , contestant chose door 1 
    ## Try 882 - Prize is behind door 3 , contestant chose door 1 
    ## Try 883 - Prize is behind door 3 , contestant chose door 3 
    ## Try 884 - Prize is behind door 2 , contestant chose door 1 
    ## Try 885 - Prize is behind door 1 , contestant chose door 3 
    ## Try 886 - Prize is behind door 2 , contestant chose door 1 
    ## Try 887 - Prize is behind door 1 , contestant chose door 1 
    ## Try 888 - Prize is behind door 2 , contestant chose door 3 
    ## Try 889 - Prize is behind door 1 , contestant chose door 2 
    ## Try 890 - Prize is behind door 1 , contestant chose door 2 
    ## Try 891 - Prize is behind door 3 , contestant chose door 2 
    ## Try 892 - Prize is behind door 1 , contestant chose door 3 
    ## Try 893 - Prize is behind door 3 , contestant chose door 3 
    ## Try 894 - Prize is behind door 3 , contestant chose door 1 
    ## Try 895 - Prize is behind door 2 , contestant chose door 2 
    ## Try 896 - Prize is behind door 3 , contestant chose door 2 
    ## Try 897 - Prize is behind door 2 , contestant chose door 2 
    ## Try 898 - Prize is behind door 1 , contestant chose door 3 
    ## Try 899 - Prize is behind door 3 , contestant chose door 3 
    ## Try 900 - Prize is behind door 3 , contestant chose door 1 
    ## Try 901 - Prize is behind door 1 , contestant chose door 2 
    ## Try 902 - Prize is behind door 1 , contestant chose door 2 
    ## Try 903 - Prize is behind door 2 , contestant chose door 2 
    ## Try 904 - Prize is behind door 1 , contestant chose door 3 
    ## Try 905 - Prize is behind door 1 , contestant chose door 1 
    ## Try 906 - Prize is behind door 2 , contestant chose door 1 
    ## Try 907 - Prize is behind door 3 , contestant chose door 2 
    ## Try 908 - Prize is behind door 3 , contestant chose door 2 
    ## Try 909 - Prize is behind door 3 , contestant chose door 2 
    ## Try 910 - Prize is behind door 1 , contestant chose door 2 
    ## Try 911 - Prize is behind door 2 , contestant chose door 1 
    ## Try 912 - Prize is behind door 1 , contestant chose door 1 
    ## Try 913 - Prize is behind door 1 , contestant chose door 2 
    ## Try 914 - Prize is behind door 1 , contestant chose door 2 
    ## Try 915 - Prize is behind door 1 , contestant chose door 2 
    ## Try 916 - Prize is behind door 2 , contestant chose door 1 
    ## Try 917 - Prize is behind door 1 , contestant chose door 2 
    ## Try 918 - Prize is behind door 3 , contestant chose door 2 
    ## Try 919 - Prize is behind door 1 , contestant chose door 3 
    ## Try 920 - Prize is behind door 2 , contestant chose door 1 
    ## Try 921 - Prize is behind door 3 , contestant chose door 3 
    ## Try 922 - Prize is behind door 3 , contestant chose door 2 
    ## Try 923 - Prize is behind door 1 , contestant chose door 1 
    ## Try 924 - Prize is behind door 3 , contestant chose door 3 
    ## Try 925 - Prize is behind door 1 , contestant chose door 2 
    ## Try 926 - Prize is behind door 2 , contestant chose door 1 
    ## Try 927 - Prize is behind door 2 , contestant chose door 1 
    ## Try 928 - Prize is behind door 3 , contestant chose door 2 
    ## Try 929 - Prize is behind door 1 , contestant chose door 1 
    ## Try 930 - Prize is behind door 1 , contestant chose door 3 
    ## Try 931 - Prize is behind door 3 , contestant chose door 3 
    ## Try 932 - Prize is behind door 2 , contestant chose door 3 
    ## Try 933 - Prize is behind door 1 , contestant chose door 1 
    ## Try 934 - Prize is behind door 2 , contestant chose door 1 
    ## Try 935 - Prize is behind door 1 , contestant chose door 2 
    ## Try 936 - Prize is behind door 3 , contestant chose door 3 
    ## Try 937 - Prize is behind door 1 , contestant chose door 1 
    ## Try 938 - Prize is behind door 2 , contestant chose door 1 
    ## Try 939 - Prize is behind door 1 , contestant chose door 3 
    ## Try 940 - Prize is behind door 3 , contestant chose door 3 
    ## Try 941 - Prize is behind door 3 , contestant chose door 3 
    ## Try 942 - Prize is behind door 2 , contestant chose door 2 
    ## Try 943 - Prize is behind door 3 , contestant chose door 3 
    ## Try 944 - Prize is behind door 3 , contestant chose door 3 
    ## Try 945 - Prize is behind door 2 , contestant chose door 2 
    ## Try 946 - Prize is behind door 3 , contestant chose door 2 
    ## Try 947 - Prize is behind door 3 , contestant chose door 2 
    ## Try 948 - Prize is behind door 3 , contestant chose door 1 
    ## Try 949 - Prize is behind door 3 , contestant chose door 3 
    ## Try 950 - Prize is behind door 3 , contestant chose door 3 
    ## Try 951 - Prize is behind door 1 , contestant chose door 3 
    ## Try 952 - Prize is behind door 2 , contestant chose door 2 
    ## Try 953 - Prize is behind door 3 , contestant chose door 3 
    ## Try 954 - Prize is behind door 3 , contestant chose door 2 
    ## Try 955 - Prize is behind door 1 , contestant chose door 1 
    ## Try 956 - Prize is behind door 1 , contestant chose door 1 
    ## Try 957 - Prize is behind door 2 , contestant chose door 3 
    ## Try 958 - Prize is behind door 2 , contestant chose door 2 
    ## Try 959 - Prize is behind door 1 , contestant chose door 2 
    ## Try 960 - Prize is behind door 1 , contestant chose door 2 
    ## Try 961 - Prize is behind door 1 , contestant chose door 1 
    ## Try 962 - Prize is behind door 1 , contestant chose door 2 
    ## Try 963 - Prize is behind door 1 , contestant chose door 1 
    ## Try 964 - Prize is behind door 1 , contestant chose door 2 
    ## Try 965 - Prize is behind door 2 , contestant chose door 2 
    ## Try 966 - Prize is behind door 3 , contestant chose door 1 
    ## Try 967 - Prize is behind door 2 , contestant chose door 1 
    ## Try 968 - Prize is behind door 1 , contestant chose door 1 
    ## Try 969 - Prize is behind door 1 , contestant chose door 3 
    ## Try 970 - Prize is behind door 1 , contestant chose door 1 
    ## Try 971 - Prize is behind door 2 , contestant chose door 3 
    ## Try 972 - Prize is behind door 3 , contestant chose door 2 
    ## Try 973 - Prize is behind door 2 , contestant chose door 2 
    ## Try 974 - Prize is behind door 3 , contestant chose door 3 
    ## Try 975 - Prize is behind door 1 , contestant chose door 3 
    ## Try 976 - Prize is behind door 2 , contestant chose door 3 
    ## Try 977 - Prize is behind door 1 , contestant chose door 1 
    ## Try 978 - Prize is behind door 2 , contestant chose door 3 
    ## Try 979 - Prize is behind door 1 , contestant chose door 2 
    ## Try 980 - Prize is behind door 2 , contestant chose door 3 
    ## Try 981 - Prize is behind door 3 , contestant chose door 3 
    ## Try 982 - Prize is behind door 3 , contestant chose door 3 
    ## Try 983 - Prize is behind door 1 , contestant chose door 3 
    ## Try 984 - Prize is behind door 3 , contestant chose door 1 
    ## Try 985 - Prize is behind door 3 , contestant chose door 2 
    ## Try 986 - Prize is behind door 2 , contestant chose door 2 
    ## Try 987 - Prize is behind door 1 , contestant chose door 2 
    ## Try 988 - Prize is behind door 3 , contestant chose door 1 
    ## Try 989 - Prize is behind door 2 , contestant chose door 3 
    ## Try 990 - Prize is behind door 3 , contestant chose door 3 
    ## Try 991 - Prize is behind door 1 , contestant chose door 2 
    ## Try 992 - Prize is behind door 2 , contestant chose door 1 
    ## Try 993 - Prize is behind door 3 , contestant chose door 2 
    ## Try 994 - Prize is behind door 2 , contestant chose door 2 
    ## Try 995 - Prize is behind door 1 , contestant chose door 3 
    ## Try 996 - Prize is behind door 3 , contestant chose door 3 
    ## Try 997 - Prize is behind door 2 , contestant chose door 3 
    ## Try 998 - Prize is behind door 2 , contestant chose door 2 
    ## Try 999 - Prize is behind door 2 , contestant chose door 2 
    ## Try 1000 - Prize is behind door 2 , contestant chose door 2

``` r
cat("Staying with the original choice, the contestant wins",
    correct, "out of", tries, "tries.\n")
```

    ## Staying with the original choice, the contestant wins 328 out of 1000 tries.

``` r
# Second strategy: switch to the other door
correct <- 0
for (i in 1:tries) {
  prize <- sample(1:3, 1) # Randomly place the car behind one of the doors
  choice <- sample(1:3, 1) # Contestant makes an initial choice

  open_door <- setdiff(1:3, c(prize, choice)) # Host opens a door with a goat
  switch_choice <-
    setdiff(1:3, c(choice, open_door[1])) # The other unopened door

  if (verbose) {
    cat("Try", i,
        " - Prize is behind door", prize,
        ", contestant chose door", choice,
        ", host opened door", open_door[1],
        ", contestant switches to door", switch_choice, "\n")
  }

  if (switch_choice == prize) {
    correct <- correct + 1 # Contestant wins if they switch to the other door
  }
}
```

    ## Try 1  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 2  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 3  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 4  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 5  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 6  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 7  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 8  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 9  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 10  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 11  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 12  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 13  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 14  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 15  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 16  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 17  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 18  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 19  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 20  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 21  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 22  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 23  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 24  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 25  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 26  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 27  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 28  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 29  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 30  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 31  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 32  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 33  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 34  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 35  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 36  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 37  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 38  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 39  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 40  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 41  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 42  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 43  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 44  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 45  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 46  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 47  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 48  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 49  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 50  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 51  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 52  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 53  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 54  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 55  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 56  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 57  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 58  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 59  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 60  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 61  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 62  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 63  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 64  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 65  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 66  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 67  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 68  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 69  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 70  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 71  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 72  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 73  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 74  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 75  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 76  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 77  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 78  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 79  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 80  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 81  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 82  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 83  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 84  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 85  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 86  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 87  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 88  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 89  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 90  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 91  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 92  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 93  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 94  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 95  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 96  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 97  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 98  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 99  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 100  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 101  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 102  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 103  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 104  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 105  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 106  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 107  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 108  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 109  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 110  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 111  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 112  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 113  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 114  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 115  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 116  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 117  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 118  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 119  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 120  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 121  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 122  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 123  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 124  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 125  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 126  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 127  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 128  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 129  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 130  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 131  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 132  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 133  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 134  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 135  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 136  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 137  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 138  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 139  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 140  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 141  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 142  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 143  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 144  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 145  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 146  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 147  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 148  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 149  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 150  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 151  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 152  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 153  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 154  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 155  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 156  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 157  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 158  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 159  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 160  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 161  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 162  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 163  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 164  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 165  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 166  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 167  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 168  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 169  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 170  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 171  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 172  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 173  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 174  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 175  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 176  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 177  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 178  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 179  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 180  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 181  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 182  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 183  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 184  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 185  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 186  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 187  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 188  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 189  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 190  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 191  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 192  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 193  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 194  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 195  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 196  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 197  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 198  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 199  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 200  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 201  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 202  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 203  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 204  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 205  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 206  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 207  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 208  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 209  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 210  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 211  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 212  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 213  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 214  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 215  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 216  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 217  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 218  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 219  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 220  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 221  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 222  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 223  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 224  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 225  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 226  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 227  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 228  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 229  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 230  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 231  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 232  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 233  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 234  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 235  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 236  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 237  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 238  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 239  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 240  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 241  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 242  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 243  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 244  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 245  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 246  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 247  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 248  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 249  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 250  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 251  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 252  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 253  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 254  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 255  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 256  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 257  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 258  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 259  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 260  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 261  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 262  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 263  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 264  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 265  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 266  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 267  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 268  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 269  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 270  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 271  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 272  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 273  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 274  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 275  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 276  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 277  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 278  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 279  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 280  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 281  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 282  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 283  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 284  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 285  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 286  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 287  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 288  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 289  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 290  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 291  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 292  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 293  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 294  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 295  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 296  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 297  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 298  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 299  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 300  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 301  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 302  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 303  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 304  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 305  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 306  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 307  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 308  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 309  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 310  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 311  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 312  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 313  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 314  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 315  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 316  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 317  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 318  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 319  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 320  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 321  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 322  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 323  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 324  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 325  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 326  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 327  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 328  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 329  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 330  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 331  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 332  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 333  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 334  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 335  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 336  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 337  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 338  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 339  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 340  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 341  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 342  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 343  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 344  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 345  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 346  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 347  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 348  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 349  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 350  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 351  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 352  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 353  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 354  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 355  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 356  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 357  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 358  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 359  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 360  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 361  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 362  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 363  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 364  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 365  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 366  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 367  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 368  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 369  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 370  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 371  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 372  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 373  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 374  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 375  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 376  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 377  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 378  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 379  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 380  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 381  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 382  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 383  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 384  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 385  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 386  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 387  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 388  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 389  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 390  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 391  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 392  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 393  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 394  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 395  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 396  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 397  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 398  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 399  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 400  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 401  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 402  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 403  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 404  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 405  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 406  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 407  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 408  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 409  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 410  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 411  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 412  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 413  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 414  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 415  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 416  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 417  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 418  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 419  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 420  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 421  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 422  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 423  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 424  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 425  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 426  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 427  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 428  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 429  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 430  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 431  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 432  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 433  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 434  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 435  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 436  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 437  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 438  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 439  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 440  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 441  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 442  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 443  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 444  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 445  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 446  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 447  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 448  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 449  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 450  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 451  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 452  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 453  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 454  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 455  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 456  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 457  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 458  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 459  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 460  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 461  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 462  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 463  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 464  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 465  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 466  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 467  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 468  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 469  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 470  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 471  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 472  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 473  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 474  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 475  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 476  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 477  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 478  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 479  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 480  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 481  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 482  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 483  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 484  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 485  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 486  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 487  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 488  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 489  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 490  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 491  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 492  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 493  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 494  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 495  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 496  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 497  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 498  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 499  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 500  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 501  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 502  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 503  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 504  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 505  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 506  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 507  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 508  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 509  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 510  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 511  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 512  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 513  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 514  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 515  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 516  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 517  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 518  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 519  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 520  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 521  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 522  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 523  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 524  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 525  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 526  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 527  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 528  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 529  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 530  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 531  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 532  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 533  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 534  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 535  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 536  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 537  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 538  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 539  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 540  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 541  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 542  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 543  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 544  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 545  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 546  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 547  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 548  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 549  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 550  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 551  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 552  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 553  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 554  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 555  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 556  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 557  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 558  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 559  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 560  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 561  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 562  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 563  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 564  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 565  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 566  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 567  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 568  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 569  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 570  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 571  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 572  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 573  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 574  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 575  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 576  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 577  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 578  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 579  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 580  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 581  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 582  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 583  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 584  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 585  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 586  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 587  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 588  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 589  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 590  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 591  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 592  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 593  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 594  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 595  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 596  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 597  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 598  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 599  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 600  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 601  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 602  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 603  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 604  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 605  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 606  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 607  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 608  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 609  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 610  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 611  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 612  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 613  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 614  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 615  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 616  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 617  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 618  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 619  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 620  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 621  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 622  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 623  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 624  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 625  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 626  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 627  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 628  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 629  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 630  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 631  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 632  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 633  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 634  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 635  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 636  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 637  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 638  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 639  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 640  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 641  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 642  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 643  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 644  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 645  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 646  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 647  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 648  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 649  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 650  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 651  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 652  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 653  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 654  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 655  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 656  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 657  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 658  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 659  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 660  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 661  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 662  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 663  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 664  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 665  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 666  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 667  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 668  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 669  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 670  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 671  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 672  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 673  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 674  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 675  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 676  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 677  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 678  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 679  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 680  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 681  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 682  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 683  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 684  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 685  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 686  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 687  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 688  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 689  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 690  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 691  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 692  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 693  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 694  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 695  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 696  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 697  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 698  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 699  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 700  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 701  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 702  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 703  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 704  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 705  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 706  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 707  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 708  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 709  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 710  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 711  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 712  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 713  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 714  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 715  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 716  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 717  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 718  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 719  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 720  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 721  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 722  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 723  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 724  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 725  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 726  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 727  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 728  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 729  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 730  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 731  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 732  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 733  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 734  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 735  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 736  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 737  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 738  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 739  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 740  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 741  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 742  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 743  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 744  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 745  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 746  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 747  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 748  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 749  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 750  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 751  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 752  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 753  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 754  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 755  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 756  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 757  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 758  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 759  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 760  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 761  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 762  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 763  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 764  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 765  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 766  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 767  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 768  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 769  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 770  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 771  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 772  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 773  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 774  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 775  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 776  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 777  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 778  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 779  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 780  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 781  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 782  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 783  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 784  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 785  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 786  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 787  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 788  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 789  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 790  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 791  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 792  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 793  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 794  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 795  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 796  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 797  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 798  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 799  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 800  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 801  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 802  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 803  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 804  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 805  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 806  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 807  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 808  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 809  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 810  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 811  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 812  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 813  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 814  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 815  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 816  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 817  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 818  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 819  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 820  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 821  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 822  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 823  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 824  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 825  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 826  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 827  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 828  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 829  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 830  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 831  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 832  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 833  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 834  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 835  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 836  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 837  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 838  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 839  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 840  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 841  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 842  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 843  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 844  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 845  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 846  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 847  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 848  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 849  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 850  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 851  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 852  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 853  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 854  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 855  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 856  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 857  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 858  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 859  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 860  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 861  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 862  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 863  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 864  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 865  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 866  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 867  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 868  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 869  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 870  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 871  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 872  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 873  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 874  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 875  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 876  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 877  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 878  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 879  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 880  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 881  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 882  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 883  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 884  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 885  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 886  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 887  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 888  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 889  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 890  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 891  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 892  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 893  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 894  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 895  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 896  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 897  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 898  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 899  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 900  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 901  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 902  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 903  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 904  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 905  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 906  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 907  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 908  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 909  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 910  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 911  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 912  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 913  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 914  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 915  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 916  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 917  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 918  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 919  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 920  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 921  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 922  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 923  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 924  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 925  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 926  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 927  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 928  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 929  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 930  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 931  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 932  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 933  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 934  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 935  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 936  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 937  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 938  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 939  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 940  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 941  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 942  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 943  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 944  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 945  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 946  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 947  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 948  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 949  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 950  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 951  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 952  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 953  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 954  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 955  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 956  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 957  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 958  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 959  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 960  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 961  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 962  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 963  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 964  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 965  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 966  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 967  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 968  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 969  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 970  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 971  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 972  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 973  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 974  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 975  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 976  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 977  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 978  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 979  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 980  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 981  - Prize is behind door 3 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 982  - Prize is behind door 2 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 983  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 984  - Prize is behind door 2 , contestant chose door 1 , host opened door 3 , contestant switches to door 2 
    ## Try 985  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 986  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 987  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 988  - Prize is behind door 3 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 989  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 990  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 991  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 992  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 993  - Prize is behind door 1 , contestant chose door 3 , host opened door 2 , contestant switches to door 1 
    ## Try 994  - Prize is behind door 3 , contestant chose door 2 , host opened door 1 , contestant switches to door 3 
    ## Try 995  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 996  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 997  - Prize is behind door 1 , contestant chose door 2 , host opened door 3 , contestant switches to door 1 
    ## Try 998  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3 
    ## Try 999  - Prize is behind door 2 , contestant chose door 3 , host opened door 1 , contestant switches to door 2 
    ## Try 1000  - Prize is behind door 1 , contestant chose door 1 , host opened door 2 , contestant switches to door 3

``` r
cat("Switching to the other door, the contestant wins",
    correct, "out of", tries, "tries.\n")
```

    ## Switching to the other door, the contestant wins 639 out of 1000 tries.

# Conclusion

The Monty Hall problem demonstrates that switching doors increases the
probability of winning from 1/3 to 2/3. This counterintuitive result
highlights the importance of understanding conditional probability and
the impact of additional information on decision-making.

### Always switch doors!

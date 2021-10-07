- 👋 Hi, I’m @arjun123412
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
arjun123412/arjun123412 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->




## using numeric input

wts_in <- c(13.12, 1.49, 0.16, -0.11, -0.19, -0.16, 0.56, -0.52, 0.81)
struct <- c(2, 2, 1) #two inputs, two hidden, one output 

olden(wts_in, struct)

## using nnet

library(nnet)

data(neuraldat) 
set.seed(123)

mod <- nnet(Y1 ~ X1 + X2 + X3, data = neuraldat, size = 5)
#> # weights:  26
#> initial  value 259.012592 
#> iter  10 value 0.986480
#> iter  20 value 0.225311
#> iter  30 value 0.139585
#> iter  40 value 0.098961
#> iter  50 value 0.038200
#> iter  60 value 0.022839
#> iter  70 value 0.013774
#> iter  80 value 0.008530
#> iter  90 value 0.005172
#> iter 100 value 0.003044
#> final  value 0.003044 
#> stopped after 100 iterations 
olden(mod)  

if (FALSE) {
## View the difference for a model w/ skip layers

set.seed(123)

mod <- nnet(Y1 ~ X1 + X2 + X3, data = neuraldat, size = 5, skip = TRUE)

olden(mod)

## using RSNNS, no bias layers

library(RSNNS)

x <- neuraldat[, c('X1', 'X2', 'X3')]
y <- neuraldat[, 'Y1']
mod <- mlp(x, y, size = 5)

olden(mod)

## using neuralnet

library(neuralnet)

mod <- neuralnet(Y1 ~ X1 + X2 + X3, data = neuraldat, hidden = 5)

olden(mod)

## using caret

library(caret)

mod <- train(Y1 ~ X1 + X2 + X3, method = 'nnet', data = neuraldat, linout = TRUE)

olden(mod)

## multiple hidden layers

x <- neuraldat[, c('X1', 'X2', 'X3')]
y <- neuraldat[, 'Y1']
mod <- mlp(x, y, size = c(5, 7, 6), linOut = TRUE)

olden(mod)
}

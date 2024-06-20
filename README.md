# Analyzing Investment Returns with Monte Carlo Simulations
# The Problem
You have \$1,000 now and need to pay \$1,050 in one year. You have available to you two assets: a risk free asset that returns 3%, and a stock that returns 10% with a 20% standard deviation. How much should you invest in the two assets to maximize your probability of having at least \$1,050 in one year?

# The Basic Model
You should first build the model which handles a single set of inputs to produce a single set of outputs. Once that is working correctly, then you can run Monte Carlo simulations using the model.

In this model, we will want to build it for a given return for each of the assets. Then later we can bring in the standard deviations by drawing the returns from normal distributions in the simulations.

# Portfolio Returns
We need to determine the returns on the portfolio. It matters what weights we have invested in each of the assets, as well as each of the asset's returns.

This is just a one period model, so the portfolio return is 𝑟𝑝=𝑟𝑟𝑓𝑤𝑟𝑓+𝑟𝑠𝑤𝑠

This can be simplified even further. There are only two assets, and we will be fully invested, so 𝑤𝑟𝑓+𝑤𝑠=1, therefore 𝑤𝑟𝑓=1−𝑤𝑠 and we can just eliminate the 𝑤𝑟𝑓, yielding:

𝑟𝑝=𝑟𝑟𝑓(1−𝑤𝑠)+𝑟𝑠𝑤𝑠

# Monte Carlo Simulations
So now we know that if we earn 10% on the stock and invest 50% in it, we will have enough money. We also know if it returns only 5%, it's not going to be enough to meet our required $1,050. But we don't know anything about the probability of having enough money.

To run a Monte Carlo simulation, all we do is assign distributions as necessary to any inputs, then run the model a bunch of times, drawing inputs from the distributions, passing them into the model, and collecting the outputs.

# Draw Inputs From Distributions
So here, we are only concerned with assigning the stock return to a distribution. We will not vary the risk free rate as it has a standard deviation of zero, so it would always be the same value anyway. We will not vary the weight as that is a decision variable. We will not vary the inital portfolio value as it shouldn't change.

We will assume that the stock's returns are normally distributed. Let's try to pull a single return from the normal distribution for this stock.

# Collect the Outputs
All we need to do here is run the above steps in a loop, appending the result to a list each time we run the model. This is especially simple because we only have one output from the model. If you have multiple outputs from a single run of your model, you will have to use some other data structure, such as multiple lists, a list of lists, a list of dictionaries, or a DataFrame.

# Visualize
Usually a first good way to analyze the outputs is to visualize them. Let's plot the results. A histogram or KDE plot is usually most appropriate for visualizing a single output. The KDE is basically a smoothed out histogram.


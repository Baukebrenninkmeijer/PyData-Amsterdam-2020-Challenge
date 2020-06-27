# Solution Pydata Amsterdam 2020 Challenge: Vector optimization with noisy loss of an unknown function using evolutionary algorithms

This repo contains my solution for the PyData Amsterdam 2020 challenge that was organized. Please have a look at the notebook, it should contain everything that is required to understand my solution. 

The PyData challenge was about finding a secret vector. This was done by you, the user, sending a vector to an API, which would calculate the distance between your vector and the secret vector and give this back to you. It quickly became clear that there were some tricks going on that made the challenge significantly harder to do. The two main challengers were:

the distance received was very noisy
there were many local minima (this only became clear to me after the challenge ended, unfortunately).
Since I had not picked up on any of the clues that might have been there indicating what kind of function we were dealing with, I decided to use a naive optimization approach using evolutionary algorithms. In short, evalutionary algorithms consist of a population of numerous individuals that have some sort of 'genes'. In optimization, these genes are changed and evaluated over and over again, while keeping the stronger candidates. In the end, you should get individuals that are very close to the target.

In my solution, the individuals were called Numbers (yes, very not confusing, I know) and the population was called Swarm. The swarm as a whole optimizes itself, by removing unfit individuals. To score my individuals, I chose to interpret their noise as something that might be or might not be gaussian. So I did several calls for each vector to get a score and kept track of both the minimum and mean of those scores. I tried optimizing for both, but optimizing for the minimum turned out to converge much faster and also resulted in better scores (in the same number of steps at least). Maybe, the mean approach requires different optimization parameters (different mutation ratio, due to lower variance in the mean). This notebook only goes through the minimum optimization, but it requires only changing a couple of lines to make it mean optimization.

If you have any questions or interest, please reach out.

Thanks to @Vincent for organizing the challenge and the whole PyData team for a cool event!
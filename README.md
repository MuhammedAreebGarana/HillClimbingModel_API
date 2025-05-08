# HillClimbingModel_API
We are trying to optimize (minimize) memory usage of an API by tweaking its configuration parameters.
This project implements a hill climbing search algorithm guided by a trained regression model to find the API configuration that results in the lowest memory usage — without the need to exhaustively test every combination.

🔧 Configuration Parameters
Each configuration defines how the API behaves and impacts memory usage:

batch_size: Amount of data processed at once

cache_ttl: Time-to-live for cached responses

thread_pool_size: Number of threads handling concurrent requests

compression_enabled: Whether response compression is used (reduces memory, increases CPU)

🔍 How It Works
Step-by-Step:
Start with a random configuration
Example: batch_size=64, cache_ttl=30, thread_pool_size=8, compression_enabled=True

Use a regression model (e.g., Random Forest) to predict memory usage for a given config.

Generate neighboring configurations

Modify one parameter at a time (e.g., increase batch_size, disable compression, etc.)

Evaluate all neighbors

Predict memory usage for each using the trained model

Move to the best neighbor

Select the neighbor with the lowest predicted memory usage

Repeat

Continue until no neighbor offers improvement (i.e., local minimum is found)

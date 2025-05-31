## Deploy ML Model as API for Inference with R Plumber
### Requirements
1. R and RStudio
2. Plumber package
3. Docker
4. Visual Studio Code
5. Docker Hub online account (optional)

### Prelude: Try Plumber
1. Create a new Plumber API file.
2. Write two API functions: 
  * One that takes a pair of random number sets (rnorm(100)) to generate a scatterplot at API endpoint '/scatter'.
  * One that takes weight and height as inputs to compute bmi at API endpoint '/bmi'.
3. Execute the Plumber API file.
4. Test the APIs.

Reference script: [try_plumber.R](src/try_plumber.R)

### Step 1: Train and Save Model
Train and save a model that predicts the price of a used car.  
Reference script: [used_car_price_model.R](src/used_car_price_model.R)

### Step 2: Design and Develop Inference API
Using Plumber, create a function that takes features/covariates as input parameters, loads the trained model and output predicted price at API endpoint '/api/v1/used-car/price'.

Reference script: [deploy_noYAML.R](src/deploy_noYAML.R)

### Step 3: Test API with Swagger UI
Create a wrapper R script that runs the Plumber API with a user-defined port. Test the response of the API.

Reference script: [plumber_deploy_noYAML.R](src/plumber_deploy_noYAML.R)

### Step 4: Serving Predictions from Docker
Start Docker engine.  

Next, in command prompt or terminal, navigate to the project directory that contains Dockerfile.  

Build the docker image using:
```
docker build -t dssi-plumber-docker:1.0 .
```

After the building the image, start an application container:
```
docker run --rm -d -p 80:8000/tcp dssi-plumber-docker:1.0
```
Verify whether the container is running:
```
docker ps
```


# Cinematic Serendipity: Unveiling Movie Magic with FastAI
🎬✨ "How's that Movie?" - A Cinematic Odyssey with Collaborative Filtering and FastAI

Welcome to a cinematic journey where 10 lines of code open the doors to an enchanting world of movie recommendations. In the realm of recommender systems, where algorithms shape our digital experiences, we unveil the artistry of collaborative filtering with a touch of FastAI wizardry.

## The Essence of Collaborative Filtering
Picture this: users with kindred cinematic spirits, influencing each other's preferences. Collaborative filtering, the maestro behind the scenes, orchestrates predictions based on shared opinions. Our twist? We're dancing with neural collaborative filtering, a modern muse in the vast landscape of recommender systems.

## Unveiling the MovieLens 100K Dataset
Our canvas is the MovieLens 100K dataset, an anthology of 100,000 movie ratings from 943 users on 1682 movies. Each user and movie, a protagonist with a unique numeric ID. Ratings, the storytellers, range from 1 to 5. Our quest? Craft a model that foretells a user's rating for an unseen movie, guided by the echoes of users with akin tastes.

## Theatrics of System Setup
To embark on this cinematic soiree, follow the script below:

bash
Copy code
pip install jovian --upgrade     # Install the jovian library 
jovian clone 5bc23520933b4cc187cfe18e5dd7e2ed # Download notebook
cd movielens-fastai              # Enter the created directory 
jovian install                   # Install the dependencies
conda activate movielens-fastai  # Activate virtual environment
jupyter notebook                 # Start Jupyter
Or, if you seek instant immersion, click "Run on Binder" for a front-row seat in the Jupyter auditorium.

## Crafting the Collaborative Symphony
In our model, users and movies take center stage as vectors of elegance. Their pas de deux, a dot product, predicts movie ratings. But there's an encore! We introduce bias terms for the dramatic outliers and an exquisite sigmoid touch for a refined denouement.

python
Copy code
learn = collab_learner(data, n_factors=40, y_range=[0,5.5], wd=.1)
## Rehearsing the Model
Training unfolds seamlessly with the FastAI repertoire. Let the learning rate finder set the stage, and a mere 5 epochs later, witness the mean squared error bowing to around 0.80, achieving a state-of-the-art crescendo.

python
Copy code
learn.fit_one_cycle(5, 0.01)
Spectacle of Predictions
Enough of the rehearsals; let's shine the spotlight on real predictions!

python
Copy code
(users, items), ratings = next(iter(data.valid_dl))
preds = learn.model(users, items)
print('Real\tPred\tDifference')
for p in list(zip(ratings, preds))[:16]:
    print('{}\t{:.1f}\t{:.1f}'.format(p[0],p[1],p[1]-p[0]))
Marvel at the predictions, dancing in harmony with actual ratings. Now, let this model serenade you with recommendations that echo your cinematic soul. 🌟🎥

User
summarize to give an overview
ChatGPT
Cinematic Harmony: FastAI-Powered Movie Recommendations
🚀 Overview

Embark on a cinematic journey with "How's that Movie?" – a collaborative filtering masterpiece powered by FastAI. In just 10 lines of code, we unravel the magic of movie recommendations, blending the classic charm of collaborative filtering with the sophistication of modern neural collaborative filtering.

## 🎭 The Essence of Collaborative Filtering

At the heart of our adventure is collaborative filtering, where users with shared tastes influence predictions. Imagine a dance of opinions shaping recommendations, enhanced by the contemporary flair of neural collaborative filtering.

## 🎬 Unveiling the MovieLens 100K Dataset

Our stage is set with the MovieLens 100K dataset – a tapestry of 100,000 ratings from 943 users on 1682 movies. Each user and movie has a unique numeric ID, and ratings paint the canvas from 1 to 5. Our mission? Craft a model predicting user ratings for unseen movies, guided by the whispers of kindred cinematic spirits.

## 🛠️ Theatrics of System Setup

Prepare for the grand show by following a simple script. Install the jovian library, clone the notebook, activate the virtual environment, and let Jupyter be your gateway to cinematic enchantment.

### bash
Copy code
pip install jovian --upgrade
jovian clone 5bc23520933b4cc187cfe18e5dd7e2ed
cd movielens-fastai
jovian install
conda activate movielens-fastai
jupyter notebook
Or, for instant immersion, click "Run on Binder" and join the Jupyter auditorium.

🎭 Crafting the Collaborative Symphony

In our model, users and movies take the stage as elegant vectors. A dot product between them predicts movie ratings, enriched by bias terms for outliers and a Sigmoid touch for a refined denouement.

python
Copy code
learn = collab_learner(data, n_factors=40, y_range=[0,5.5], wd=.1)
🚀 Rehearsing the Model

Training unfolds seamlessly with the FastAI repertoire. Let the learning rate finder set the stage, and witness the mean squared error bowing to around 0.80 after just 5 epochs.

python
Copy code
learn.fit_one_cycle(5, 0.01)
🌟 Spectacle of Predictions

Marvel at the predictions – a dance in harmony with actual ratings. Let this model serenade you with recommendations that echo your cinematic soul.

python
Copy code
(users, items), ratings = next(iter(data.valid_dl))
preds = learn.model(users, items)
print('Real\tPred\tDifference')
for p in list(zip(ratings, preds))[:16]:
    print('{}\t{:.1f}\t{:.1f}'.format(p[0],p[1],p[1]-p[0]))
Now, let the magic of personalized movie recommendations unfold before your eyes. 🌟🎥

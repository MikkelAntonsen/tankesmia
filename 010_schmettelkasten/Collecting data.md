## Data
## How much data do you need?
This question is impossible to answer without knowing what we're trying to achieve. WIthout a clear goal. It's still impossible possibly if you have a clearly defined goal.
You can somewhat estimate how much you would need to add to get a certain performance on your current validation set, but does the current validation set represent production conditions?
Adding data to the validation/test set  is just as important as adding to the train set.


## What data do we need?
Managers will tend to ask how much data we need because they want to allocate resources for annotation and setting up timelines. An other question is `what data do we need?`.

### Training data
We need data to train our model and evaluate it after training. It's easy to say what training data we need. It's what ever data makes the validation and test scores go up.
The test and train set need to reflect what we expect to see out in the world.

### Validation and test data
Problem: The Validation and test set only represent the world as we have seen it yet. This is similar to cyber security, the best case you can hope for is being on par with your adversary. You can't prepare for what they've got up in their sleeve.

When your first model is deployed, you have data that represents the situation as it was when you collected the data. 

Transient phenomena:
	- Jellyfish
	- Debris
	- Sharks
	- Whales
	- Wild fish

Seasonal phenomena:
	- Melting water
	- Fish size
	- Light conditions

Hardware/software issues (autogain, threading on windows)
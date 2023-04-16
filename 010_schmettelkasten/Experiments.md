### Data quality test

Checkpoint: /home/mikkel/workspace/Produce101/outputs/2023-02-13/12-53-41
Trained on full quality jpeg

Checkpoint: /home/mikkel/workspace/Produce101/outputs/2023-02-13/10-53-02

reposet_multiprocessing er høy kvalitet, reposet_async er sequences kvalitet


Trent på sequence quality jpeg
Big jpeg - mp
small jpg - async

| f1  |  async  |  multiprocessing |
|---|---|---|
| async  | 0.7043  | 0.7055 |
| multiprocessing  | 0.6969  | 0.6969 |

| prec  |  async  |  multiprocessing |
|---|---|---|
| async  | 0.7822 |  0.7871 |
| multiprocessing  | 0.7783 |  0.7753 |

| recall |  async  |  multiprocessing |
|---|---|---|
| async  | 0.64 | 0.6392 |
| multiprocessing  | 0.6310  |  0.6296 |


## New louse detector


### chestnut-snail

Name: 2023-02-28/22-54-04
Description: Run with only hflip transform

###  defiant-wildebeest

Name: 2023-03-01/01-27-15
Description: Run with all transforms

Grad2 norms die as the network starts overfitting?
Starts overfitting a lot more than [[#chestnut-snail]] for some reason?
How does it overfit while gradients are going low?


### strange-tarsier

Name: 2023-03-01/08-22-21
Description: Run without empty images in the training set and only hflip transform

### real-butterfly

Name: 2023-03-01/10-34-35
Description: Run without empty images in the training set and only hflip + pixel dropout(0.5) as transforms. This lead to better val set performance than [[#strange-tarsier]]

### delightful-guan

Name: 2023-03-01/15-00-27
Description: Same as [[#real-butterfly]] except gt box min radius has been hard coded to 8.
This increased F1/Recall but annihilated precision. This should maybe be looked into visually. It might not be a big deal since train set is beyond borked wrt labeling standard compared to validation set.

### daft-myna
Name: 2023-03-01/17-35-43
Description: same as [[#delightful-guan]] but radius is set to 16 instead of 8. Also moved reposet to ssd to check if faster than 2.2 hours.

### cuddly-cricket
Name: 2023-03-01/21-06-50

Same as [[#delightful-guan]] and [[#daft-myna]] except radius is 4.
Gava results Prec=0.570, recall=0.269, f1=0.365

### certain-fossa
Name: 2023-03-02/13-37-59

Same as [[#cuddly-cricket]] but half scale images.
Prec=0.517, recall=0.196, f1=0.284

### hopping-pogona
Name: 2023-03-05/00-04-25

Same as [[#certain-fossa]] but (most importantly) randomresizedcrop makes the images 1024x1024 instead of quartersize which was a bug and save rotate limit went from 20 to 30.

### nocturnal-axolotl

Name: 2023-03-06/07-48-19
Same as [[#hopping-pogona]] but see if specifying border_mode for shiftscalerotate leads to better error (since lice won't be reflected (not not annotated!)).








|   | Infer All Lice  | Infer AF  | 
|---|---|---|
|  Eval all lice | Prec=0.582, recall=0.177, f1=0.271  |  Prec=0.606, recall=0.120, f1=0.200
| Eval AF  | Prec=0.381, recall=0.188, f1=0.251 | Prec=0.484, recall=0.155, f1=0.234

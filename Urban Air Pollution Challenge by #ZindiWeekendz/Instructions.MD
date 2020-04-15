## Instructions for running.

1. Run the notebooks from zindi-weekendz-pollution-v1.ipynb to zindi-weekendz-pollution-v4.ipynb to generate the output submission files for each of them.
2. Change the data path from '/kaggle/input' to where the files are stored in your local machine.
3. Finally run the notebook zindi-weekendz-pollution-blend.ipynb, to generate the final output file, **submission.csv**

##Approach

Only the first notebook **zindi-weekendz-pollution-v1.ipynb** has comments added, because all the notebooks are almost same.

The idea was simply to use future and past values to predict the future, along with the current readings. If you see the feature importances you will see that future and past values are indeed important. Some kinds of features that were added were:

1. Past and previous values of target for arbitary number of days, which you can experiment.
2. Past and previous values of sensor readings for arbitary number of days.
3. Extracting information from the date column about weekday, month, is_month_start or is_month_end.
4. Adding cyclic features because of the cyclic behaviour of time, consider this Monday repeats after every 7 days. Sunday is just before Monday, but while doing encoding we would encode Sunday as 6, and Monday as 0. Adding cyclic features help eliminate some of this problem.
5. Adding frequency encoding for **place_ID** since some place_IDs had different number of occurences in the data compared to others, I added a feature to capture it.

The final model was a blended version of 4 different lightGBM models I created, weights were adjusted to ensure optimal performance on the leaderboard.



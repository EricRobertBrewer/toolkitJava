# Java Toolkit

A toolkit for running basic machine learning algorithms.

## Running

```bash
javac *.java
java MLSystemManager -L <learning-algorithm> -A <training-set-filename.arff> -E <evaluation-method> [-V] [-N]
```

Learning algorithms (`-L`):

- `baseline` A non-algorithm which simply guesses the most common label for every feature set seen during training.
- `perceptron` A perceptron.

Training set files (`-A`) are similar to .csv files with the extension `.arff`.

Evaluation methods (`-E`):

- `static <test-set-filename.arff>` Specify the name of another `.arff` file with which to test. Example using a separate test data set: `-E static abalone-test.arff`
- `random <percent>` Test against a random subset of the given training set. Example using 25% of the given data set for testing (and 75% of the same set for training): `-E random 0.25`
- `cross <folds>` Cross-validate against the training set `folds` number of times, then compute the average accuracy of each validation. Example of 10-fold cross-validation: `-E cross 10`
- `training` Test directly against the entire training set. Example: `-E training`

Other options:

- `-V` Verbose. Print the confusion matrix and learner accuracy.
- `-N` Normalize. Normalize the given training set (and test set if the evalutation method is `static`) to values between 0 and 1.

Example:
```bash
java MLSystemManager -L perceptron -A ../datasets/iris.arff -E random .3 -N
```

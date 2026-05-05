# Analysis-of-different-variants-in-CNN-classifier
This project analyses the following variants of CNN classifiers:<br>
1. Variants with full data:<br>
i) Baseline CNN<br>
ii) CNN with data augmentation<br>
iii) CNN with Self Supervised Learning<br>
2. Variants with 1,5,10 and 20 shots learning with self supervised learning

## Background
**Data Augmentation**: A machine learning technique used to artificially increase the size and diversity of training datasets by creating modified versions of existing data.<br>
**Self-supervised learning**: Self-supervised learning (SSL) is a machine learning approach in which models generate their own supervisory signals from raw data rather than relying on human-provided labels. It bridges supervised and unsupervised learning, enabling systems to exploit vast unlabeled datasets efficiently and learn transferable data representations for downstream tasks.The model is trained using a pretask. Then, the trained model is used for training with input data. There are 2 approaches:<br>
i. *Fine tuning*: The trained SSL model is fine tuned with input data.<br>
ii. *Freeze*: The SSL model is not tuned. Only the classifier part is trained with input data.<br>
**Few-shot learning**:Few-shot learning is a machine learning paradigm designed to enable models to learn new concepts or tasks from only a small number of labeled examples. It addresses the challenge of data scarcity by leveraging prior knowledge or meta-learning to generalize effectively from limited supervision. The goal is to generalize from few labeled samples. Typical sample size: 1–10 examples per class.

## Experiment setup
1. Input data: CIFAR 10 dataset - a foundational machine learning dataset consisting of 60,000 32x32 color images across 10 distinct classes, with 6000 images per class. It is divided into 50,000 training images and 10,000 test images. It has images of 10 classes, which are as follows:Airplane, Automobile, Bird, Cat, Deer, Dog, Frog, Horse, Ship, Truck.<br>
2. Track 1: Compairing Baseline CNN, CNN with data augmentation and CNN with SSL <br>
  i. 20% of training data is set aside for validation <br>
  ii. Data agmentation is done by flipping, rotating, zooming etc <br>
  iii. The pretask for SSL model is image rotation. The model is trained with 10000 rotated samples from training data <br>
  iv. The trained SSL model is used for training the classifer in fine tuning and freeze modes. <br>
3. Track 2: Analysing SSL with 1 shot, 5 shot, 10 shot and 20 shot learning
   i. n shot -> n samples per class <br>
   ii. Since number of training samples is less, no data is set aside for validation <br>
   iii. The SSL model trained before is used. <br>

## Result and Interpretations
### Track 1
<img width="1638" height="748" alt="Screenshot (5014)" src="https://github.com/user-attachments/assets/650db1c0-1f81-4dec-b10e-c9b525533fd6" />
<br> In terms of accuracy, Baseline CNN performs the best. SSL CNN may be underperforming because the pretask chosen (rotation) is not powerful enough. Trraining time is the least for SSL CCN with freeze, as only the classifier is trained and tuned.

### Track 2
<img width="1667" height="742" alt="Screenshot (5015)" src="https://github.com/user-attachments/assets/34ef65ad-ba7a-477c-b71e-59343a5d358b" />
<br> Overall accuracy is less than baseline CNN. As number of samples increases, the accuracy also increases. Also, fine tuning works better that freeze, especially when number of data samples is more.




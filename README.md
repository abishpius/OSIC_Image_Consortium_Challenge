
 
MODELING IDIOPATHIC PULMONARY FIBROSIS INDUCED LUNG FUNCTION DECLINE


Nicholas Kshatri1, Kamaru-Deen Lawal2, Abish Pius2

1University of Pittsburgh Swanson School of Engineering, Pittsburgh, PA
2University of Pittsburgh School of Medicine, Pittsburgh, PA

 
ABSTRACT
Idiopathic Pulmonary Fibrosis (IPF) is a restrictive, inflammation driven lung disorder with little known progression and no known cure. Even clinicians are baffled by its pathophysiology and often express distress in predicting its progression, thus resulting in imperfect treatment options for patients. In this study, we used data from patients with IPF provided by the Open Source Image Consortium (OSIC) to design a model to help physicians estimate the progression of the disease. Using the PyTorch library, we created a six-layer convolutional neural network that predicts lung function forced vital capacity (FVC) with a mean squared error of 6763.
Keywords: Idiopathic Pulmonary Fibrosis (IPF), CT Scans, Image Processing, Machine Learning, CNN, PyTorch

1.	INTRODUCTION
IPF is a rare, incurable lung disease that affects primarily middle-aged adults (50+ years) [1]. Though its prevalence is on the order of a handful per 100,000 people, the economic burden upon the hospital is critical, as the average stay is roughly ~40 days and often unnecessary treatments or tests are ordered [1,2]. The disease pathophysiology is marked by shallow, labored breathing (dyspnea) as well as scarring or stiffening of the lung parenchyma [3,4]. 
In patients, IPF is diagnosed most commonly using histopathology which requires surgical procedures on an anesthetized patient at great cost to both the patient and the hospital [5]. Other less common diagnostic options include CT scans and spirometry readings, such as forced vital capacity (FVC) or the amount of air that can be forcibly expelled from the lung with a higher FVC corresponding to healthier lung function [3]. Both tools show great promise amidst advancements in computer vision technology [6].
Current treatment of IPF varies depending on the expected progression by clinicians, ranging from simple anti-inflammatory agents to lung transplantation [7]. However, with current diagnostic reasoning and tools, physicians report difficulty in estimating a patient’s disease progression, resulting in both unsuccessful therapies and increased patient anxiety [8]. In this study, we use modern advancements in convolutional neural networks (CNNs) libraries to construct a model correlating patient lung CT scans to their corresponding spirometry FVC readings thereby providing physicians with a greater sense of their patients’ lung health and in turn improving patient outcomes.

2.	MATERIALS AND METHODS
Images (~1500 out of 30000) in DICOM format were obtained from the Open Source Image Consortium’s (OSIC) [9] dataset of patients’ lung CT scans and spirometry results. Sample CT images from male and female patients were visualized using Paraview 5.8.1. Pydicom library was used to load the images and the dataset was split into 80% training and 20% validation data. Image data of size 512x512 was floating point normalized between 0 and 1 and only the middle reference image was used across patients. The PyTorch library was used to create a four-layer CNN with max-pooling and two fully connected layers containing 200 neurons and 100 neurons respectively with ReLU activation. The model was trained using a CPU for 50 epochs, using two-fold cross validation and evaluated using mean-squared error and log loss.

3.	RESULTS AND DISCUSSION
From roughly 150 randomly selected patients from the entirety of the databank, we visualized 3D volume renderings of DICOM images from a handful of patients with different conditions in Paraview. Visually IPF is rather hard to discern from CT images (Figure 1) as the patient with IPF seems to have less lung volume in their right lobe. Furthermore, lung size also varied across patients and surprisingly, the utilized CT scans had no obvious traits betraying individuals who smoked.
 FIGURE 1: NON IPF vs IPF LUNG CT SCANS

 
FIGURE 2: PATIENT DATA DISTRIBUTION FEATURES

Investigating our patient data, we have a wide range of FVC scores with a drastic difference in scores between males and females (Figure 2A,B). This difference is expected due to physiologic differences among the sexes and is an important feature to incorporate into the model. Furthermore, the dataset provided details on smoking status of the individuals and interestingly smokers have, on average, higher FVC scores than non-smokers irrespective of sex (Figure 2C). This is concerning for clinicians as it may indicate that FVC is a poor measure of healthy lung function.

 
FIGURE 3: MODEL PERFORMANCE 

Due to the limited data size we decided to create just a training and validation split. The constructed model consists of one convolutional layer with padded 3x3 convolutions and a max-pooling layer followed by two fully connected layers with ReLU activation functions. After training for 50 epochs with two-fold cross-validation, the model achieved a log-cosh loss around 130 and a mean square error (MSE) of around 6700 on the training set (Figure 3A). Its performance on the validation set was slightly worse, with early epoch plateaus at an MSE of 6775 and a log loss of 150.
The model’s performance could be improved with more data as only a limited amount of OSIC patient data was used in the interest of computational power. Furthermore, it would be beneficial to integrate additional features, such as the patient sex and even smoking status, in the model as it is currently only dependent upon image features. Finally, the model may also be improved with the implementation of more convolutional layers with different convolutions, again this was not investigated further in the interest of computational power.

4.	CONCLUSION
Through this project we demonstrated our understanding of DICOM formatted CT image files in developing a machine learning solution to a medically relevant problem. We used CNNs on patients’ lung CT scans to predict lung function FVC score with a MSE of around 6800 on unseen data. In the future, we hope to translate this product into a functioning app to be used in the clinic.

ACKNOWLEDGEMENTS
Dr. Prahlad Menon Gopalakrishna, University of Pittsburgh Swanson School of Engineering

REFERENCES
[1] Raghu, G., Weycker, D., Edelsberg, J., Bradford, W. Z., & Oster, G. (2006). Incidence and prevalence of idiopathic pulmonary fibrosis. American journal of respiratory and critical care medicine, 174(7), 810-816.
[2] Raghu, G. (2017). Epidemiology, survival, incidence and prevalence of idiopathic pulmonary fibrosis in the USA and Canada. European Respiratory Journal, 49(1).
[3] Gross, Thomas J., and Gary W. Hunninghake. "Idiopathic pulmonary fibrosis." New England Journal of Medicine 345.7 (2001): 517-525.
[4] Thannickal, Victor J., et al. "Mechanisms of pulmonary fibrosis." Annu. Rev. Med. 55 (2004): 395-417.
[5] Lynch, David A., et al. "High-resolution computed tomography in idiopathic pulmonary fibrosis: diagnosis and prognosis." American journal of respiratory and critical care medicine 172.4 (2005): 488-493.
[6] Jacob, J., Bartholmai, B. J., Rajagopalan, S., Kokosi, M., Nair, A., Karwoski, R., ... & Hansell, D. M. (2016). Automated quantitative computed tomography versus visual computed tomography scoring in idiopathic pulmonary fibrosis. Journal of thoracic imaging, 31(5), 304-311.
[7] Du Bois, R. M. "Strategies for treating idiopathic pulmonary fibrosis." Nature reviews Drug discovery 9.2 (2010): 129-140.
[8] Karimi-Shah, Banu A., and Badrul A. Chowdhury. "Forced vital capacity in idiopathic pulmonary fibrosis–FDA review of pirfenidone and nintedanib." N Engl J Med 372.13 (2015): 1189-1191.
[9] OSICild.org • Open Source Imaging Consortium, www.osicild.org/.



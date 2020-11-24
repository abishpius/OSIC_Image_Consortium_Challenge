# OSIC_Image_Consortium_Challenge
Using Pytorch Model to predict Pulmonary Fibrosis Progression

### Title: Modeling lung function decline in Pulmonary Fibrosis <br>
**Background:** Idiopathic Pulmonary Fibrosis is a restrictive, inflammation driven lung disorder with little known progression and no known cure [1]. The disease pathophysiology is marked by shallow, labored breathing (dyspnea) as well as scarring or stiffening of the lung parenchyma [2,3]. In patients, diagnosis is often made histopathologically requiring patients be placed under general anesthesia, though newer methods using CT and spirometry are growing in popularity [4]. Treatment strategies include anti-inflammatory agents, corticosteroids, and even lung transplantation depending on the progression of the disease, an area that is less well studied [5]. Interestingly, clinicians report patient anxiety as a direct result of this inability to discern the future impact of the disease’s progression [6]. Here modern advancements in computer vision can aide in bridging the gap in predicting how lung function will progress on the individual patient level thereby helping clinicians understand the disease and better explain expected outcomes to patients. <br>
**Aims:** We aim to model a patients’ severity of decline in lung function given a CT scan of their lung. <br>
Approach: Using the Open Source Image Consortium (OSIC) [7] dataset of patients’ lung CT scans and spirometry results we propose to model the severity of expected lung function decline. Lung function will be evaluated using the patient spirometry’s recorded Forced Vital Capacity (FVC), or the maximum amount of air a person can voluntarily expel from their lungs, with a higher FVC correlating to stronger lung function [8]. We will split our dataset of ~34000 DICOM format CT scan images and CSV format spirometer results into training, validation and testing splits of 50%, 20%, and 30% respectively. Utilizing a convolutional neural network, we will predict FVC values from lung CT scans and evaluate our model using mean squared error and log likelihood ratios. <br>
**Possible Pitfalls:** Given the size of the dataset, constructing deep neural networks will be computationally expensive and may require access to GPUs. In such an event, we will restrict the size of the dataset and proceed with the process. <br>

<br>
**References:** <br>
1.	King Jr, Talmadge E., Annie Pardo, and Moisés Selman. "Idiopathic pulmonary fibrosis." The Lancet 378.9807 (2011): 1949-1961.
2.	Gross, Thomas J., and Gary W. Hunninghake. "Idiopathic pulmonary fibrosis." New England Journal of Medicine 345.7 (2001): 517-525.
3.	Thannickal, Victor J., et al. "Mechanisms of pulmonary fibrosis." Annu. Rev. Med. 55 (2004): 395-417.
4.	Lynch, David A., et al. "High-resolution computed tomography in idiopathic pulmonary fibrosis: diagnosis and prognosis." American journal of respiratory and critical care medicine 172.4 (2005): 488-493.
5.	Du Bois, R. M. "Strategies for treating idiopathic pulmonary fibrosis." Nature reviews Drug discovery 9.2 (2010): 129-140.
6.	Lee, Ye Jin, et al. "Clinical impact of depression and anxiety in patients with idiopathic pulmonary fibrosis." PLoS One 12.9 (2017): e0184300.
7.	OSICild.org • Open Source Imaging Consortium, www.osicild.org/.
8.	Karimi-Shah, Banu A., and Badrul A. Chowdhury. "Forced vital capacity in idiopathic pulmonary fibrosis–FDA review of pirfenidone and nintedanib." N Engl J Med 372.13 (2015): 1189-1191.

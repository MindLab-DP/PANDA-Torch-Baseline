# Prostate cANcer graDe Assessment (PANDA) Challenge Baseline | EfficientNet-B0 | 256 x 256 Tiling

## About the challenge

With more than 1 million new diagnoses reported every year, prostate cancer (PCa) is the second most common cancer among males worldwide that results in more than 350,000 deaths annually. The key to decreasing mortality is developing more precise diagnostics. Diagnosis of PCa is based on the grading of prostate tissue biopsies. These tissue samples are examined by a pathologist and scored according to the Gleason grading system. In this challenge, you will develop models for detecting PCa on images of prostate tissue samples, and estimate severity of the disease using the most extensive multi-center dataset on Gleason grading yet available.
The grading process consists of finding and classifying cancer tissue into so-called Gleason patterns (3, 4, or 5) based on the architectural growth patterns of the tumor. After the biopsy is assigned a Gleason score, it is converted into an ISUP grade on a 1-5 scale. The Gleason grading system is the most important prognostic marker for PCa, and the ISUP grade has a crucial role when deciding how a patient should be treated. There is both a risk of missing cancers and a large risk of overgrading resulting in unnecessary treatment. However, the system suffers from significant inter-observer variability between pathologists, limiting its usefulness for individual patients. This variability in ratings could lead to unnecessary treatment, or worse, missing a severe diagnosis.
Automated deep learning systems have shown some promise in accurately grading PCa. Recent research, including two studies independently conducted by the groups hosting this challenge, have shown that these systems can achieve pathologist-level performance. However, these systems/results were not tested with multi-center datasets at scale.

The training set consists of around 11,000 whole-slide images of digitized H&E-stained biopsies originating from two centers. This is the largest public whole-slide image dataset available, roughly 8 times the size of the CAMELYON17 challenge, one of the largest digital pathology datasets and best known challenges in the field. Furthermore, in contrast to previous challenges, we are making full diagnostic biopsy images available. Using a sizable multi-center test set, graded by expert uro-pathologists, we will evaluate challenge submissions on their applicability to improve this critical diagnostic function.


## Digital pathology
Many fundamental aspects of pathology as a medical discipline have remained largely unchanged for decades, but the field is currently undergoing a transition into a digital discipline. In digital pathology, microscopy slides containing tissue samples are scanned into whole slide images (WSI). These high-resolution images are then analyzed computationally instead of the conventional approach of visually evaluating the slides under a microscope. Among other benefits, digital pathology unlocks the possibility of applying computational methods on the resulting data, most notably image analysis techniques based on artificial intelligence (AI) and machine learning. For more information on digital and computational pathology, see e.g. (Bera, 2019) or (Niazi, 2019).

### Gleason patterns
Each WSI in this challenge contains one, or in some cases two, thin tissue sections cut from a single biopsy sample. Prior to scanning, the tissue is stained with haematoxylin & eosin (H&E). This is a standard way of staining the originally transparent tissue to produce some contrast. The samples are made up of glandular tissue and connective tissue. The glands are hollow structures, which can be seen as white “holes” or branched cavities in the WSI. The appearance of the glands forms the basis of the Gleason grading system. The glandular structure characteristic of healthy prostate tissue is progressively lost with increasing grade. The grading system recognizes three categories: 3, 4, and 5. The patterns are described in detail below and exemplified in Fig. 2:

A. Benign prostate glands with folded epithelium. The cytoplasm is pale and the nuclei small and regular. The glands are grouped together.
B. Prostatic adenocarcinoma - Gleason Pattern 3 has no loss of glandular differentiation. Small glands infiltrate between benign glands. The cytoplasm is often dark and the nuclei enlarged with dark chromatin and some prominent nucleoli. Each epithelial unit is separate and has a lumen.
C. Prostatic adenocarcinoma - Gleason Pattern 4 has partial loss of glandular differentiation. There is an attempt to form lumina but the tumor fails to form complete, well-developed glands. This microphotograph shows irregular cribriform cancer, i.e. epithelial sheets with multiple lumina. There are also some poorly formed small glands and some fused glands. All of these are included in Gleason Pattern 4.
D. Prostatic adenocarcinoma - Gleason Pattern 5 has an almost complete loss of glandular differentiation. Dispersed single cancer cells are seen in the stroma. Gleason Pattern 5 may also contain solid sheets or strands of cancer cells. All microphotographs show hematoxylin and eosin stains at 20x lens magnification.





### ISUP grade

The patterns present in a single biopsy are used to form a Gleason score, e.g. 4 + 3 = 7. To simplify slightly, in the case of multiple different Gleason patterns being present, the score is composed of the most frequently occurring pattern and the second most frequent pattern in the biopsy, as judged by the pathologist. The minority pattern must account for at least 5% of the total area to be included, e.g. if pattern 3 is less than 5%, the Gleason score 4 + 3 will instead be 4 + 4. Further, the highest grade should always be part of the score. For example, a biopsy that contains 60% Gleason 4, 37% Gleason 3 and 3% Gleason 5 should get a score of 4 + 5 = 9. For details see (Epstein, 2016).

According to current guidelines by the International Society of Urological Pathology (ISUP), the Gleason scores are summarized into an ISUP grade on a scale from 1 to 5 according to the following rule:

Gleason score 6 = ISUP grade 1 
Gleason score 7 (3 + 4) = ISUP grade 2 
Gleason score 7 (4 + 3) = ISUP grade 3 
Gleason score 8 = ISUP grade 4 
Gleason score 9-10 = ISUP grade 5.

If there is no cancer in the sample, we use the label ISUP grade 0 in this competition. 

Your task in the challenge is to provide the correct ISUP grade for each biopsy, with correctness measured against the grades assigned by pathologists. One should note that there is considerable variation in the ISUP grades assigned by different pathologists even for the same biopsy, which leads to noise also in the labels provided for the data in this challenge. We have therefore invited several international expert pathologists to each label the test data, and from that derived a consensus label. See for example (Egevad, 2013) for more information on inter-pathologist variation in Gleason grading.

### Computational Gleason grading.
For recent reports on performing Gleason grading of biopsies automatically based on AI, see e.g. (Ström & Kartasalo, 2020) and (Bulten, 2020) or the corresponding freely available pre-print versions at https://arxiv.org/abs/1907.01368 and https://arxiv.org/abs/1907.07980.

### References

Bera et al., 2019. Artificial intelligence in digital pathology—new tools for diagnosis and precision oncology. Nature Reviews Clinical Oncology, 16(11), 703-715.

Bulten et al., 2020. Automated deep-learning system for Gleason grading of prostate cancer using biopsies: a diagnostic study. The Lancet Oncology.

Egevad et al., 2013. Standardization of Gleason grading among 337 European pathologists. Histopathology, 62(2), 247-256. 

Epstein et al, 2016. The 2014 International Society of Urological Pathology (ISUP) consensus conference on gleason grading of prostatic carcinoma definition of grading patterns and proposal for a new grading system. Am J Surg Pathol; 40: 244–52. 

Niazi et al., 2019. Digital pathology and artificial intelligence. The Lancet Oncology, 20(5), e253-e261. 

Ström & Kartasalo et al., 2020. Artificial intelligence for diagnosis and grading of prostate cancer in biopsies: a population-based, diagnostic study. The Lancet Oncology.

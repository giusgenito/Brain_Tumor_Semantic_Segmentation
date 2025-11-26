# Brain Tumor Semantic Segmentation con U-Net 🧠

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-ee4c2c)
![Computer Vision](https://img.shields.io/badge/Task-Semantic%20Segmentation-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📋 Descrizione del Progetto

Questo progetto implementa un'architettura **U-Net** da zero utilizzando **PyTorch** per eseguire la segmentazione semantica su immagini di risonanza magnetica (MRI) cerebrale. L'obiettivo è identificare e segmentare automaticamente le regioni affette da tumore, classificando ogni pixel dell'immagine.

Il progetto è stato sviluppato come elaborato finale per l'esame di **Deep Learning** presso l'**Università di Liegi (Belgio)**, durante il mio periodo di studio Erasmus nel corso di Laurea Magistrale in Informatica.


## 🚀 Caratteristiche Principali

* **Architettura U-Net Personalizzata**: Implementazione manuale della rete U-Net con encoder (contracting path) e decoder (expanding path).
* **Componenti Avanzati**: Utilizzo di `GroupNorm` invece di BatchNorm per una migliore stabilità su batch size ridotti e funzione di attivazione `LeakyReLU`.
* **Training Loop Robusto**: Implementazione di Early Stopping, Learning Rate Scheduler (`ReduceLROnPlateau`) e salvataggio del miglior modello.
* **Metriche di Valutazione**: Monitoraggio della Loss (BCEWithLogitsLoss) e del **Dice Coefficient** per valutare la qualità della segmentazione.
* **Data Pipeline**: Pipeline di pre-processing personalizzata con trasformazioni e normalizzazione delle immagini.

## 🛠️ Tecnologie Utilizzate

* **Linguaggio**: Python
* **Framework DL**: PyTorch, Torchvision
* **Librerie**: NumPy, OpenCV (cv2), Matplotlib, Scikit-Image, PIL
* **Ambiente**: Google Colab / Jupyter Notebook

## 🧠 Architettura del Modello

Il modello utilizzato è una variante della classica **U-Net**, progettata specificamente per la segmentazione biomedica.

* **Encoder**: 5 blocchi convoluzionali che estraggono le feature gerarchiche, riducendo la dimensione spaziale e aumentando la profondità dei canali (fino a 1024).
* **Bottleneck**: Il punto più profondo della rete che connette l'encoder al decoder.
* **Decoder**: 5 blocchi di upsampling che ricostruiscono la dimensione originale dell'immagine, concatenando le feature map dell'encoder (Skip Connections) per preservare i dettagli spaziali.
* **Output**: Un singolo canale con attivazione sigmoidea (implicita nella Loss) per la maschera binaria del tumore.


## 📂 Struttura del Dataset

Il codice si aspetta un dataset organizzato nelle seguenti cartelle per training, validation e test:

```text
/dataset
    /train
        /images
        /masks
    /valid
        /images
        /masks

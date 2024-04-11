# MoonLabs
The task

Background
<br> An online marketplace specialising in jewellery crafted by independent makers is looking to enhance its platform with AI technology. The marketplace aims to streamline the process for artisans to list their products by automatically generating detailed product descriptions and specifications based on images uploaded by the makers. This system is intended to reduce the time and effort required for artisans to create listings, improve the consistency and quality of product information across the platform, and enhance the shopping experience for customers.

Task
<br> Outline how you would go about developing and deploying an AI system capable of analysing jewellery images to accurately generate product information, including materials, design attributes, and potential categorizations. Be specific about what technologies you would use, and how you would use them to solve the problem. If required, your plan may contain diagrams and code snippets to illustrate your solution

Your plan may assume that the company has a large amount of existing data, consisting of images stored in cloud object storage, and associated descriptions and other labels being held in a relational database.




# Aim
To develop an AI system capable of analyzing jewellery images and generating detailed product information, including materials, design attributes, and categorizations. This will be achieved by using Computer Vision and Natural Language Processing techniques.


# Proposed Solution

The below solution will be developed using the Python programming language due to its ease of use.

1. Collate data to build an accurate dataset:

  - Build a datatset by extracting images from the cloud object storage and associated descriptions and labels from the relational database using SQL (PostgreSQL, MySQL,     SQLite).
  -  Process the data to ensure it is representative of various types of jewellery, materials, designs and styles.
  -  Speak to someone with Jewellery design if possible while curating/pre-processing the dataset.
  -  Look at additonal data sources to provide richer context.

2. Image augmentations

 -  Resize and normalise images to help improve trainning speeds and convergence.
  -  Write data preprocessing functions and data loader functions to perform augmentations (such as rotation, color change etc.) to the images using the albumentations library for augmentations and pytorch data class.


3. Model Selection :

  -  The model pipeline will be using CNNs along with  a transformer model to output the required text.


 - Extract Features using CNN:
   -  Utilize a pre-trained CNN model (e.g., VGG, ResNet) for feature extraction from jewelry images using PyTorch.
   -  Remove the classification head of the CNN model, keeping the feature extraction layers intact.
   -  Pass the jewelry images through the CNN model to obtain high-level feature representations (numercial feature vector).
   -  Retrieve the output of the penultimate layer.


 - Text Generation with Transformer:
   - Use a transformer-based model such as BERT, GPT etc for text generation using Pytorch and HuggingFace.


4.Model Architecture:

 - Design a unified architecture where the image features from the CNN serve as input to the transformer model.
 - Concatenate or merge the image features with positional encodings and pass them through the transformer layers for text generation.
 - Train the entire architecture end-to-end to jointly learn the mapping from images to textual descriptions including materials, design attributes, and categorizations .

5.Training Procedure

 - Select a suitable loss function such as cross entropy loss and optimizer such as Adam using scikit-learn. 
 - Use cross validation techniques using Scikit-Learn.
 - Perfrom hyperparameter tuning.


6.Evaluation and validation

 - Use metrics like ROUGE score, BLEU score etc to evaluate the model using available libraries.


7.Deployment:

 - Once the models are trained and evaluated satisfactorily, deploy them in a production environment through cloud services such as AWS, Azure, and GCP.
 - Utilize containerization technologies like Docker for packaging the models and deploying them as microservices.
 - Implement RESTful APIs to expose the model functionalities for inference using FastAPI or Flask.

8.Monitoring & Feedback

 - Implement logging and monitoring processes to track performance of the system.
 - Establish a feedback loop where artisans can provide feedback on the generated product information (to improve the models). 

# Additonal notes:
 - Alternate approach: Please note that instead of a transformer a RNN such as LSTM or GRU can also be used.
 - The reason for using pre-trained models is because it helps accelerate development however fine tuning can be computationally expensive.


# Additional Considerations:

 - Ethics and Bias: Ensure the models are free from bias and ethical concerns, especially regarding the representation of jewellery from different cultures and styles.
 - Legal and Privacy: Discuss any legal or privacy concerns related to handling data and generated content, especially regarding intellectual property and customer privacy.








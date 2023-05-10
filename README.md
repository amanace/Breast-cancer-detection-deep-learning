# Breast-cancer-detection-deep-learning
Breast-cancer-detection-deep-learning

Breast histopathology is a medical field that involves the diagnosis and treatment of breast diseases
by analyzing breast tissue samples. The diagnosis is made by examining the tissue samples under a
microscope to identify the presence or absence of certain abnormalities.
In recent years, the use of artificial intelligence and machine learning techniques has become more
prevalent in this field. With the help of these techniques, it is now possible to automate the analysis
of breast tissue samples and improve the accuracy and speed of the diagnosis. The background of
our project focuses on Invasive ductal carcinoma (IDC), also known as infiltrating ductal carcinoma. It
is cancer that begins growing in a milk duct and has invaded the fibrous or fatty tissue of the breast
outside of the duct. Invasive means that the cancer has “invaded” or spread to the surrounding
breast tissues. Ductal means that the cancer began in the milk ducts, which are the “pipes” that
carry milk from the milk-producing lobules to outside. Carcinoma refers to any cancer that begins in
the skin or other tissues that cover internal organs, such as breast tissue. Over time, invasive ductal
carcinoma can spread to the lymph nodes and possibly to other areas of the body. IDC starts in the
cells that line a milk duct in the breast, breaks through the wall of the duct, and grows into the
nearby breast tissues. At this point, it may be able to spread (metastasize) to other parts of the body
through the lymph system and bloodstream. According to the American Cancer Society, about twothirds of women are 55 or older when they are diagnosed with invasive breast cancer.
The problem that arises with this is that more women are diagnosed with breast cancer than any
other cancer, besides skin cancer and As with any breast cancer, there may be no signs or
symptoms. Invasive ductal carcinoma is the most common form of invasive breast cancer and
represents 80 percent of these cases.
A mammogram may reveal a suspicious mass, which will lead to further testing including biopsies,
which involve taking out some or all of the abnormal-looking tissue for examination by a pathologist
. Histopathology, on the other hand, is the microscopic examination of breast tissue samples that
have been surgically removed or obtained through a biopsy. The tissue is examined by a pathologist
who analyzes the structure and composition of the tissue to diagnose or rule out breast cancer or
other breast diseases. Basically it can provide a more definitive diagnosis, but it requires a tissue
sample and a trained pathologist to interpret the results.
Our dataset is a breast histopathology image dataset provided by Kaggle.
The dataset consists of 162 whole mount slide images of Breast Cancer (BCa) specimens scanned at
40x.
From that, 383171 patches of size 50 x 50 were extracted (191577 IDC negative and 191594 IDC
positive).
Our idea is to feed These pictures into an algorithm which would be able to classify whether invasive
ductal carcinoma is present in an image.
First part of our model building is to prepare data for processing.
We started by importing all the required libraries and installed Kaggle API by running !pip install
Kaggle.The next three lines create a directory called .kaggle in the user's home directory and copy a
Kaggle API token called kaggle.json into this directory. Finally, download the required dataset.
We then create a directory named all_images_dir using the os.mkdir function. The first line sets the
variable all_images_dir equal to the string 'all_images_dir', which is the name of the directory that
will be created. The next three lines create two subdirectories inside all_images_dir using the
os.mkdir function again. This creates a subdirectory named 1 inside all_images_dir, while the other
line creates a subdirectory named 0. 1 and 0 directories store images of malignant and benign tissue
samples
We want to create a dataframe for the image information. This code is used to create two pandas
DataFrames (df_data_1 and df_data_0) from lists of image filenames in two separate directories
(all_images_dir/1 and all_images_dir/0) and then combine them into a single DataFrame (df_data).
The first two lines of code function to get lists of all the files in all_images_dir/1 and
all_images_dir/0 directories, respectively. These lists are assigned to image_list_1 and image_list_0.
The next two lines of code create two pandas DataFrames (df_data_1 and df_data_0) from these
lists of image filenames. The pd.concat() function concatenates DataFrames along a particular axis
(in this case, the default axis of 0, which corresponds to stacking DataFrames vertically)
For these following functions.The extract_patient_id function takes a string as input (x) and splits it
using the underscore symbol (_) as a separator. It then selects the first element of the resulting list
and assigns it to a variable named patient_id. The function returns the patient_id. The extract_target
function also takes a string as input (x) and splits it using the underscore symbol (_) as a separator. It
then selects the fifth element of the resulting and then the sixth character of that element and
assigns it to a variable named target. The function returns the target. Results are assigned to new
columns named patient_id and target, respectively.
Here, we split the data into 3 parts. a training set, a validation set, and a test set. Then, the
train_test_split function is called twice on the df_data data frame with different values for the
test_size parameter. The test_size parameter determines the proportion of the data that should be
allocated to the test and validation sets. The random_state parameter is set to 42 to ensure that the
splits are reproducible. The stratify parameter is set to y to ensure that the distribution of target
values in the test and validation sets is similar to that in the original data frame.
The use of this function is that the function takes a single argument (x) which is a value from the
image_id column of the df_data data frame. It first creates two lists of image_id values from the
df_val and df_test data frames. Then, it checks if the x value is in either of those lists. Pertaining to
whatever result It is then added in the dataframe. The same process is repeated to create val_dir
and test_dir directories.After this subdirectories for the different classes of images are created. In
this case, two classes are present: class 1 and class 0. Basically this code sets up the directory
structure necessary for organizing the image data into training, validation, and test sets for further
processing.
In this we copy the images from their original directories into the new directories created earlier
(train_dir, val_dir, and test_dir) based on their respective data splits (training, validation, and
testing).
This code block is simply printing out some statistics about the data split across the training,
validation, and test sets.
Here we create augmented images from the images in the "train_dir/1" directory. Augmentation is a
technique used to increase the size of the training data by applying different transformations to the
images. It helps to reduce overfitting and improve the performance of the model.

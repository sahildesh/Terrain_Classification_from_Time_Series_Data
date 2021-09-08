Team No-20

There are two files submitted:
    
    1.ProjC-DAug_and_Training--->This file deals with the different types of data Augmentation that we have tried
                                     combined with different models that we have tried for training and saving the model.
    
    2.ProjC_Predictions---->This file deals with just loading the model and making predictions and converting the predictions to csv file 
                              to be uploaded to Gradescope


ProjC-DAug_and_Training::
        
    @libs-->
           a)For matrix and data operations-Numpy and Pandas
           b)Sklearn.metrics and sklearn.modelSelection-For F1 score, classificationreport and train_test_split
           c)Keras/tensorflow.keras- for model layers and model training
           d)Warnings-To post warnings to user
           e)Google.collab -To mount google drive

    @Class Utility
        @Func1- def Create_time_windows()-The function divides the data into time windows in float64/float128 default format .
                The concept is referenced from Jason Brownlee's book.

        @Func2-def Create_time_windows_opt_float()-The function divides the data into time windows in float32 default format .
                The concept is referenced from Jason Brownlee's book. It is just the optimization of the previous function.

        @Func3-def plot history()-utility function to plot training and validation curves of the model.

        @Func4-Select_training_type()-This function creates a user interface where the user can choose which data augmentation to choose
                                        A1, A2, and B for the model training.

    @Class Data_Augmentation
        @Func1-> def type1()-This is an A1 type of Data augmentation as shown in the report where the max of 3 and min of 1 data is equally distributed for each subject
                                and is sent to the model for training.
        @Func--->Def type2()---> This is A2 or brute force data where all the data of the subjects are trained
    As we will see in the later report Training on the fly (type  B) and Type A1 gives the best results while A2 overfits the data


    @Class Select_Model();
        @Func1-Create_Lstm_Dropout_model--One lstm and one dropout followed by two dense layers.

        @Func2-Create_Model_BatchNorm--One Lstm ,1 BatchNorm 2 dense---Final model used the highest prediction on Gradesope 85.8

        @Func3-Create_CNN_GRU()--2 Conv1d,2 BatchNorm,2 GRU,1 dropout,1 dense--->Gave promising results, and GRU is used instead of LSTM for faster training.

        @Func4-Model_RNN_LSTM()-1 SimpeleRNN,1 Dropout,1 Dense followed by LSTM and dropout, flatten and dense-->Referred from Team 22's report but the model was overfitting because our method data augmentation was different.


        @Func5-Model_CNN_1D()-2 Conv1d Followed by1 lstm divided by 1 batch norm layer-Model not giving proper final predictions

        @Func6-Create_Model_BatchNorm_BILSTM()-1 Bi-direction LSTM followed by 1 LSTM ,1 Batchnorm followed by 2 dense layers-Model overfits

        @Func7-Shreedhar_LSTM_2_Model()-->1 lstm,1 dropout, and 2 dense --->Model experimented by teammate shreedhar gave quite promising results.

        @Func8-Select_model_for_Training-->Creates a user interface where the user can select a model to train the data (Only for type 1 and Type2) for type 3 shreedhar_model_LSTM_2_Dropout() is the default.


    @Main_Function-def main()-Trains the model and gets plots
            training_type==1-->A1 augmentation and user can select any model to train
            training_type==2-->A2 augmentation and user can select any model to train
            training_type==3--> B augmentation where each subjects data is trained individually on the shreedhar_lstm2_Dropout_model() the user cannot select anyother model for this.




ProjC_Predictions::
    
    This file loads the save model and does prediction snd plots histograms and finally saves .csv file for predictions of each subject

    @libs-Same as ProjectC1_DAug_and_Training.ipynb

    @func1-Create_X_training()-Prepares the data for testing same as we did for training fo each subject, path given manually fo each subject
    @func2-Create_time_windows()-Before feeding to the model the test data also need to be divided into timewindows

@Conclusion::

        We trained 7 models with 3 different data augmentation techniques. This code can be scaled up for more models and augmentation types.
        Final Augtype-A1 model
        Final Model-Create_Model_BatchNorm
        Promising models-CNN_GRU and LSTM2_Dropout()
        Promising augmentation-B should be giving a better result but due to some bugs maybe we got a better result with A1
    
    
            
                            

# ilcm-integration
the following explains how to upload a self-trained Tibetan language model can be integrated into the iLCM. 
## Preliminaries:

1.	Download the Docker application.
2.	Pull the iLCM’s Docker distribution with the command line prompt ```docker pull ckahmann/ilcm```.
3.	Run ```docker run -it -d -p 3838:3838 -p 8787:8787 -p 8983:8983 ckahmann/ilcm:latest``` in the command line. 
4.	Make sure the SpaCy model is saved in the same environment/directory location as the Docker container.

## Copying and Unpacking:

5.	Copy file from accessible folder into running Docker container using the following command, all one line:

    - ```docker cp path/to/model/<model>.tar.gz <docker_container_name>:/home/rstudio/<model>.tar.gz```

6.	Note: ```docker_container_name``` is usually the last container listed in the docker interface. 

7.	Unpack the model from within the docker environment. 

	-	Open the rStudio interface from within the iLCM
  
	-	In the lower left section of the rstudio interface, change from “console” to “terminal” and input the following command, all on one line: ```/home/rstudio/miniconda3/bin/pip3 install /home/rstudio/<model>.tar.gz```

8.	Ensure that the stopword list is loaded into the iLCM. Using the docker cp command, load a file like ```stopwords.txt``` into the ```rstudio/collections/blacklists``` directory, like this:
   
	-    ```docker cp path/to/stopwords.txt docker_container_name:/home/rstudio/collections/blacklists```

9. Select the custom stopword list in the graphical interface ```task scheduler```. 

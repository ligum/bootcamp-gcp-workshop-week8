![image](https://bootcamp.rhinops.io/images/gcp-intro.gif)
![image](https://lh5.googleusercontent.com/ADfJF_U_oq2WG9CUoQmolanuI213d3AsWx1kuKeFqhHfS4s1n1O9BYTPT31MfzPRt7FEDHe3zhFhBdBQznnZlsyYDanb8FgMZZvKRO06GCuk047FicM-XuWbXpHlnmCAmPy2R54G)
GCP Cloud Main Services - Project


Introduction

This week we will learn about the possibilities that opened up with the world of cloud computing. For this, we will use GCP to get started on using "serverless" technologies.
 

Description

In this project, you will create two Cloud Functions that when invoked via HTTP will display an “Hello World” message and an image of the Go gopher.


Project Target

![image](https://lh5.googleusercontent.com/eYAYg3Yyr8DQSeEuokBryuttDA2CmNIIkdG5r3MEUslWCsOl3v2mGxnqCymkKnX06NtX6MJaTkJaT9dy64GzJu98c9jdUu4SASLR3G3tkcMQ9xuPFaGlobCiKkVGqmjqYv0334h1)


Project Tasks Summary

Access cloud shell in the web console
Download and setup the code
Creating the HTTP “Hello World” Cloud Function
Creating the HTTP “Gopher” Cloud Function

Tasks Details

1) Access cloud shell in the web console

In the Cloud Console, in the top right toolbar, click the Activate Cloud Shell button.
![image](https://lh6.googleusercontent.com/mEI06doXzSVQVVedk_DzFzxG5o-Ii6XoMINoJ0tArSJMGhdz7cSE_xmbwY-5j3a18hYM-7ebYtH621fnkh8Jv3HktZhwD_dDa-ciVAT58ADCvKlb_wqMKiK3Py8Uxu4N40cw1npy)
![image](https://lh6.googleusercontent.com/7c7zi_8rvxaihu6tWK2CWxMk3CN8bDOfU9pgM51t_TDGhMcSZbvrX0ika8Mhumr0tRG9gOGiqfsFWoC2tKU1MylfhoHlrF-kmli-g0Jxx8dlEs4tE4aVTH8QeQrpSQOgHG0lOHyk)



It takes a few moments to provision and connect to the environment. When you are connected, you are already authenticated, and the project is set to your PROJECT_ID. For example:
![image](https://lh6.googleusercontent.com/50yTYHqFFyU8wc_1AuOeYULcQQ6VNzryxs8MZ8doC-gzIz7__jJqg59unXDPewsJ7wi6kvbIXWtwTmhYeBe5wGSwrLe_4AJbRorIz_gt-ditTe5uqgtcbLuBbr8zfrFY9fhRiSpO)



2) Download and setup the code

From the Cloud Shell terminal, use curl to download a zip with the code for this lab:

git clone https://github.com/sela-rhinops/bootcamp-gcp-workshop.git
Change to the directory containing the code for this project:

cd project


The project directory contains the following directories and files:

![image](https://lh3.googleusercontent.com/-Rd-YRi-JIKmewDb-oO3pkFJ0wm6QmBiALyPdy_1XL13ZNXLmFRmZtgisQeSoINHSo3xOpbTJU__o0UPrQvErsQ8_HsKbGBJhBm3JXD0IF7UBxwcSIKPEmt9dG0jzoFkkRvxzc4j)



Update the file “hello.go” to include your name in the “Hello World” message
![image](https://lh3.googleusercontent.com/tLIMW45BBEYnRj6oemoKKui7MymRnuX__Y6JKONNnKYmgEOW4gvJKCLTf4wtMwgTQPccajQ4UBDOoZ8leObN7PpyoU3HBjCm_uvnZIbetx_nh4oI6KNLmLyNrQGmKTEo-oqfNDcd)



3) Creating the HTTP “Hello World” Cloud Function

From the project directory you can deploy the function name with gcloud functions deploy (this will take a minute or two)

gcloud functions deploy {your-name}-HelloWorld --runtime go113 --trigger-http --allow-unauthenticated --entry-point=HelloWorld

![image](https://lh6.googleusercontent.com/UPeELUeUesNtrhTlpQhtkDb2kAF4-mPbrG2UaYNv10r4i-mtTyA18_YD9m1NNHlZMmsd9ROI-pClD3HmTFBIjsJgKn5h5qsja8XiQVBBzOz7bMejPOztWEBiv4dAxs111LsIRHS5)

Copy the httpsTrigger URL that's displayed in the output. It will have a form like this:

![image](https://lh6.googleusercontent.com/kDqPEH3VfySBWokIVwLaQn6nPUf6DxylR3gIz1yoPVCmj7GVM5H7QwhlxK3ehqV9m6v_CZK9viH3uGNyx7SYABbOOotlLdOZepYPv4SR9XzyQ_dQN4svPr9dyHDWcWe-A-ypNDnf)

Paste the httpsTrigger URL in your browser to trigger the function

![image](https://lh6.googleusercontent.com/JnJkBXil55YqVQ7HU0cTHTaYzmT45yjhasTNuQYoXTeJsesRcEX5LyoCJ6HBZqyCoEYmGGRjWraiYkVSFh0IBribOR-rAeQwVVNkbcozlZhntRDtlHQz4aP9g7M0AtjlDEEIT66L)


4) Creating the HTTP “Gopher” Cloud Function

Now make the "Hello, world" function a bit more entertaining by printing an image of a Gopher for every request. He is Gopher:

![image](https://lh4.googleusercontent.com/OFpHqOMElmt_ZEheH45CvQTc_xZd6PP-rdJKdT40s7Dtp0jrvL6g3PfNBCqo6p531vjzMv3OobJTi0ryAsSpBFdFeauQvm6IuNTIJDAscJZnfPlQycxPR3vjGsjMeE-rXaIXtGsA)

Understand the source code (stored on ./project/gopher.go)

The file starts with a package declaration and comment. All Go code is written inside a package, with a declaration like this at the top.

The import block contains a list of other packages that this file depends on. These packages are referred to in the rest of the file using their name. For example, to use the ResponseWriter type from the http package, you write http.ResponseWriter.

Next is the Gopher function declaration.

The function starts by reading the gophercolor.png file (see the sample code) using the os.Open function.

Then, it checks whether there was an error reading the file, which might occur if the file is corrupted or was accidentally left out of the upload.

It uses io.Copy to copy the gopher image to w, the http.ResponseWriter argument. Everything written to w will be sent in the HTTP response.

If there was no error when writing the response, the function returns normally.
Deploy this function as you did for the "Hello, world" function from before, using gcloud functions deploy and the name of the function, Gopher:

gcloud functions deploy {your-name}-Gopher --runtime go113 --trigger-http --allow-unauthenticated --entry-point=Gopher

![image](https://lh5.googleusercontent.com/85GRqfy4SD4NAXn2GQGRuRV-QyaNdTE3HYgLCADAH2_k235U1f-w7bLe03X07GztbLut9K_YhzCXCKtS6zf_FSx4QoG9mIXu2DSHeoFxh0JeQE8yVRbS8iMGhiEj3LhMV9bcTGbD)

Copy the httpsTrigger URL that's displayed in the output. It will have a form like this:

![image](https://lh6.googleusercontent.com/RhH8RPMNNWrTX9xJXvFrd7sccdplnvrhOpl-ZkJJ8pNQEQmvP1MvyU2xfvgiIP7pNdb29eGbk2DGjWxCenOjIdeNeDGCZpT_HRBewoxQeh4tpq-KwgQLukpaUtF8TNLiV63vcBq4)

Paste the httpsTrigger URL in your browser to trigger the function

![image](https://lh5.googleusercontent.com/3k4eo_lYxppYbOZ1zhA6aI_mlC_xVUlRmAQ2IlS7wLkWtEf2jdrYevFBJdJrAJpRmAVbZLIL7FuUZmqS4JuCk6KWmq07EFkYCU8BxmraDM-NAAibOYU_QI9hcQUT8j9tx98yU2C4)

Good Job!


Delivery

Send the following in your 1-on-1 channel:

The httpsTrigger URL for your HelloWorld Function
The httpsTrigger URL for your Gopher Function

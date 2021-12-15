# Tutorial: Connect MySQL data source in Linux Server to Power BI Dataflow
This is reference graphical implementation guideline for anyone connecting Power BI Dataflow to Mysql data source running in Linux Server.   

## Prerequisites
You need to use windows machine or create windows vm prior to install power BI gateway.  
Install putty to create ssh connection with linux.  

## Setting Up power BI gateway  
To Set up Power BI Gateway, take the following steps:   

> 1. Download Power BI Gateway from Power BI service (online)  
> ![image](https://user-images.githubusercontent.com/85021780/146190874-922f73a5-6081-4e99-a369-a86137e67459.png)  
>  
> 2. After downloading the gateway set up by signing in  
> ![image](https://user-images.githubusercontent.com/85021780/146191116-22b2ed82-4341-465d-806a-df1b3086f005.png)  
>   
> 3. By clicking sign in dialog page will appear for email  
> ![image](https://user-images.githubusercontent.com/85021780/146191366-c7df72bd-6ebb-410f-8884-5024d1f41d62.png)  
>  
> 4. Sign in with your power BI credential  
> 5. Once done. Select OK.  
> ![image](https://user-images.githubusercontent.com/85021780/146191719-86ffe866-dd08-4658-88e1-6710c7d1c5fa.png)  
> 

## Setting up SSH Tunnel
At the moment we can't run Power BI Gateway in Linux Server where our MySQL data source is located thus create SSH tunneling. SSH is a secure Shell that uses public-key crytography to securely exhange information between different network over an insecure channel i.e Internet. An SSH tunnel enable to link a port on your local machine (in our case windows) to a port on a remote host (Linux Server). This Creates Communications from remote machine to our local machine through the port which is encrypted by the SSH Connection.  
> 1. Open ** Putty ** and Type Ip address of your Linux Server.  
> ![image](https://user-images.githubusercontent.com/85021780/146193712-50fdf01d-511d-44c4-b794-5b6682bb901b.png)  
>   
> 2. Click Tunnels under SSH tab and Add source port with Destination address to be localhost.  
> ![image](https://user-images.githubusercontent.com/85021780/146195094-5299d461-6bfd-4dca-8d69-861b04e465cd.png)  
>   
> 3. Sign in to your Linux Server Credentials and ** Keep IT Running**   
> ![image](https://user-images.githubusercontent.com/85021780/146195700-48ab8ff4-9e12-4735-b389-61e0a97cedf1.png)  

## Creating DataFlow Pipeline
> 1. On your Power BI Cloud Service Open Manage gateways under settings tab ( ** This feature is only available for Pro and above account **)  
> ![image](https://user-images.githubusercontent.com/85021780/146196332-83d3086e-b41c-49a0-a402-12264c341e99.png)  
> 
> 2. Your Gateway will be automatically detected if you're using the same Power BI account when setting up your gateway.  
> ![image](https://user-images.githubusercontent.com/85021780/146196641-ab82c53e-63cc-4afd-b897-675b9f676d34.png)  
>  
> 3. Add Data Source  
> ![image](https://user-images.githubusercontent.com/85021780/146196711-c0681905-28d9-4313-abff-5e7929c5aeab.png)  
>  
> 4. Fill the Dialog page   
> ![image](https://user-images.githubusercontent.com/85021780/146196952-7951ce89-52aa-4df8-8d9a-36f43894f4dc.png)  
> 5. Select MySQl in the dropdown option under Data Source Type  
> 6. Add the localhost Address 127.0.0.1  
> 7. Add the Database you want to connect  
> 8. Select the Basic authentication kind and input your MySQL credentials in the Username and Password boxes.  
> 9. If your connection isn't encrypted, clear Use Encrypted Connection.  
> 10. Don't Check Skip Test Connection  

You Now Added a MySQL as data source.  
NOW LETS ADD NEW TABLES AND SCHEDULE REFRESH.  
> ![image](https://user-images.githubusercontent.com/85021780/146198610-0998f2da-bd7e-456a-9c32-9bc252aa5934.png)  
>   
> SELECT MySQL Database and insect the same details when Adding the MySQL as data Source.  
> ![image](https://user-images.githubusercontent.com/85021780/146198977-10341ff9-1597-4517-8621-36865df39b35.png)  
>  
> ![image](https://user-images.githubusercontent.com/85021780/146199128-36aca0f4-4ef2-48ec-8670-242ec0f22ce6.png)  
>   
> Selectting a refresh options   
> ![image](https://user-images.githubusercontent.com/85021780/146199346-9237d179-7e70-4d5c-9ee2-4316083b64b3.png)  

## Further Reading
https://docs.microsoft.com/en-us/power-query/connectors/mysqldatabase


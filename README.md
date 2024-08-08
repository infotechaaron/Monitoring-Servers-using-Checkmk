## Monitoring Linux Servers using Checkmk


In this tutorial, I'm going to show you how to use a free open-source Server Monitoring program to maintain system performance and health.

As depicted in the diagram below, I will be installing the program on an Ubuntu Linux machine (which acts as the monitoring server).

Then we're going to install the Monitoring Agents on two Linux servers and one Windows Server.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/1acf93cc-1a7b-4a35-92cc-72f2107e9282/screenshot.jpeg?tl_px=0,0&br_px=624,619&force_format=png&width=860)




**Part One: Installing Checkmk Monitoring on our CommandCenter machine**

So here we are on our Ubuntu machine called commandcenter:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/af5da986-a797-4a20-80c3-bd59b2c9033b/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860)

**Step 1** - Open a browser and go to [checkmk.com](http://checkmk.com) and hit the Download button:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/ecc56777-2bf8-49f1-aed7-ebcf58006b05/screenshot.jpeg?tl_px=0,0&br_px=643,362&force_format=png&width=860)

Choose **Checkmk for Linux** and then the **Raw** edition:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/df063bee-d8fd-41e9-9c9a-ccaac3f2f14c/screenshot.jpeg?tl_px=0,0&br_px=643,364&force_format=png&width=860)

**Step 2** - Choose correct Version/Platform/OS

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/adb38094-56be-4517-9058-cd868f5933e1/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860)

**Step 3** - Install Checkmk

**Step 3.1** - Downloading Checkmk for Ubuntu or Debian

Pulling the package using *wget*

Copy and paste the wget command into the Ubuntu terminal:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/ef39710f-f971-431e-85cf-1b6eab6d1b9e/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860)

Open Terminal:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6c54bf79-473b-49f0-9c9f-a1c98fdc2c02/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860)

**Paste**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/5bbb731b-79da-43ce-8475-fbd079f3ac93/screenshot.jpeg?tl_px=0,22&br_px=643,503&force_format=png&width=860)

Press **Enter**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d9badcd2-1678-4585-982b-c6a896893f2c/screenshot.jpeg?tl_px=0,22&br_px=643,503&force_format=png&width=860)

**Step 3.3** - Install the Checkmk package

Now install the package including all of its dependencies.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/5b76b461-33ea-4ed5-9823-88c382bf1bf7/screenshot.jpeg?tl_px=0,0&br_px=643,362&force_format=png&width=860)

Copy and paste **sudo apt install ./check-mk-raw-2.3.0p12_0.noble_amd64.deb** into terminal and press **Enter**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d535203b-4877-44aa-8836-3de0b8d4d88d/screenshot.jpeg?tl_px=0,0&br_px=643,639&force_format=png&width=1120.0)

Test if the installation was successful by running the **omd version** command:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/17b9f769-03bf-43e0-a96f-72932ccd9279/screenshot.jpeg?tl_px=0,0&br_px=642,66&force_format=png&width=860)

### **Step 3.4 - Create a Checkmk monitoring site**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/c55dcdfc-73bc-4e14-8b7d-a6d9b34ffdff/screenshot.jpeg?tl_px=0,0&br_px=643,520&force_format=png&width=983)

Use the **omd** command to create a new Checkmk site:

Type **sudo omd create <sitename>**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/1e8f3755-9fbc-4b17-951a-aa3f2b1822e4/screenshot.jpeg?tl_px=0,0&br_px=643,392&force_format=png&width=860)

Notice the admin username **cmkadmin** and default password have been created for you.

Copy the auto-generated password from the terminal:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e98180af-9006-49b3-b4c0-7c138c81207d/screenshot.jpeg?tl_px=0,0&br_px=829,590&force_format=png&width=1120.0)

Use the **sudo omd start <sitename>** command to start the site:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/3cd52f12-0c3e-4d06-b0c4-411876677e00/screenshot.jpeg?tl_px=0,0&br_px=643,189&force_format=png&width=860)

Type **ip address** in terminal to get IP address of the Ubuntu machine then **copy it to clipboard**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/21fcfc06-9801-407e-93cf-b0b2cd0d18de/screenshot.jpeg?tl_px=0,0&br_px=643,474&force_format=png&width=860)

While still on your Ubuntu machine, **paste the ip address into a new browser** and add **/monitoring** after the ip address. Then press **Enter**:

For example: *192.168.7.134/monitoring*

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/308203a2-c223-4149-b64d-482abe007de4/screenshot.jpeg?tl_px=0,0&br_px=643,458&force_format=png&width=860)

You then see the checkmk web login:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/fb257708-2e14-4bb0-aee3-e1445a3923ed/screenshot.jpeg?tl_px=0,0&br_px=643,416&force_format=png&width=860)

Use the default Username and Password given to you in the terminal:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/98eef1d1-df5b-4e91-b754-e41a015e31d3/screenshot.jpeg?tl_px=0,0&br_px=643,293&force_format=png&width=860)





**Login**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/c42a4f10-172a-469b-9462-c532034dcf64/screenshot.jpeg?tl_px=0,0&br_px=643,455&force_format=png&width=860)

Once logged in, the first thing you should do is change the default password by going to **User** >> **Change password**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/792dfabd-6624-4bc1-a2ff-e13ff2abf785/screenshot.jpeg?tl_px=0,0&br_px=643,814&force_format=png&width=884)

Now we’re done with installing Checkmk onto the command center device/server and as long as it is running, we can access the monitoring dashboard from any device with a web browser.

**Part Two: Installing the Checkmk Agents on the Linux Servers**

So both of the Linux Servers I have running on two separate virtual machines.

On the left **EHR-Linux-Server**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7a64143c-afb4-49bd-addd-c27da0b97bdf/ascreenshot.jpeg?tl_px=0,0&br_px=1920,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=226,65)

and on the right **PatientPortalWebServer**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/132d57dc-1caf-41bb-9f10-1714e00e97a6/ascreenshot.jpeg?tl_px=0,0&br_px=1920,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=603,66)

For more detail you can use the Checkmk Documentation for installing monitoring agents here:

<https://docs.checkmk.com/latest/en/wato_monitoringagents.html>

The following image shows the various ways that Checkmk can access systems to be monitored:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/cd69f9d3-a826-41c2-a742-6f694ecf38a9/screenshot.jpeg?tl_px=0,23&br_px=957,664&force_format=png&width=1120.0)

In the Checkmk Raw edition, you can find the agent’s Linux packages within the Web GUI via **Setup** > **Agents** > **Linux**

So let's setup **EHR-Linux-Server** for monitoring by opening a web browser within it:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/fb9097da-4c26-4e50-8200-c5e23b1a595e/ascreenshot.jpeg?tl_px=0,118&br_px=1719,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=59,401)

Type in the ip address of the CommandCenter (Ubuntu) machine, followed by a slash and the name of your site, in the search bar:

*192.168.7.134/monitoring*

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e9a20e2b-6fd2-4b33-9471-c94c28b2ad1e/ascreenshot.jpeg?tl_px=0,0&br_px=1719,961&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=255,139)



**Login** with the same credentials:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/8a90b849-4c64-4ed4-987a-bffae0bb66e3/File.jpeg?tl_px=0,0&br_px=643,455&force_format=png&width=860)

Go to **Setup** > **Agents** > **Linux**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/4e8d1980-5f9e-42eb-8a6c-5ddeadb5a3a2/user_cropped_screenshot.jpeg?tl_px=0,118&br_px=1360,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=75,361)

Click on

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/eb303dc8-4dab-443a-a049-e5771ad304f1/ascreenshot.jpeg?tl_px=0,64&br_px=859,545&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=163,212)

After downloading the Linux Agent package, the Checkmk documentation says to run the following as a root user:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/42d5bd0d-cb26-4fd1-b7e5-17d03af68b80/ascreenshot.jpeg?tl_px=336,87&br_px=1483,728&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=524,277)

Copy the command from the documentation:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6654226e-37c6-4015-bf1c-0492eae1f9c8/ascreenshot.jpeg?tl_px=0,97&br_px=1146,738&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=507,277)

Change to the Downloads folder in the terminal then paste in the command from the Checkmk docs:

*cd Downloads*

*sudo dpkg -i check-mk-agent_2.3.0p12-1_all.deb*

*enter*

**NOTE:** Make sure you change the ***check-mk-agent_2.3.0p12-1_all.deb*** in the command you copied from the documentation to match the latest version of the Linux Agent you just downloaded (as the docs may be outdated).

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/0fa1da89-fa02-424d-9ef4-07f455ad4963/screenshot.jpeg?tl_px=0,0&br_px=942,382&force_format=png&width=983)

The agent installs:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d00de725-2e15-4d2b-8a9f-4ef97897df06/screenshot.jpeg?tl_px=0,0&br_px=935,543&force_format=png&width=983)

Now go to **Setup** > **Hosts**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/82572ea4-6b7a-472f-b41e-238b91569efc/ascreenshot.jpeg?tl_px=0,90&br_px=859,571&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=110,212)

Click on **Add host to the monitoring**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7715b5c6-8c3c-4056-928a-a1adf1907976/ascreenshot.jpeg?tl_px=0,99&br_px=859,580&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=223,212)

Enter the Host name

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e47f40c9-6893-4731-82a7-cd0d9c971f57/ascreenshot.jpeg?tl_px=0,102&br_px=859,583&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=366,212)



**EHR-Linux-Server**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/b82ba8ec-7d97-4e95-9c42-f47ba688c133/screenshot.jpeg?tl_px=12,59&br_px=872,540&force_format=png&width=860)

Click on the IP address family box:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/5b795473-949f-41e9-a8dd-b05b3bb70560/ascreenshot.jpeg?tl_px=0,172&br_px=859,653&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=286,212)

Click on the IPv4 address checkbox:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6534756b-3264-4282-acf6-51cb500dde2b/ascreenshot.jpeg?tl_px=0,207&br_px=859,688&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=286,212)

Then get the IP address from the terminal with the **ip address** command:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6221dfcf-1037-49eb-8e5c-df3674ab6e2b/screenshot.jpeg?tl_px=39,27&br_px=898,508&force_format=png&width=860)

Input it in to the IPv4 address text area:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/bdc19601-6057-4fda-a0a3-937b455af69e/screenshot.jpeg?tl_px=0,0&br_px=968,638&force_format=png&width=1120.0)

Check the box next to **Checkmk agent/API integrations**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/b82962ac-96a8-4099-9330-745b21c73342/ascreenshot.jpeg?tl_px=0,283&br_px=859,764&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=283,212)

Click **Save & run service discovery**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/cecf06d9-513a-4419-a9a6-d7d7bd6f2779/ascreenshot.jpeg?tl_px=0,19&br_px=859,500&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=193,212)

Click **Change** on top right:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d005d0c7-84d7-4d1d-a0d3-e45c839eedb8/ascreenshot.jpeg?tl_px=0,0&br_px=1920,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=881,77)

Click **Activate on selected sites**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6aa90f31-47fe-4c23-aa05-e60d76eadb88/ascreenshot.jpeg?tl_px=0,0&br_px=1146,640&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=172,216)




It will shortly say Success.

Then go to **Setup**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/3c608435-8d10-4afa-b830-7724dcd888b5/ascreenshot.jpeg?tl_px=0,122&br_px=859,603&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=3,212)

Go to **Hosts**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/39e14915-0d2a-4e5d-9115-c42babe96829/ascreenshot.jpeg?tl_px=0,84&br_px=859,565&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=107,212)

Hit **Run Service Discovery**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/650966f7-46d8-40b4-85c5-588c70de1ef8/ascreenshot.jpeg?tl_px=0,147&br_px=859,628&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=144,212)

You'll start to see the system status of the EHR-Linux-Server roll in as it scans the system via the Linux agent we just installed.

Then go to **Monitor**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e7900401-41a1-4399-9f50-c076782a4254/ascreenshot.jpeg?tl_px=0,0&br_px=1719,961&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=-8,130)

Click **All hosts**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7c82d0e7-6efd-4662-9c7c-2fc6c050eaf7/ascreenshot.jpeg?tl_px=0,108&br_px=859,589&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=113,212)

Click on the Host name to check the progress of the scan:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/dff77889-a806-4334-aad8-5f3c1acbb090/ascreenshot.jpeg?tl_px=0,53&br_px=1146,694&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=129,277)

It still says it's PENDing:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/357aab67-0f92-4d4c-ad73-446de914f1bc/ascreenshot.jpeg?tl_px=0,193&br_px=859,674&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=130,212)

Eventually, when the scans are complete, it will start showing more stats (as shown below):

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/22271ac8-baeb-4081-8625-396154177d34/screenshot.jpeg?tl_px=71,0&br_px=1448,514&force_format=png&width=1120.0)

Click here:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d988bc50-43df-4d96-bfa5-fd1aacdb89b0/ascreenshot.jpeg?tl_px=0,0&br_px=859,480&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=9,208)

Click here:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/1c08406e-8304-458e-a9c3-58b3b0940e72/ascreenshot.jpeg?tl_px=0,87&br_px=859,568&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=131,212)




While the scans are still being processed, it will look sort of blank (but it will show you now have 1 host up and running). Shortly you will see the scans start to finish and display stats about the device or server you are monitoring:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/9275920d-dbc9-4897-a7f9-44b55173bc24/screenshot.jpeg?tl_px=0,0&br_px=1521,864&force_format=png&width=1120.0)

Click on the **1 Up** under Host statistics to check the status of the ping:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/78517da6-ea10-471b-8e29-b08eb4340bc1/ascreenshot.jpeg?tl_px=0,113&br_px=688,498&force_format=png&wat_scale=61&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=231,170)

Click **EHR-Linux-Server**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/140f55f6-e715-4eff-b9a9-774f7e8132cc/ascreenshot.jpeg?tl_px=0,134&br_px=859,615&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=153,212)

The Ping will still say PENDing for a while, but eventually it will finish Pinging and look as shown below.

Now click on **PING**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/eb8de334-d845-4c94-8677-21a50a98e04e/user_cropped_screenshot.jpeg?tl_px=72,0&br_px=1448,634&force_format=png&width=1120.0)

After clicking on the Ping you will see detailed metrics such as: Packet loss, Round trip ping time, if device is up/down, etc...

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/00fa6bde-9eee-4733-9a37-bf996cd9b936/screenshot.jpeg?tl_px=0,0&br_px=1323,941&force_format=png&width=1120.0)

Now go back to **Monitor** > **All hosts** > **EHR-Linux-Server**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/181d421d-d7d3-411e-939a-852e6e07cfcb/ascreenshot.jpeg?tl_px=0,160&br_px=764,587&force_format=png&width=764&wat_scale=68&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=184,188)

Step

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/c55a2425-c6c9-4c2a-a81c-2cb5f84f6b95/user_cropped_screenshot.jpeg?tl_px=73,0&br_px=1449,525&force_format=png&width=1120.0)

This WARN is warning me that there are several device services that are not being monitored (cpu_loads, kernel, diskstat). This is probably because I'm monitoring a Virtual Machine, but I think more investigation is needed.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7c3903f0-f79b-46e9-b7b5-a033109410c3/screenshot.jpeg?tl_px=0,0&br_px=1559,912&force_format=png&width=1120.0)

If you scroll down to the bottom of the page, you'll see some extra details describing this type of warning:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/04421295-a3e8-42a7-9dd2-3f2396a84a3a/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=1513,885&force_format=png&width=1120.0)
#### [Made with Scribe](https://scribehow.com/shared/Installing_and_Monitoring_Linux_Servers_with_Checkmk__czKMfEBMTsaDGIDmmFJ6Ig)







## Monitoring Linux Servers using Checkmk

[](https://github.com/infotechaaron/Monitoring-Servers-using-Checkmk#monitoring-linux-servers-using-checkmk)

In this tutorial, I'm going to show you how to use a free open-source Server Monitoring program Checkmk to maintain system performance and health.

As depicted in the diagram below, I will be installing the program on an Ubuntu Linux machine (which acts as the monitoring server).

Then we're going to install the Monitoring Agents on two Linux servers and one Windows Server.

[![](https://camo.githubusercontent.com/c083ac83fca40e33388a25a3c742edf50d8bc7c831a5e111bf7766412df9ffc7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31616366393363632d316137622d346133352d393263632d3732663231303765393238322f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3632342c36313926666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/c083ac83fca40e33388a25a3c742edf50d8bc7c831a5e111bf7766412df9ffc7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31616366393363632d316137622d346133352d393263632d3732663231303765393238322f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3632342c36313926666f7263655f666f726d61743d706e672677696474683d383630)

<br>
<br>

# **Part One: Installing Checkmk Monitoring on our CommandCenter machine**

So here we are on our Ubuntu machine called commandcenter:

[![](https://camo.githubusercontent.com/6d07600c1dc9eb374b0507c110cd8819ba7ce57a80cc535fd3965a5dba8256d5/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f61663564613938362d613739372d346132302d383063332d6264353962326339303333622f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363126666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/6d07600c1dc9eb374b0507c110cd8819ba7ce57a80cc535fd3965a5dba8256d5/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f61663564613938362d613739372d346132302d383063332d6264353962326339303333622f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363126666f7263655f666f726d61743d706e672677696474683d383630)

<br>
<br>

## **Step 1** - Download and Install Checkmk

Open a browser and go to  [checkmk.com](http://checkmk.com/)  and hit the Download button:

[![](https://camo.githubusercontent.com/61b9077b0c7e4426c8d1d1593663d8718166dd4c681d541fdc2b061c56f523c3/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65636335363737372d326266382d343966312d616564372d6562636635383030366230352f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363226666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/61b9077b0c7e4426c8d1d1593663d8718166dd4c681d541fdc2b061c56f523c3/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65636335363737372d326266382d343966312d616564372d6562636635383030366230352f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363226666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Choose  **Checkmk for Linux**  and then the  **Raw**  edition:

[![](https://camo.githubusercontent.com/af9b4de48fddc8de9b3ce62b64b1bac5a4a40c93f12beb6f3dff6d12a0732b61/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64663036336265652d643866642d343165392d396339612d6363616163336632663134632f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363426666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/af9b4de48fddc8de9b3ce62b64b1bac5a4a40c93f12beb6f3dff6d12a0732b61/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64663036336265652d643866642d343165392d396339612d6363616163336632663134632f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363426666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

## **Step 2** - Choose correct Version/Platform/OS

[![](https://camo.githubusercontent.com/9ec99d06651a63651cd4cd51c1b77b796391723c6d1507192e6e1f42ca99ceec/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f61646233383039342d353662652d343531372d393035382d6364383638663539333365312f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363126666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/9ec99d06651a63651cd4cd51c1b77b796391723c6d1507192e6e1f42ca99ceec/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f61646233383039342d353662652d343531372d393035382d6364383638663539333365312f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363126666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>
<br>

## **Step 3** - Install Checkmk

### **Step 3.1 - Downloading Checkmk for Ubuntu or Debian**


Pulling the package using  _wget_

Copy and paste the wget command into the Ubuntu terminal:

[![](https://camo.githubusercontent.com/9ae2a51e133b1da5f03a77902cf4003125f363f43046219691c3a92f4716668c/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65663339373130662d663937312d343331652d383563662d3162366561623664316239652f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363126666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/9ae2a51e133b1da5f03a77902cf4003125f363f43046219691c3a92f4716668c/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65663339373130662d663937312d343331652d383563662d3162366561623664316239652f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363126666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Open Terminal:

[![](https://camo.githubusercontent.com/95a5c23073f3fe31022dc1739212e958c4d58b9612faf6f627ef6e11d1599814/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36633534626637392d343733622d343966302d396339662d6131633938666463326330322f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363126666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/95a5c23073f3fe31022dc1739212e958c4d58b9612faf6f627ef6e11d1599814/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36633534626637392d343733622d343966302d396339662d6131633938666463326330322f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363126666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

**Paste**

[![](https://camo.githubusercontent.com/d813d0b0507bc5852308b358f15b8bfe3819f04dda65012bdaf937aff7c58355/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f35626262373331622d373964612d343363652d383437352d6662643037396633616339332f73637265656e73686f742e6a7065673f746c5f70783d302c32322662725f70783d3634332c35303326666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/d813d0b0507bc5852308b358f15b8bfe3819f04dda65012bdaf937aff7c58355/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f35626262373331622d373964612d343363652d383437352d6662643037396633616339332f73637265656e73686f742e6a7065673f746c5f70783d302c32322662725f70783d3634332c35303326666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Press  **Enter**

[![](https://camo.githubusercontent.com/1496ae3dadab9ef9e34fa17ac81c82643cc77866881d360c04e6010852394f9d/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64396261646364322d313637382d343538352d393832622d6336613839363839336632632f73637265656e73686f742e6a7065673f746c5f70783d302c32322662725f70783d3634332c35303326666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/1496ae3dadab9ef9e34fa17ac81c82643cc77866881d360c04e6010852394f9d/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64396261646364322d313637382d343538352d393832622d6336613839363839336632632f73637265656e73686f742e6a7065673f746c5f70783d302c32322662725f70783d3634332c35303326666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

### **Step 3.3 - Install the Checkmk package**
Now install the package including all of its dependencies.

[![](https://camo.githubusercontent.com/04556d240422c71d8846346aa876a76761fd4f1d5ec60187e60f97c8396f077f/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f35623736623436312d333365612d346564352d393832332d3838633338326266316266372f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363226666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/04556d240422c71d8846346aa876a76761fd4f1d5ec60187e60f97c8396f077f/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f35623736623436312d333365612d346564352d393832332d3838633338326266316266372f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33363226666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Copy and paste  **sudo apt install ./check-mk-raw-2.3.0p12_0.noble_amd64.deb**  into terminal and press  **Enter**:

[![](https://camo.githubusercontent.com/903cfd4a6168e156383be081704c39f2e32c15646a8d14b0c85a8e8e85400057/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64353335323033622d343837372d343461612d383833362d3364653062386434643838642f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c36333926666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/903cfd4a6168e156383be081704c39f2e32c15646a8d14b0c85a8e8e85400057/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64353335323033622d343837372d343461612d383833362d3364653062386434643838642f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c36333926666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

Test if the installation was successful by running the  **omd version**  command:

[![](https://camo.githubusercontent.com/2f176723296b375189dfb7a9c15d524a3ec6a433ed55932e78b0f1ce15a65366/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31376239663736392d303362662d343365302d613936662d3732393332636364393237392f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634322c363626666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/2f176723296b375189dfb7a9c15d524a3ec6a433ed55932e78b0f1ce15a65366/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31376239663736392d303362662d343365302d613936662d3732393332636364393237392f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634322c363626666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

### **Step 3.4 - Create a Checkmk monitoring site**

[](https://github.com/infotechaaron/Monitoring-Servers-using-Checkmk#step-34---create-a-checkmk-monitoring-site)

[![](https://camo.githubusercontent.com/342d8f7e109511eb25af0d314a80e5ce00d3308983eb240a3508901771d74815/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63353564636466632d373362632d346531342d386237642d6136643962333466666466662f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c35323026666f7263655f666f726d61743d706e672677696474683d393833)](https://camo.githubusercontent.com/342d8f7e109511eb25af0d314a80e5ce00d3308983eb240a3508901771d74815/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63353564636466632d373362632d346531342d386237642d6136643962333466666466662f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c35323026666f7263655f666f726d61743d706e672677696474683d393833)
<br>
<br>

Use the  **omd**  command to create a new Checkmk site:

Type  **sudo omd create**

[![](https://camo.githubusercontent.com/ec30559bf6992bf7a259f2264c71157bdab1b4c207c90d8fc809a08361edc6ce/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31653866333735352d396662632d346231372d393531612d6161336632623138323265342f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33393226666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/ec30559bf6992bf7a259f2264c71157bdab1b4c207c90d8fc809a08361edc6ce/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31653866333735352d396662632d346231372d393531612d6161336632623138323265342f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c33393226666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>
Notice the admin username  **cmkadmin**  and default password have been created for you.

Copy the auto-generated password from the terminal:

[![](https://camo.githubusercontent.com/a66edf78dbb7656ce08e29d89cdd55dc666a67054fc0df214165959a9926f36e/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65393831383061662d393030362d343962332d623463302d3763313338633831323037642f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3832392c35393026666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/a66edf78dbb7656ce08e29d89cdd55dc666a67054fc0df214165959a9926f36e/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65393831383061662d393030362d343962332d623463302d3763313338633831323037642f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3832392c35393026666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

Use the  **sudo omd start** command to start the site:

[![](https://camo.githubusercontent.com/2db8f182472a72f128b7ab1d29ca762f382a5ba65e4074f7a3a6648ff9935de1/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33636435326631322d306333652d346430362d623063342d3431313837363637376530302f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c31383926666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/2db8f182472a72f128b7ab1d29ca762f382a5ba65e4074f7a3a6648ff9935de1/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33636435326631322d306333652d346430362d623063342d3431313837363637376530302f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c31383926666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Type  **ip address**  in terminal to get IP address of the Ubuntu machine then  **copy it to clipboard**:

[![](https://camo.githubusercontent.com/bfebf58b79047e5809ea8e84637b66a8d66aee45bae727cb85c31207d3169b3a/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f32316663666330362d393830312d343037652d393363662d6230623263643064313864652f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c34373426666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/bfebf58b79047e5809ea8e84637b66a8d66aee45bae727cb85c31207d3169b3a/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f32316663666330362d393830312d343037652d393363662d6230623263643064313864652f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c34373426666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

While still on your Ubuntu machine,  **paste the ip address into a new browser**  and add  **/monitoring**  after the ip address. Then press  **Enter**:

For example:  _192.168.7.134/monitoring_

[![](https://camo.githubusercontent.com/ee7539f52e23c99da8619d6a80892c58a49c974ea2ea0e9ed771c0d649884e6d/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33303832303361322d633232332d343134392d623634642d3438326162653030376465342f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c34353826666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/ee7539f52e23c99da8619d6a80892c58a49c974ea2ea0e9ed771c0d649884e6d/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33303832303361322d633232332d343134392d623634642d3438326162653030376465342f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c34353826666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

You then see the checkmk web login:

[![](https://camo.githubusercontent.com/8cc757168af891043b5203f707b5cfdb395952a23729211efbcac7d2a75d2ef7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f66623235373730382d326531342d346262302d616565332d6531343435613339323365642f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c34313626666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/8cc757168af891043b5203f707b5cfdb395952a23729211efbcac7d2a75d2ef7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f66623235373730382d326531342d346262302d616565332d6531343435613339323365642f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c34313626666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Use the default Username and Password given to you in the terminal:

[![](https://camo.githubusercontent.com/5135191b620f8525378f3baef6c60de784d5f48ba5bab4b1ffe859e92ff1ffe7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f39386565663164312d646635622d346539312d623735342d6534316130313565333164332f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c32393326666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/5135191b620f8525378f3baef6c60de784d5f48ba5bab4b1ffe859e92ff1ffe7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f39386565663164312d646635622d346539312d623735342d6534316130313565333164332f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c32393326666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

**Login**

[![](https://camo.githubusercontent.com/d4a7f826459eb2bde5c79cb2a6b6141aa7d0e2cb635b61d57e357f953d0278e7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63343261346631302d313732612d343639622d393436322d6335333230333464636636342f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c34353526666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/d4a7f826459eb2bde5c79cb2a6b6141aa7d0e2cb635b61d57e357f953d0278e7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63343261346631302d313732612d343639622d393436322d6335333230333464636636342f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c34353526666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Once logged in, the first thing you should do is change the default password by going to  **User**  >>  **Change password**:

[![](https://camo.githubusercontent.com/2c77e1d320b7b6a8f09fc5beedb067af63fec548a39bacd4c729f21a583b10c5/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37393264666162642d363632342d346263312d613266662d6531336666326162663738352f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c38313426666f7263655f666f726d61743d706e672677696474683d383834)](https://camo.githubusercontent.com/2c77e1d320b7b6a8f09fc5beedb067af63fec548a39bacd4c729f21a583b10c5/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37393264666162642d363632342d346263312d613266662d6531336666326162663738352f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3634332c38313426666f7263655f666f726d61743d706e672677696474683d383834)
<br>
<br>

Now we’re done with installing Checkmk onto the command center device/server and as long as it is running, we can access the monitoring dashboard from any device with a web browser.
<br>
<br>
<br>
<br>

# **Part Two: Installing the Checkmk Agents on the Linux Servers**

So both of the Linux Servers I have running on two separate virtual machines.

On the left  **EHR-Linux-Server**:

[![](https://camo.githubusercontent.com/c4dbc3ec5b07fb2e8b7458b790398df865d3f18a266f334f50763f3ded3771bd/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37613634313433632d616662342d343962642d616464642d6332376461306239376264662f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313932302c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3232362c3635)](https://camo.githubusercontent.com/c4dbc3ec5b07fb2e8b7458b790398df865d3f18a266f334f50763f3ded3771bd/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37613634313433632d616662342d343962642d616464642d6332376461306239376264662f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313932302c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3232362c3635)
<br>
<br>
and on the right  **PatientPortalWebServer**:

[![](https://camo.githubusercontent.com/10b5bafc33ef9a8abface7a0b243aedb13d9d2503c43e6df7bd3930fc72128d2/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31333264353764632d316361662d343162622d396631302d3137313465303065393761362f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313932302c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3630332c3636)](https://camo.githubusercontent.com/10b5bafc33ef9a8abface7a0b243aedb13d9d2503c43e6df7bd3930fc72128d2/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31333264353764632d316361662d343162622d396631302d3137313465303065393761362f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313932302c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3630332c3636)
<br>
<br>

For more detail you can use the Checkmk Documentation for installing monitoring agents here:

[https://docs.checkmk.com/latest/en/wato_monitoringagents.html](https://docs.checkmk.com/latest/en/wato_monitoringagents.html)

The following image shows the various ways that Checkmk can access systems to be monitored:

[![](https://camo.githubusercontent.com/2028aaf3a3b10f13f203dbd6693abceb4c6a479e4e24cfa8ae0773c13f16e5c6/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63643639663964332d613832362d343163322d613734322d3666363934656366333861392f73637265656e73686f742e6a7065673f746c5f70783d302c32332662725f70783d3935372c36363426666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/2028aaf3a3b10f13f203dbd6693abceb4c6a479e4e24cfa8ae0773c13f16e5c6/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63643639663964332d613832362d343163322d613734322d3666363934656366333861392f73637265656e73686f742e6a7065673f746c5f70783d302c32332662725f70783d3935372c36363426666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

In the Checkmk Raw edition, you can find the agent’s Linux packages within the Web GUI via  **Setup**  >  **Agents**  >  **Linux**

So let's setup  **EHR-Linux-Server**  for monitoring by opening a web browser within it:

[![](https://camo.githubusercontent.com/a325cf27f89bd163f3e9f276abcee28254e6e9f876c1c44ac4d47c3cbc647eb3/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f66623930393764612d346332362d346535302d383230302d6335653233623161353935652f6173637265656e73686f742e6a7065673f746c5f70783d302c3131382662725f70783d313731392c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d35392c343031)](https://camo.githubusercontent.com/a325cf27f89bd163f3e9f276abcee28254e6e9f876c1c44ac4d47c3cbc647eb3/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f66623930393764612d346332362d346535302d383230302d6335653233623161353935652f6173637265656e73686f742e6a7065673f746c5f70783d302c3131382662725f70783d313731392c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d35392c343031)
<br>
<br>

Type in the ip address of the CommandCenter (Ubuntu) machine, followed by a slash and the name of your site, in the search bar:

_192.168.7.134/monitoring_

[![](https://camo.githubusercontent.com/838024efec4fe8e7c8c2f60bc4b11690dfd39451d94a4ef7283768d14be8b591/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65396132306532622d366664322d346233332d393437312d6339346332386232616431652f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313731392c39363126666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3235352c313339)](https://camo.githubusercontent.com/838024efec4fe8e7c8c2f60bc4b11690dfd39451d94a4ef7283768d14be8b591/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65396132306532622d366664322d346233332d393437312d6339346332386232616431652f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313731392c39363126666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3235352c313339)
<br>
<br>

**Login**  with the same credentials:

[![](https://camo.githubusercontent.com/a374a3ae8ade36c29b6a124d389cc29a72f2df574e78891624a98b119ad0916a/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f38613930623834392d346336342d346564342d393837612d6266666165306262363665332f46696c652e6a7065673f746c5f70783d302c302662725f70783d3634332c34353526666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/a374a3ae8ade36c29b6a124d389cc29a72f2df574e78891624a98b119ad0916a/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f38613930623834392d346336342d346564342d393837612d6266666165306262363665332f46696c652e6a7065673f746c5f70783d302c302662725f70783d3634332c34353526666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Go to  **Setup**  >  **Agents**  >  **Linux**

[![](https://camo.githubusercontent.com/0a320bbda8d2ed597350b8beb0255a09bbdfdbcb38d9f2304981d5cf21cb47d7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f34653864313938302d356639652d343265622d386136632d3564646561646235613361322f757365725f63726f707065645f73637265656e73686f742e6a7065673f746c5f70783d302c3131382662725f70783d313336302c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d37352c333631)](https://camo.githubusercontent.com/0a320bbda8d2ed597350b8beb0255a09bbdfdbcb38d9f2304981d5cf21cb47d7/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f34653864313938302d356639652d343265622d386136632d3564646561646235613361322f757365725f63726f707065645f73637265656e73686f742e6a7065673f746c5f70783d302c3131382662725f70783d313336302c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d37352c333631)
<br>
<br>

Click on the first Package Agents (.deb)

[![](https://camo.githubusercontent.com/61ec50bebcbbfccb5cefa5bc410217c4ed054cb3e8d611c09ecf712c60334759/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65623330336463382d346461622d343433612d613034392d6535373731616433303466312f6173637265656e73686f742e6a7065673f746c5f70783d302c36342662725f70783d3835392c35343526666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3136332c323132)](https://camo.githubusercontent.com/61ec50bebcbbfccb5cefa5bc410217c4ed054cb3e8d611c09ecf712c60334759/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65623330336463382d346461622d343433612d613034392d6535373731616433303466312f6173637265656e73686f742e6a7065673f746c5f70783d302c36342662725f70783d3835392c35343526666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3136332c323132)
<br>
<br>

After downloading the Linux Agent package, the [Checkmk documentation](https://docs.checkmk.com/latest/en/agent_linux.html) says to run the following as a root user:

[![](https://camo.githubusercontent.com/e43ca684332ca4c3fa3270bf6542572681edcc2a664251d830dd9b9ed2f91a7d/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f34326435626430642d636232362d346664312d623765352d3137643033616636386238302f6173637265656e73686f742e6a7065673f746c5f70783d3333362c38372662725f70783d313438332c37323826666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3532342c323737)](https://camo.githubusercontent.com/e43ca684332ca4c3fa3270bf6542572681edcc2a664251d830dd9b9ed2f91a7d/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f34326435626430642d636232362d346664312d623765352d3137643033616636386238302f6173637265656e73686f742e6a7065673f746c5f70783d3333362c38372662725f70783d313438332c37323826666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3532342c323737)
<br>
<br>

Copy the command from the documentation:

[![](https://camo.githubusercontent.com/8fbb1e41fce2136bf439685d8a48316372e932395f1a7eabe1d7d77ef3948eab/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36363534323236652d333763362d343031352d626631632d3034393265616531663963382f6173637265656e73686f742e6a7065673f746c5f70783d302c39372662725f70783d313134362c37333826666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3530372c323737)](https://camo.githubusercontent.com/8fbb1e41fce2136bf439685d8a48316372e932395f1a7eabe1d7d77ef3948eab/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36363534323236652d333763362d343031352d626631632d3034393265616531663963382f6173637265656e73686f742e6a7065673f746c5f70783d302c39372662725f70783d313134362c37333826666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3530372c323737)
<br>
<br>

Change to the Downloads folder in the terminal then paste in the command from the Checkmk docs:

_cd Downloads_

_sudo dpkg -i check-mk-agent_2.3.0p12-1_all.deb_

_enter_

**NOTE:**  Make sure you change the  _**check-mk-agent_2.3.0p12-1_all.deb**_  in the command you copied from the documentation to match the latest version of the Linux Agent you just downloaded (as the docs may be outdated).

[![](https://camo.githubusercontent.com/5ea2a6a295ad389fb8bdb53d06295f9a201b9c4f46fd9f1352cd7c14cdd14132/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f30666131646138392d666130322d343234642d396566342d3037663435356164343936332f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3934322c33383226666f7263655f666f726d61743d706e672677696474683d393833)](https://camo.githubusercontent.com/5ea2a6a295ad389fb8bdb53d06295f9a201b9c4f46fd9f1352cd7c14cdd14132/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f30666131646138392d666130322d343234642d396566342d3037663435356164343936332f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3934322c33383226666f7263655f666f726d61743d706e672677696474683d393833)
<br>
<br>

The agent installs:

[![](https://camo.githubusercontent.com/04de7928a615d9a5189458e8913a1d266b06a2b56d0071f060ff84e5cb780d03/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64303064653732352d326531352d346432622d386139662d3465663937383937646630362f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3933352c35343326666f7263655f666f726d61743d706e672677696474683d393833)](https://camo.githubusercontent.com/04de7928a615d9a5189458e8913a1d266b06a2b56d0071f060ff84e5cb780d03/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64303064653732352d326531352d346432622d386139662d3465663937383937646630362f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3933352c35343326666f7263655f666f726d61743d706e672677696474683d393833)
<br>
<br>

Now go to  **Setup**  >  **Hosts**

[![](https://camo.githubusercontent.com/b0fedc3a28d42a035978be7fd649c70d981f7907997b23d286b4f5a2eb2e724a/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f38323537326561342d366237612d343732662d623431652d3233386239313536396566632f6173637265656e73686f742e6a7065673f746c5f70783d302c39302662725f70783d3835392c35373126666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3131302c323132)](https://camo.githubusercontent.com/b0fedc3a28d42a035978be7fd649c70d981f7907997b23d286b4f5a2eb2e724a/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f38323537326561342d366237612d343732662d623431652d3233386239313536396566632f6173637265656e73686f742e6a7065673f746c5f70783d302c39302662725f70783d3835392c35373126666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3131302c323132)
<br>
<br>

Click on  **Add host to the monitoring**:

[![](https://camo.githubusercontent.com/26553d86e71ba939e56efe85cb65699f4a828e1558030f12a54970dac996b9e6/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37373135623563362d386333632d343035362d393238612d6131616466313930373937362f6173637265656e73686f742e6a7065673f746c5f70783d302c39392662725f70783d3835392c35383026666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3232332c323132)](https://camo.githubusercontent.com/26553d86e71ba939e56efe85cb65699f4a828e1558030f12a54970dac996b9e6/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37373135623563362d386333632d343035362d393238612d6131616466313930373937362f6173637265656e73686f742e6a7065673f746c5f70783d302c39392662725f70783d3835392c35383026666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3232332c323132)
<br>
<br>

Enter the Host name

[![](https://camo.githubusercontent.com/7d62de32b8f4b2071826f43cb24ff65fdd6d2801c8777bf5629cec0baab7f548/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65343766343063392d363839332d343733312d383261372d6364306439633937316635372f6173637265656e73686f742e6a7065673f746c5f70783d302c3130322662725f70783d3835392c35383326666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3336362c323132)](https://camo.githubusercontent.com/7d62de32b8f4b2071826f43cb24ff65fdd6d2801c8777bf5629cec0baab7f548/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65343766343063392d363839332d343733312d383261372d6364306439633937316635372f6173637265656e73686f742e6a7065673f746c5f70783d302c3130322662725f70783d3835392c35383326666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3336362c323132)
<br>
<br>

**EHR-Linux-Server**

[![](https://camo.githubusercontent.com/cfb7b8c1ec87c2a53b5d8de253a7b9befb15ff71f948145bd9035fe8565657e0/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f62383262613865632d376439372d346539352d396334322d6634376261363838633133332f73637265656e73686f742e6a7065673f746c5f70783d31322c35392662725f70783d3837322c35343026666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/cfb7b8c1ec87c2a53b5d8de253a7b9befb15ff71f948145bd9035fe8565657e0/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f62383262613865632d376439372d346539352d396334322d6634376261363838633133332f73637265656e73686f742e6a7065673f746c5f70783d31322c35392662725f70783d3837322c35343026666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Click on the IP address family box:

[![](https://camo.githubusercontent.com/08f11f912c8b73184b40247704c28d93cbb05303b4ea696ba13a4529b8af5d77/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f35623739353437332d393439662d343165392d613864642d6230356233626237303536302f6173637265656e73686f742e6a7065673f746c5f70783d302c3137322662725f70783d3835392c36353326666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3238362c323132)](https://camo.githubusercontent.com/08f11f912c8b73184b40247704c28d93cbb05303b4ea696ba13a4529b8af5d77/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f35623739353437332d393439662d343165392d613864642d6230356233626237303536302f6173637265656e73686f742e6a7065673f746c5f70783d302c3137322662725f70783d3835392c36353326666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3238362c323132)
<br>
<br>

Click on the IPv4 address checkbox:

[![](https://camo.githubusercontent.com/6ad5a55e634dfe763fbcb71e3c5d48409bae2158bca6ac20cc00564b88a11b74/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36353334373536622d333236342d343238322d616366362d3531636235303064646532622f6173637265656e73686f742e6a7065673f746c5f70783d302c3230372662725f70783d3835392c36383826666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3238362c323132)](https://camo.githubusercontent.com/6ad5a55e634dfe763fbcb71e3c5d48409bae2158bca6ac20cc00564b88a11b74/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36353334373536622d333236342d343238322d616366362d3531636235303064646532622f6173637265656e73686f742e6a7065673f746c5f70783d302c3230372662725f70783d3835392c36383826666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3238362c323132)
<br>
<br>

Then get the IP address from the terminal with the  **ip address**  command:

[![](https://camo.githubusercontent.com/821b5c26be791c8c61cb3d7e7855fbcabb1edc62e3a5243a37644e5a9dfeca64/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36323231646663662d313033372d343965622d386535632d6466333637346162366532622f73637265656e73686f742e6a7065673f746c5f70783d33392c32372662725f70783d3839382c35303826666f7263655f666f726d61743d706e672677696474683d383630)](https://camo.githubusercontent.com/821b5c26be791c8c61cb3d7e7855fbcabb1edc62e3a5243a37644e5a9dfeca64/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36323231646663662d313033372d343965622d386535632d6466333637346162366532622f73637265656e73686f742e6a7065673f746c5f70783d33392c32372662725f70783d3839382c35303826666f7263655f666f726d61743d706e672677696474683d383630)
<br>
<br>

Input it in to the IPv4 address text area:

[![](https://camo.githubusercontent.com/4e532a0fdfa777b3511e88211518cb277bf8bf316c62fe9332ff4af8d043b469/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f62646331393630312d363035372d346664612d613061332d3933376234353561663639652f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3936382c36333826666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/4e532a0fdfa777b3511e88211518cb277bf8bf316c62fe9332ff4af8d043b469/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f62646331393630312d363035372d346664612d613061332d3933376234353561663639652f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3936382c36333826666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

Check the box next to  **Checkmk agent/API integrations**:

[![](https://camo.githubusercontent.com/0d834890f56148b11e7e79ad0c406ff5decb036929aff2ef8c47af9fc73dadc5/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f62383239363261632d393661382d343039392d393333302d3734356232316337333334322f6173637265656e73686f742e6a7065673f746c5f70783d302c3238332662725f70783d3835392c37363426666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3238332c323132)](https://camo.githubusercontent.com/0d834890f56148b11e7e79ad0c406ff5decb036929aff2ef8c47af9fc73dadc5/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f62383239363261632d393661382d343039392d393333302d3734356232316337333334322f6173637265656e73686f742e6a7065673f746c5f70783d302c3238332662725f70783d3835392c37363426666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3238332c323132)
<br>
<br>

Click  **Save & run service discovery**:

[![](https://camo.githubusercontent.com/c24aff3a21511f9be1ebe0882515b65e5bd9d991f5adf5f0e934d72d3f716399/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63656366303664392d353133612d343431392d613961362d6437643762643666323737392f6173637265656e73686f742e6a7065673f746c5f70783d302c31392662725f70783d3835392c35303026666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3139332c323132)](https://camo.githubusercontent.com/c24aff3a21511f9be1ebe0882515b65e5bd9d991f5adf5f0e934d72d3f716399/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63656366303664392d353133612d343431392d613961362d6437643762643666323737392f6173637265656e73686f742e6a7065673f746c5f70783d302c31392662725f70783d3835392c35303026666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3139332c323132)
<br>
<br>

Click  **Change**  on top right:

[![](https://camo.githubusercontent.com/c84467ec2d6796c1fdc1413f92d4bfaeaee96f0c94edd14b34a497a0df00cd05/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64303035643063372d383464372d346431642d613064332d6534356338333965656462382f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313932302c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3838312c3737)](https://camo.githubusercontent.com/c84467ec2d6796c1fdc1413f92d4bfaeaee96f0c94edd14b34a497a0df00cd05/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64303035643063372d383464372d346431642d613064332d6534356338333965656462382f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313932302c3130383026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3838312c3737)
<br>
<br>

Click  **Activate on selected sites**:

[![](https://camo.githubusercontent.com/b29ed534cb25429b7e047e0b911335479de81ef36d568facbf79912140581f40/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36616139306633312d343766652d346332332d616130352d6536306437366561646238382f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313134362c36343026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3137322c323136)](https://camo.githubusercontent.com/b29ed534cb25429b7e047e0b911335479de81ef36d568facbf79912140581f40/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36616139306633312d343766652d346332332d616130352d6536306437366561646238382f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313134362c36343026666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3137322c323136)
<br>
<br>

It will shortly say Success.

Then go to  **Setup**:

[![](https://camo.githubusercontent.com/f5ba92230b913fcd0ec4a6a6b8c51b4e21f2037d1e64ecf2b575e1ad96de5461/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33633630383433352d386431302d346166612d623833302d3737323464636438383862352f6173637265656e73686f742e6a7065673f746c5f70783d302c3132322662725f70783d3835392c36303326666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d332c323132)](https://camo.githubusercontent.com/f5ba92230b913fcd0ec4a6a6b8c51b4e21f2037d1e64ecf2b575e1ad96de5461/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33633630383433352d386431302d346166612d623833302d3737323464636438383862352f6173637265656e73686f742e6a7065673f746c5f70783d302c3132322662725f70783d3835392c36303326666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d332c323132)
<br>
<br>

Go to  **Hosts**:

[![](https://camo.githubusercontent.com/0de4cdd63f1aed04e0467950e812edaf729a5af0eb4c5de3bb4a95eb5ddfbcb0/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33396531343931352d306432612d346535642d393131352d6334326261626539363832392f6173637265656e73686f742e6a7065673f746c5f70783d302c38342662725f70783d3835392c35363526666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3130372c323132)](https://camo.githubusercontent.com/0de4cdd63f1aed04e0467950e812edaf729a5af0eb4c5de3bb4a95eb5ddfbcb0/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33396531343931352d306432612d346535642d393131352d6334326261626539363832392f6173637265656e73686f742e6a7065673f746c5f70783d302c38342662725f70783d3835392c35363526666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3130372c323132)
<br>
<br>

Hit  **Run Service Discovery**:

[![](https://camo.githubusercontent.com/3f0a74fc3a142446741031ed65ebce61b3538bdf12e9b9939d8ed9eb9a58cc2a/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36353039363666372d343664382d343062342d383563352d3538386337306465316566382f6173637265656e73686f742e6a7065673f746c5f70783d302c3134372662725f70783d3835392c36323826666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3134342c323132)](https://camo.githubusercontent.com/3f0a74fc3a142446741031ed65ebce61b3538bdf12e9b9939d8ed9eb9a58cc2a/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f36353039363666372d343664382d343062342d383563352d3538386337306465316566382f6173637265656e73686f742e6a7065673f746c5f70783d302c3134372662725f70783d3835392c36323826666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3134342c323132)
<br>
<br>

You'll start to see the system status of the EHR-Linux-Server roll in as it scans the system via the Linux agent we just installed.

Then go to  **Monitor**:

[![](https://camo.githubusercontent.com/357f1de897773635e5f1869bc0635e0d8cdbd1a190c4aeb016a150237bb9c5f5/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65373930303430312d343161312d343339392d396635302d6330373637383261343235342f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313731392c39363126666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d2d382c313330)](https://camo.githubusercontent.com/357f1de897773635e5f1869bc0635e0d8cdbd1a190c4aeb016a150237bb9c5f5/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65373930303430312d343161312d343339392d396635302d6330373637383261343235342f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313731392c39363126666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d2d382c313330)
<br>
<br>

Click  **All hosts**:

[![](https://camo.githubusercontent.com/0546cbcf20569a89761bbb6acfc094dedfeefa0e19f18bbdeb7d78f71b7a5c70/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37633832643065372d366566642d343636322d396337632d3266633663303530656166372f6173637265656e73686f742e6a7065673f746c5f70783d302c3130382662725f70783d3835392c35383926666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3131332c323132)](https://camo.githubusercontent.com/0546cbcf20569a89761bbb6acfc094dedfeefa0e19f18bbdeb7d78f71b7a5c70/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37633832643065372d366566642d343636322d396337632d3266633663303530656166372f6173637265656e73686f742e6a7065673f746c5f70783d302c3130382662725f70783d3835392c35383926666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3131332c323132)
<br>
<br>

Click on the Host name to check the progress of the scan:

[![](https://camo.githubusercontent.com/181c577cba0ab462fff7745999ccf674344cebdc06cabdb0103d4d6cd0aca647/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64666637373838392d613830362d343333342d616164382d3566336331616362623039302f6173637265656e73686f742e6a7065673f746c5f70783d302c35332662725f70783d313134362c36393426666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3132392c323737)](https://camo.githubusercontent.com/181c577cba0ab462fff7745999ccf674344cebdc06cabdb0103d4d6cd0aca647/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64666637373838392d613830362d343333342d616164382d3566336331616362623039302f6173637265656e73686f742e6a7065673f746c5f70783d302c35332662725f70783d313134362c36393426666f7263655f666f726d61743d706e672677696474683d313132302e30267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3132392c323737)
<br>
<br>

It still says it's PENDing:

[![](https://camo.githubusercontent.com/1232a3ea7a759f558fc2758567ae3509cc30395abdff3f8c229b9c1b47f5bf3b/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33353761616236372d306639322d346434632d616437332d3434366465393134663162632f6173637265656e73686f742e6a7065673f746c5f70783d302c3139332662725f70783d3835392c36373426666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3133302c323132)](https://camo.githubusercontent.com/1232a3ea7a759f558fc2758567ae3509cc30395abdff3f8c229b9c1b47f5bf3b/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f33353761616236372d306639322d346434632d616437332d3434366465393134663162632f6173637265656e73686f742e6a7065673f746c5f70783d302c3139332662725f70783d3835392c36373426666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3133302c323132)
<br>
<br>

Eventually, when the scans are complete, it will start showing more stats (as shown below):

[![](https://camo.githubusercontent.com/b26641f85a9b68a283dd755e71accf2d806eff770a34fe8b1daa46ad6136ebf6/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f32323237316163382d626165622d343038312d383632352d3339363135343137376433342f73637265656e73686f742e6a7065673f746c5f70783d37312c302662725f70783d313434382c35313426666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/b26641f85a9b68a283dd755e71accf2d806eff770a34fe8b1daa46ad6136ebf6/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f32323237316163382d626165622d343038312d383632352d3339363135343137376433342f73637265656e73686f742e6a7065673f746c5f70783d37312c302662725f70783d313434382c35313426666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

Click here:

[![](https://camo.githubusercontent.com/c6de6ea87e5d94445f7e7d13719b409414a69b2ffa82ea4abe3013ec9146beae/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64393838626335302d343364662d346439362d626661352d6664316161636462383962302f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3835392c34383026666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d392c323038)](https://camo.githubusercontent.com/c6de6ea87e5d94445f7e7d13719b409414a69b2ffa82ea4abe3013ec9146beae/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f64393838626335302d343364662d346439362d626661352d6664316161636462383962302f6173637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d3835392c34383026666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d392c323038)
<br>
<br>

Click here:

[![](https://camo.githubusercontent.com/e92fc94148b518ada3e08611c0fcedec17d06af204e2c390dab2e4dbf3dabd50/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31633038343036652d383330342d343538652d613963332d3538623362303934306537322f6173637265656e73686f742e6a7065673f746c5f70783d302c38372662725f70783d3835392c35363826666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3133312c323132)](https://camo.githubusercontent.com/e92fc94148b518ada3e08611c0fcedec17d06af204e2c390dab2e4dbf3dabd50/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31633038343036652d383330342d343538652d613963332d3538623362303934306537322f6173637265656e73686f742e6a7065673f746c5f70783d302c38372662725f70783d3835392c35363826666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3133312c323132)
<br>
<br>

While the scans are still being processed, it will look sort of blank (but it will show you now have 1 host up and running). Shortly you will see the scans start to finish and display stats about the device or server you are monitoring:

[![](https://camo.githubusercontent.com/16593b2fd32998a3bf17c6016b770f2f5aa359f482f2d5d7415aafc9fd767b10/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f39323735393230642d646263392d343839372d613766392d3434623535313733626332342f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313532312c38363426666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/16593b2fd32998a3bf17c6016b770f2f5aa359f482f2d5d7415aafc9fd767b10/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f39323735393230642d646263392d343839372d613766392d3434623535313733626332342f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313532312c38363426666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

Click on the  **1 Up**  under Host statistics to check the status of the ping:

[![](https://camo.githubusercontent.com/366ffe5a092a194004a7a445390e45b69d5f0b22c199afc6d1137d1fe7f9d86b/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37383531376461362d656131302d343731622d386532392d6230386562343334306263312f6173637265656e73686f742e6a7065673f746c5f70783d302c3131332662725f70783d3638382c34393826666f7263655f666f726d61743d706e67267761745f7363616c653d3631267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3233312c313730)](https://camo.githubusercontent.com/366ffe5a092a194004a7a445390e45b69d5f0b22c199afc6d1137d1fe7f9d86b/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37383531376461362d656131302d343731622d386532392d6230386562343334306263312f6173637265656e73686f742e6a7065673f746c5f70783d302c3131332662725f70783d3638382c34393826666f7263655f666f726d61743d706e67267761745f7363616c653d3631267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3233312c313730)
<br>
<br>

Click  **EHR-Linux-Server**:

[![](https://camo.githubusercontent.com/00e44761f4507d8419ce92b5b374239a15eb958437467d89fb3e5f5037a691e4/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31343066353566362d653731352d346566662d623961392d3737346637653831333263632f6173637265656e73686f742e6a7065673f746c5f70783d302c3133342662725f70783d3835392c36313526666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3135332c323132)](https://camo.githubusercontent.com/00e44761f4507d8419ce92b5b374239a15eb958437467d89fb3e5f5037a691e4/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31343066353566362d653731352d346566662d623961392d3737346637653831333263632f6173637265656e73686f742e6a7065673f746c5f70783d302c3133342662725f70783d3835392c36313526666f7263655f666f726d61743d706e672677696474683d383630267761745f7363616c653d3736267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3135332c323132)
<br>
<br>

The Ping will still say PENDing for a while, but eventually it will finish Pinging and look as shown below.

Now click on  **PING**:

[![](https://camo.githubusercontent.com/4d2148ab69459693e33650d6609f5c120ae995a94d86b1d815de9550f9315c61/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65623864653333342d643834352d346339342d383637372d3231613530613938653034652f757365725f63726f707065645f73637265656e73686f742e6a7065673f746c5f70783d37322c302662725f70783d313434382c36333426666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/4d2148ab69459693e33650d6609f5c120ae995a94d86b1d815de9550f9315c61/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f65623864653333342d643834352d346339342d383637372d3231613530613938653034652f757365725f63726f707065645f73637265656e73686f742e6a7065673f746c5f70783d37322c302662725f70783d313434382c36333426666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

After clicking on the Ping you will see detailed metrics such as: Packet loss, Round trip ping time, if device is up/down, etc...

[![](https://camo.githubusercontent.com/fe2939d5a47436f90baf15137d64e34b0d7aff8768be9e1fc12af6726b1f4f06/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f30306661366264652d396565652d343733332d396133372d6266393936636439623933362f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313332332c39343126666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/fe2939d5a47436f90baf15137d64e34b0d7aff8768be9e1fc12af6726b1f4f06/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f30306661366264652d396565652d343733332d396133372d6266393936636439623933362f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313332332c39343126666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

Now go back to  **Monitor**  >  **All hosts**  >  **EHR-Linux-Server**

[![](https://camo.githubusercontent.com/d72f0601898286e3257a74af94cc0c4a0f56e84aa1f769992a1bb004d4431978/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31383164343231642d643764332d343131652d393339612d3835326536653037636663622f6173637265656e73686f742e6a7065673f746c5f70783d302c3136302662725f70783d3736342c35383726666f7263655f666f726d61743d706e672677696474683d373634267761745f7363616c653d3638267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3138342c313838)](https://camo.githubusercontent.com/d72f0601898286e3257a74af94cc0c4a0f56e84aa1f769992a1bb004d4431978/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f31383164343231642d643764332d343131652d393339612d3835326536653037636663622f6173637265656e73686f742e6a7065673f746c5f70783d302c3136302662725f70783d3736342c35383726666f7263655f666f726d61743d706e672677696474683d373634267761745f7363616c653d3638267761743d31267761745f6f7061636974793d302e37267761745f677261766974793d6e6f72746877657374267761745f75726c3d68747470733a2f2f636f6c6f6e792d7265636f726465722e73332e75732d776573742d312e616d617a6f6e6177732e636f6d2f696d616765732f77617465726d61726b732f4642393233435f7374616e646172642e706e67267761745f7061643d3138342c313838)
<br>
<br>

Click on the **Check_MK Discovery** yellow WARN:

[![](https://camo.githubusercontent.com/22b1f06f92bb0a07fba8791be79b9105a3902f5c915fb18907d7c19a711f27ed/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63353561323432352d633663392d346332612d613831632d3263623566383466366239352f757365725f63726f707065645f73637265656e73686f742e6a7065673f746c5f70783d37332c302662725f70783d313434392c35323526666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/22b1f06f92bb0a07fba8791be79b9105a3902f5c915fb18907d7c19a711f27ed/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f63353561323432352d633663392d346332612d613831632d3263623566383466366239352f757365725f63726f707065645f73637265656e73686f742e6a7065673f746c5f70783d37332c302662725f70783d313434392c35323526666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

This WARN is warning that says there are several device services that are not being monitored (cpu_loads, kernel, diskstat). This is probably because I'm monitoring a Virtual Machine, but I think more investigation is needed.

[![](https://camo.githubusercontent.com/2149e267b5d408ced7b18fb803c4711b17e3a0b9ada6cd42e97269d760e5af50/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37633339303366302d663739622d343665392d623762352d6130333331303934313063332f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313535392c39313226666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/2149e267b5d408ced7b18fb803c4711b17e3a0b9ada6cd42e97269d760e5af50/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f37633339303366302d663739622d343665392d623762352d6130333331303934313063332f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313535392c39313226666f7263655f666f726d61743d706e672677696474683d313132302e30)
<br>
<br>

If you scroll down to the bottom of the page, you'll see some extra details describing this type of warning:

[![](https://camo.githubusercontent.com/d462b35f62a52ce7f526530e8fa4c1315ed1b812991306f414a3da7994e87b11/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f30343432313239352d613365382d343261372d396464322d3366323339366138346133612f757365725f63726f707065645f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313531332c38383526666f7263655f666f726d61743d706e672677696474683d313132302e30)](https://camo.githubusercontent.com/d462b35f62a52ce7f526530e8fa4c1315ed1b812991306f414a3da7994e87b11/68747470733a2f2f616a65757762687668722e636c6f7564696d672e696f2f636f6c6f6e792d7265636f726465722e73332e616d617a6f6e6177732e636f6d2f66696c65732f323032342d30382d30382f30343432313239352d613365382d343261372d396464322d3366323339366138346133612f757365725f63726f707065645f73637265656e73686f742e6a7065673f746c5f70783d302c302662725f70783d313531332c38383526666f7263655f666f726d61743d706e672677696474683d313132302e30)

# Installing and Monitoring Linux Servers with Checkmk



1\. **Part One: Installing Checkmk Monitoring on our CommandCenter machine**


2\. So here we are on our Ubuntu machine called commandcenter:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/af5da986-a797-4a20-80c3-bd59b2c9033b/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860)


3\. **Step 1** - Open a browser and go to [checkmk.com](http://checkmk.com) and hit the Download button:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/ecc56777-2bf8-49f1-aed7-ebcf58006b05/screenshot.jpeg?tl_px=0,0&br_px=643,362&force_format=png&width=860)


4\. Choose **Checkmk for Linux** and then the **Raw** edition:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/df063bee-d8fd-41e9-9c9a-ccaac3f2f14c/screenshot.jpeg?tl_px=0,0&br_px=643,364&force_format=png&width=860)


5\. **Step 2** - Choose correct Version/Platform/OS

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/adb38094-56be-4517-9058-cd868f5933e1/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860)


6\. **Step 3** - Install Checkmk

**Step 3.1** - Downloading Checkmk for Ubuntu or Debian

Pulling the package using *wget*

Copy and paste the wget command into the Ubuntu terminal:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/ef39710f-f971-431e-85cf-1b6eab6d1b9e/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860)


7\. Open Terminal:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6c54bf79-473b-49f0-9c9f-a1c98fdc2c02/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860)


8\. **Paste**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/5bbb731b-79da-43ce-8475-fbd079f3ac93/screenshot.jpeg?tl_px=0,22&br_px=643,503&force_format=png&width=860)


9\. Press **Enter**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d9badcd2-1678-4585-982b-c6a896893f2c/screenshot.jpeg?tl_px=0,22&br_px=643,503&force_format=png&width=860)


10\. **Step 3.3** - Install the Checkmk package

Now install the package including all of its dependencies.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/5b76b461-33ea-4ed5-9823-88c382bf1bf7/screenshot.jpeg?tl_px=0,0&br_px=643,362&force_format=png&width=860)


11\. Copy and paste **sudo apt install ./check-mk-raw-2.3.0p12_0.noble_amd64.deb** into terminal and press **Enter**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d535203b-4877-44aa-8836-3de0b8d4d88d/screenshot.jpeg?tl_px=0,0&br_px=643,639&force_format=png&width=1120.0)


12\. Test if the installation was successful by running the **omd version** command:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/17b9f769-03bf-43e0-a96f-72932ccd9279/screenshot.jpeg?tl_px=0,0&br_px=642,66&force_format=png&width=860)


13\. ### **Step 3.4 - Create a Checkmk monitoring site**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/c55dcdfc-73bc-4e14-8b7d-a6d9b34ffdff/screenshot.jpeg?tl_px=0,0&br_px=643,520&force_format=png&width=983)


14\. Use the **omd** command to create a new Checkmk site:

Type **sudo omd create &lt;sitename&gt;**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/1e8f3755-9fbc-4b17-951a-aa3f2b1822e4/screenshot.jpeg?tl_px=0,0&br_px=643,392&force_format=png&width=860)


15\. Notice the admin username **cmkadmin** and default password have been created for you.

Copy the auto-generated password from the terminal:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e98180af-9006-49b3-b4c0-7c138c81207d/screenshot.jpeg?tl_px=0,0&br_px=829,590&force_format=png&width=1120.0)


16\. Use the **sudo omd start &lt;sitename&gt;** command to start the site:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/3cd52f12-0c3e-4d06-b0c4-411876677e00/screenshot.jpeg?tl_px=0,0&br_px=643,189&force_format=png&width=860)


17\. Type **ip address** in terminal to get IP address of the Ubuntu machine then **copy it to clipboard**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/21fcfc06-9801-407e-93cf-b0b2cd0d18de/screenshot.jpeg?tl_px=0,0&br_px=643,474&force_format=png&width=860)


18\. While still on you Ubuntu machine, **paste the ip address into a new browser** and and add **/monitoring** after the ip address. Then press **Enter**:

For example: *192.168.7.134/monitoring*

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/308203a2-c223-4149-b64d-482abe007de4/screenshot.jpeg?tl_px=0,0&br_px=643,458&force_format=png&width=860)


19\. You then see the checkmk web login:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/fb257708-2e14-4bb0-aee3-e1445a3923ed/screenshot.jpeg?tl_px=0,0&br_px=643,416&force_format=png&width=860)


20\. Use the default Username and Password given to you in the terminal:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/98eef1d1-df5b-4e91-b754-e41a015e31d3/screenshot.jpeg?tl_px=0,0&br_px=643,293&force_format=png&width=860)


21\. **Login**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/c42a4f10-172a-469b-9462-c532034dcf64/screenshot.jpeg?tl_px=0,0&br_px=643,455&force_format=png&width=860)


22\. Once logged in, the first thing you should do is change the default password by going to **User** &gt;&gt; **Change password**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/792dfabd-6624-4bc1-a2ff-e13ff2abf785/screenshot.jpeg?tl_px=0,0&br_px=643,814&force_format=png&width=884)


23\. Now we’re done with installing checkmk onto the command center device/server and as long as it is running, we can access the monitoring dashboard from any device with a web browser.


24\. **Part Two: Installing the Checkmk Agents on the Linux Servers**


25\. So both of the Linux Servers I have running on two separate virtual machines.

On the left **EHR-Linux-Server**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7a64143c-afb4-49bd-addd-c27da0b97bdf/ascreenshot.jpeg?tl_px=0,0&br_px=1920,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=226,65)


26\. and on the right **PatientPortalWebServer**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/132d57dc-1caf-41bb-9f10-1714e00e97a6/ascreenshot.jpeg?tl_px=0,0&br_px=1920,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=603,66)


27\. For more detail you can use the Checkmk Documentation for installing monitoring agents here:

<https://docs.checkmk.com/latest/en/wato_monitoringagents.html>

The following image shows the various ways that Checkmk can access systems to be monitored:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/cd69f9d3-a826-41c2-a742-6f694ecf38a9/screenshot.jpeg?tl_px=0,23&br_px=957,664&force_format=png&width=1120.0)


28\. In the Checkmk Raw edition, you can find the agent’s Linux packages within the Web GUI via **Setup** &gt; **Agents** &gt; **Linux**


29\. So let's setup **EHR-Linux-Server** for monitoring by opening a web browser within it:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/fb9097da-4c26-4e50-8200-c5e23b1a595e/ascreenshot.jpeg?tl_px=0,118&br_px=1719,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=59,401)


30\. Type in the ip address of the CommandCenter (Ubuntu) machine, followed by the a slash and name of your site, in the search bar:

*192.168.7.134/monitoring*

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e9a20e2b-6fd2-4b33-9471-c94c28b2ad1e/ascreenshot.jpeg?tl_px=0,0&br_px=1719,961&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=255,139)


31\. **Login** with the same credentials:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/8a90b849-4c64-4ed4-987a-bffae0bb66e3/File.jpeg?tl_px=0,0&br_px=643,455&force_format=png&width=860)


32\. Go to **Setup** &gt; **Agents** &gt; **Linux**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/4e8d1980-5f9e-42eb-8a6c-5ddeadb5a3a2/user_cropped_screenshot.jpeg?tl_px=0,118&br_px=1360,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=75,361)


33\. Click on

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/eb303dc8-4dab-443a-a049-e5771ad304f1/ascreenshot.jpeg?tl_px=0,64&br_px=859,545&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=163,212)


34\. After downloading the Linux Agent package, the Checkmk documentation says to run the following as a root user:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/42d5bd0d-cb26-4fd1-b7e5-17d03af68b80/ascreenshot.jpeg?tl_px=336,87&br_px=1483,728&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=524,277)


35\. Copy the command from the documentation:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6654226e-37c6-4015-bf1c-0492eae1f9c8/ascreenshot.jpeg?tl_px=0,97&br_px=1146,738&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=507,277)


36\. Change to the Downloads folder in the terminal then paste in the command from the Checkmk docs:

*cd Downloads*

*sudo dpkg -i check-mk-agent_2.3.0p12-1_all.deb*

*enter*

**NOTE:** Make sure you change the ***check-mk-agent_2.3.0p12-1_all.deb*** in the command you copied from the documentation to match the latest version of the Linux Agent you just downloaded (as the docs may be outdated).

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/0fa1da89-fa02-424d-9ef4-07f455ad4963/screenshot.jpeg?tl_px=0,0&br_px=942,382&force_format=png&width=983)


37\. The agent installs:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d00de725-2e15-4d2b-8a9f-4ef97897df06/screenshot.jpeg?tl_px=0,0&br_px=935,543&force_format=png&width=983)


38\. Now got to **Setup** &gt; **Hosts**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/82572ea4-6b7a-472f-b41e-238b91569efc/ascreenshot.jpeg?tl_px=0,90&br_px=859,571&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=110,212)


39\. Click on **Add host to the monitoring**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7715b5c6-8c3c-4056-928a-a1adf1907976/ascreenshot.jpeg?tl_px=0,99&br_px=859,580&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=223,212)


40\. Enter the Host name

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e47f40c9-6893-4731-82a7-cd0d9c971f57/ascreenshot.jpeg?tl_px=0,102&br_px=859,583&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=366,212)


41\. **EHR-Linux-Server**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/b82ba8ec-7d97-4e95-9c42-f47ba688c133/screenshot.jpeg?tl_px=12,59&br_px=872,540&force_format=png&width=860)


42\. Click on the IP address family box:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/5b795473-949f-41e9-a8dd-b05b3bb70560/ascreenshot.jpeg?tl_px=0,172&br_px=859,653&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=286,212)


43\. Click on the IPv4 address checkbox:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6534756b-3264-4282-acf6-51cb500dde2b/ascreenshot.jpeg?tl_px=0,207&br_px=859,688&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=286,212)


44\. Then get the IP address from the terminal with the **ip address** command:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6221dfcf-1037-49eb-8e5c-df3674ab6e2b/screenshot.jpeg?tl_px=39,27&br_px=898,508&force_format=png&width=860)


45\. Input it in to the IPv4 address text area:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/bdc19601-6057-4fda-a0a3-937b455af69e/screenshot.jpeg?tl_px=0,0&br_px=968,638&force_format=png&width=1120.0)


46\. Check the box next to **Checkmk agent/API integrations**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/b82962ac-96a8-4099-9330-745b21c73342/ascreenshot.jpeg?tl_px=0,283&br_px=859,764&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=283,212)


47\. Click **Save & run service discovery**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/cecf06d9-513a-4419-a9a6-d7d7bd6f2779/ascreenshot.jpeg?tl_px=0,19&br_px=859,500&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=193,212)


48\. Click **Change** on top right:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d005d0c7-84d7-4d1d-a0d3-e45c839eedb8/ascreenshot.jpeg?tl_px=0,0&br_px=1920,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=881,77)


49\. Click **Activate on selected sites**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6aa90f31-47fe-4c23-aa05-e60d76eadb88/ascreenshot.jpeg?tl_px=0,0&br_px=1146,640&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=172,216)


50\. It will shortly say Success.

Then go to **Setup**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/3c608435-8d10-4afa-b830-7724dcd888b5/ascreenshot.jpeg?tl_px=0,122&br_px=859,603&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=3,212)


51\. Go to **Hosts**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/39e14915-0d2a-4e5d-9115-c42babe96829/ascreenshot.jpeg?tl_px=0,84&br_px=859,565&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=107,212)


52\. Hit **Run Service Discovery**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/650966f7-46d8-40b4-85c5-588c70de1ef8/ascreenshot.jpeg?tl_px=0,147&br_px=859,628&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=144,212)


53\. You'll start to see the system status of the EHR-Linux-Server roll in as it scans the system via the Linux agent we just installed.

Then go to **Monitor**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e7900401-41a1-4399-9f50-c076782a4254/ascreenshot.jpeg?tl_px=0,0&br_px=1719,961&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=-8,130)


54\. Click **All hosts**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7c82d0e7-6efd-4662-9c7c-2fc6c050eaf7/ascreenshot.jpeg?tl_px=0,108&br_px=859,589&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=113,212)


55\. Click on the Host name to check the progress of the scan:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/dff77889-a806-4334-aad8-5f3c1acbb090/ascreenshot.jpeg?tl_px=0,53&br_px=1146,694&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=129,277)


56\. It stil says it's PENDing:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/357aab67-0f92-4d4c-ad73-446de914f1bc/ascreenshot.jpeg?tl_px=0,193&br_px=859,674&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=130,212)


57\. Eventually, when the scans are complete, it will start showing more stats (as shown below):

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/22271ac8-baeb-4081-8625-396154177d34/screenshot.jpeg?tl_px=71,0&br_px=1448,514&force_format=png&width=1120.0)


58\. Click here

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d988bc50-43df-4d96-bfa5-fd1aacdb89b0/ascreenshot.jpeg?tl_px=0,0&br_px=859,480&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=9,208)


59\. Click here

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/1c08406e-8304-458e-a9c3-58b3b0940e72/ascreenshot.jpeg?tl_px=0,87&br_px=859,568&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=131,212)


60\. While the scans are still being processed, it will look sort of blank (but it will show you now have 1 host up and running). Shortly you will see the scans start to finish and display stats about the device or server you are monitoring:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/9275920d-dbc9-4897-a7f9-44b55173bc24/screenshot.jpeg?tl_px=0,0&br_px=1521,864&force_format=png&width=1120.0)


61\. Click on the **1 Up** under Host statistics to check the status of the ping:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/78517da6-ea10-471b-8e29-b08eb4340bc1/ascreenshot.jpeg?tl_px=0,113&br_px=688,498&force_format=png&wat_scale=61&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=231,170)


62\. Click **EHR-Linux-Server**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/140f55f6-e715-4eff-b9a9-774f7e8132cc/ascreenshot.jpeg?tl_px=0,134&br_px=859,615&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=153,212)


63\. The Ping will still say PENDing for a while, but eventually it will finish Pinging and look as shown below.

Now click on **PING**:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/eb8de334-d845-4c94-8677-21a50a98e04e/user_cropped_screenshot.jpeg?tl_px=72,0&br_px=1448,634&force_format=png&width=1120.0)


64\. After clicking on the Ping you will see detailed metrics such as: Packet loss, Round trip ping time, if device is up/down, etc...

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/00fa6bde-9eee-4733-9a37-bf996cd9b936/screenshot.jpeg?tl_px=0,0&br_px=1323,941&force_format=png&width=1120.0)


65\. Now go back to **Monitor** &gt; **All hosts** &gt; **EHR-Linux-Server**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/181d421d-d7d3-411e-939a-852e6e07cfcb/ascreenshot.jpeg?tl_px=0,160&br_px=764,587&force_format=png&width=764&wat_scale=68&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=184,188)


66\. Step

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/c55a2425-c6c9-4c2a-a81c-2cb5f84f6b95/user_cropped_screenshot.jpeg?tl_px=73,0&br_px=1449,525&force_format=png&width=1120.0)


67\. This WARN is warning me that there are several device services that are not being monitored (cpu_loads, kernel, diskstat). This is probably because I'm monitoring a Virtual Machine, but I think more investigation is needed.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7c3903f0-f79b-46e9-b7b5-a033109410c3/screenshot.jpeg?tl_px=0,0&br_px=1559,912&force_format=png&width=1120.0)


68\. If you scroll down to the bottom of the page, you'll see some extra details describing this type of warning:

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/04421295-a3e8-42a7-9dd2-3f2396a84a3a/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=1513,885&force_format=png&width=1120.0)
#### [Made with Scribe](https://scribehow.com/shared/Installing_and_Monitoring_Linux_Servers_with_Checkmk__czKMfEBMTsaDGIDmmFJ6Ig)



<div>
  
</div>




<h1 class="scribe-title">Installing and Monitoring Linux Servers with Checkmk</h1><br/><br/><div class="scribe-step"><p class="scribe-step-text">1. <strong>Part One: Installing Checkmk Monitoring on our CommandCenter machine</strong></p>
</div><div class="scribe-step"><p class="scribe-step-text">2. So here we are on our Ubuntu machine called commandcenter:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/af5da986-a797-4a20-80c3-bd59b2c9033b/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">3. <strong>Step 1</strong> - Open a browser and go to <a href="http://checkmk.com">checkmk.com</a> and hit the Download button:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/ecc56777-2bf8-49f1-aed7-ebcf58006b05/screenshot.jpeg?tl_px=0,0&br_px=643,362&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">4. Choose <strong>Checkmk for Linux</strong> and then the <strong>Raw</strong> edition:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/df063bee-d8fd-41e9-9c9a-ccaac3f2f14c/screenshot.jpeg?tl_px=0,0&br_px=643,364&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">5. <strong>Step 2</strong> - Choose correct Version/Platform/OS</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/adb38094-56be-4517-9058-cd868f5933e1/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">6. <strong>Step 3</strong> - Install Checkmk</p>
<p class="scribe-step-text"><strong>Step 3.1</strong> - Downloading Checkmk for Ubuntu or Debian</p>
<p class="scribe-step-text">Pulling the package using <em>wget</em></p>
<p class="scribe-step-text">Copy and paste the wget command into the Ubuntu terminal:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/ef39710f-f971-431e-85cf-1b6eab6d1b9e/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">7. Open Terminal:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6c54bf79-473b-49f0-9c9f-a1c98fdc2c02/screenshot.jpeg?tl_px=0,0&br_px=643,361&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">8. <strong>Paste</strong></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/5bbb731b-79da-43ce-8475-fbd079f3ac93/screenshot.jpeg?tl_px=0,22&br_px=643,503&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">9. Press <strong>Enter</strong></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d9badcd2-1678-4585-982b-c6a896893f2c/screenshot.jpeg?tl_px=0,22&br_px=643,503&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">10. <strong>Step 3.3</strong> - Install the Checkmk package</p>
<p class="scribe-step-text">Now install the package including all of its dependencies.</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/5b76b461-33ea-4ed5-9823-88c382bf1bf7/screenshot.jpeg?tl_px=0,0&br_px=643,362&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">11. Copy and paste <strong>sudo apt install ./check-mk-raw-2.3.0p12_0.noble_amd64.deb</strong> into terminal and press <strong>Enter</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d535203b-4877-44aa-8836-3de0b8d4d88d/screenshot.jpeg?tl_px=0,0&br_px=643,639&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">12. Test if the installation was successful by running the <strong>omd version</strong> command:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/17b9f769-03bf-43e0-a96f-72932ccd9279/screenshot.jpeg?tl_px=0,0&br_px=642,66&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">13. ### <strong>Step 3.4 - Create a Checkmk monitoring site</strong></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/c55dcdfc-73bc-4e14-8b7d-a6d9b34ffdff/screenshot.jpeg?tl_px=0,0&br_px=643,520&force_format=png&width=983"/></p><div class="scribe-step"><p class="scribe-step-text">14. Use the <strong>omd</strong> command to create a new Checkmk site:</p>
<p class="scribe-step-text">Type <strong>sudo omd create &lt;sitename&gt;</strong></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/1e8f3755-9fbc-4b17-951a-aa3f2b1822e4/screenshot.jpeg?tl_px=0,0&br_px=643,392&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">15. Notice the admin username <strong>cmkadmin</strong> and default password have been created for you.</p>
<p class="scribe-step-text">Copy the auto-generated password from the terminal:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e98180af-9006-49b3-b4c0-7c138c81207d/screenshot.jpeg?tl_px=0,0&br_px=829,590&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">16. Use the <strong>sudo omd start &lt;sitename&gt;</strong> command to start the site:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/3cd52f12-0c3e-4d06-b0c4-411876677e00/screenshot.jpeg?tl_px=0,0&br_px=643,189&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">17. Type <strong>ip address</strong> in terminal to get IP address of the Ubuntu machine then <strong>copy it to clipboard</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/21fcfc06-9801-407e-93cf-b0b2cd0d18de/screenshot.jpeg?tl_px=0,0&br_px=643,474&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">18. While still on you Ubuntu machine, <strong>paste the ip address into a new browser</strong> and and add <strong>/monitoring</strong> after the ip address. Then press <strong>Enter</strong>:</p>
<p class="scribe-step-text">For example: <em>192.168.7.134/monitoring</em></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/308203a2-c223-4149-b64d-482abe007de4/screenshot.jpeg?tl_px=0,0&br_px=643,458&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">19. You then see the checkmk web login:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/fb257708-2e14-4bb0-aee3-e1445a3923ed/screenshot.jpeg?tl_px=0,0&br_px=643,416&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">20. Use the default Username and Password given to you in the terminal:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/98eef1d1-df5b-4e91-b754-e41a015e31d3/screenshot.jpeg?tl_px=0,0&br_px=643,293&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">21. <strong>Login</strong></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/c42a4f10-172a-469b-9462-c532034dcf64/screenshot.jpeg?tl_px=0,0&br_px=643,455&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">22. Once logged in, the first thing you should do is change the default password by going to <strong>User</strong> &gt;&gt; <strong>Change password</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" height="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/792dfabd-6624-4bc1-a2ff-e13ff2abf785/screenshot.jpeg?tl_px=0,0&br_px=643,814&force_format=png&width=884"/></p><div class="scribe-step"><p class="scribe-step-text">23. Now we’re done with installing checkmk onto the command center device/server and as long as it is running, we can access the monitoring dashboard from any device with a web browser.</p>
</div><div class="scribe-step"><p class="scribe-step-text">24. <strong>Part Two: Installing the Checkmk Agents on the Linux Servers</strong></p>
</div><div class="scribe-step"><p class="scribe-step-text">25. So both of the Linux Servers I have running on two separate virtual machines.</p>
<p class="scribe-step-text">On the left <strong>EHR-Linux-Server</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7a64143c-afb4-49bd-addd-c27da0b97bdf/ascreenshot.jpeg?tl_px=0,0&br_px=1920,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=226,65"/></p><div class="scribe-step"><p class="scribe-step-text">26. and on the right <strong>PatientPortalWebServer</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/132d57dc-1caf-41bb-9f10-1714e00e97a6/ascreenshot.jpeg?tl_px=0,0&br_px=1920,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=603,66"/></p><div class="scribe-step"><p class="scribe-step-text">27. For more detail you can use the Checkmk Documentation for installing monitoring agents here:</p>
<p class="scribe-step-text"><a href="https://docs.checkmk.com/latest/en/wato_monitoringagents.html">https://docs.checkmk.com/latest/en/wato_monitoringagents.html</a></p>
<p class="scribe-step-text">The following image shows the various ways that Checkmk can access systems to be monitored:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/cd69f9d3-a826-41c2-a742-6f694ecf38a9/screenshot.jpeg?tl_px=0,23&br_px=957,664&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">28. In the Checkmk Raw edition, you can find the agent’s Linux packages within the Web GUI via <strong>Setup</strong> &gt; <strong>Agents</strong> &gt; <strong>Linux</strong></p>
</div><div class="scribe-step"><p class="scribe-step-text">29. So let's setup <strong>EHR-Linux-Server</strong> for monitoring by opening a web browser within it:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/fb9097da-4c26-4e50-8200-c5e23b1a595e/ascreenshot.jpeg?tl_px=0,118&br_px=1719,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=59,401"/></p><div class="scribe-step"><p class="scribe-step-text">30. Type in the ip address of the CommandCenter (Ubuntu) machine, followed by the a slash and name of your site, in the search bar:</p>
<p class="scribe-step-text"><em>192.168.7.134/monitoring</em></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e9a20e2b-6fd2-4b33-9471-c94c28b2ad1e/ascreenshot.jpeg?tl_px=0,0&br_px=1719,961&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=255,139"/></p><div class="scribe-step"><p class="scribe-step-text">31. <strong>Login</strong> with the same credentials:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/8a90b849-4c64-4ed4-987a-bffae0bb66e3/File.jpeg?tl_px=0,0&br_px=643,455&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">32. Go to <strong>Setup</strong> &gt; <strong>Agents</strong> &gt; <strong>Linux</strong></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/4e8d1980-5f9e-42eb-8a6c-5ddeadb5a3a2/user_cropped_screenshot.jpeg?tl_px=0,118&br_px=1360,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=75,361"/></p><div class="scribe-step"><p class="scribe-step-text">33. Click on</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/eb303dc8-4dab-443a-a049-e5771ad304f1/ascreenshot.jpeg?tl_px=0,64&br_px=859,545&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=163,212"/></p><div class="scribe-step"><p class="scribe-step-text">34. After downloading the Linux Agent package, the Checkmk documentation says to run the following as a root user:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/42d5bd0d-cb26-4fd1-b7e5-17d03af68b80/ascreenshot.jpeg?tl_px=336,87&br_px=1483,728&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=524,277"/></p><div class="scribe-step"><p class="scribe-step-text">35. Copy the command from the documentation:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6654226e-37c6-4015-bf1c-0492eae1f9c8/ascreenshot.jpeg?tl_px=0,97&br_px=1146,738&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=507,277"/></p><div class="scribe-step"><p class="scribe-step-text">36. Change to the Downloads folder in the terminal then paste in the command from the Checkmk docs:</p>
<p class="scribe-step-text"><em>cd Downloads</em></p>
<p class="scribe-step-text"><em>sudo dpkg -i check-mk-agent_2.3.0p12-1_all.deb</em></p>
<p class="scribe-step-text"><em>enter</em></p>
<p class="scribe-step-text"><strong>NOTE:</strong> Make sure you change the <em><strong>check-mk-agent_2.3.0p12-1_all.deb</strong></em> in the command you copied from the documentation to match the latest version of the Linux Agent you just downloaded (as the docs may be outdated).</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/0fa1da89-fa02-424d-9ef4-07f455ad4963/screenshot.jpeg?tl_px=0,0&br_px=942,382&force_format=png&width=983"/></p><div class="scribe-step"><p class="scribe-step-text">37. The agent installs:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d00de725-2e15-4d2b-8a9f-4ef97897df06/screenshot.jpeg?tl_px=0,0&br_px=935,543&force_format=png&width=983"/></p><div class="scribe-step"><p class="scribe-step-text">38. Now got to <strong>Setup</strong> &gt; <strong>Hosts</strong></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/82572ea4-6b7a-472f-b41e-238b91569efc/ascreenshot.jpeg?tl_px=0,90&br_px=859,571&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=110,212"/></p><div class="scribe-step"><p class="scribe-step-text">39. Click on <strong>Add host to the monitoring</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7715b5c6-8c3c-4056-928a-a1adf1907976/ascreenshot.jpeg?tl_px=0,99&br_px=859,580&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=223,212"/></p><div class="scribe-step"><p class="scribe-step-text">40. Enter the Host name</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e47f40c9-6893-4731-82a7-cd0d9c971f57/ascreenshot.jpeg?tl_px=0,102&br_px=859,583&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=366,212"/></p><div class="scribe-step"><p class="scribe-step-text">41. <strong>EHR-Linux-Server</strong></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/b82ba8ec-7d97-4e95-9c42-f47ba688c133/screenshot.jpeg?tl_px=12,59&br_px=872,540&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">42. Click on the IP address family box:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/5b795473-949f-41e9-a8dd-b05b3bb70560/ascreenshot.jpeg?tl_px=0,172&br_px=859,653&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=286,212"/></p><div class="scribe-step"><p class="scribe-step-text">43. Click on the IPv4 address checkbox:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6534756b-3264-4282-acf6-51cb500dde2b/ascreenshot.jpeg?tl_px=0,207&br_px=859,688&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=286,212"/></p><div class="scribe-step"><p class="scribe-step-text">44. Then get the IP address from the terminal with the <strong>ip address</strong> command:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6221dfcf-1037-49eb-8e5c-df3674ab6e2b/screenshot.jpeg?tl_px=39,27&br_px=898,508&force_format=png&width=860"/></p><div class="scribe-step"><p class="scribe-step-text">45. Input it in to the IPv4 address text area:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/bdc19601-6057-4fda-a0a3-937b455af69e/screenshot.jpeg?tl_px=0,0&br_px=968,638&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">46. Check the box next to <strong>Checkmk agent/API integrations</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/b82962ac-96a8-4099-9330-745b21c73342/ascreenshot.jpeg?tl_px=0,283&br_px=859,764&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=283,212"/></p><div class="scribe-step"><p class="scribe-step-text">47. Click <strong>Save &amp; run service discovery</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/cecf06d9-513a-4419-a9a6-d7d7bd6f2779/ascreenshot.jpeg?tl_px=0,19&br_px=859,500&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=193,212"/></p><div class="scribe-step"><p class="scribe-step-text">48. Click <strong>Change</strong> on top right:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d005d0c7-84d7-4d1d-a0d3-e45c839eedb8/ascreenshot.jpeg?tl_px=0,0&br_px=1920,1080&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=881,77"/></p><div class="scribe-step"><p class="scribe-step-text">49. Click <strong>Activate on selected sites</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/6aa90f31-47fe-4c23-aa05-e60d76eadb88/ascreenshot.jpeg?tl_px=0,0&br_px=1146,640&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=172,216"/></p><div class="scribe-step"><p class="scribe-step-text">50. It will shortly say Success.</p>
<p class="scribe-step-text">Then go to <strong>Setup</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/3c608435-8d10-4afa-b830-7724dcd888b5/ascreenshot.jpeg?tl_px=0,122&br_px=859,603&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=3,212"/></p><div class="scribe-step"><p class="scribe-step-text">51. Go to <strong>Hosts</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/39e14915-0d2a-4e5d-9115-c42babe96829/ascreenshot.jpeg?tl_px=0,84&br_px=859,565&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=107,212"/></p><div class="scribe-step"><p class="scribe-step-text">52. Hit <strong>Run Service Discovery</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/650966f7-46d8-40b4-85c5-588c70de1ef8/ascreenshot.jpeg?tl_px=0,147&br_px=859,628&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=144,212"/></p><div class="scribe-step"><p class="scribe-step-text">53. You'll start to see the system status of the EHR-Linux-Server roll in as it scans the system via the Linux agent we just installed.</p>
<p class="scribe-step-text">Then go to <strong>Monitor</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/e7900401-41a1-4399-9f50-c076782a4254/ascreenshot.jpeg?tl_px=0,0&br_px=1719,961&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=-8,130"/></p><div class="scribe-step"><p class="scribe-step-text">54. Click <strong>All hosts</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7c82d0e7-6efd-4662-9c7c-2fc6c050eaf7/ascreenshot.jpeg?tl_px=0,108&br_px=859,589&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=113,212"/></p><div class="scribe-step"><p class="scribe-step-text">55. Click on the Host name to check the progress of the scan:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/dff77889-a806-4334-aad8-5f3c1acbb090/ascreenshot.jpeg?tl_px=0,53&br_px=1146,694&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=129,277"/></p><div class="scribe-step"><p class="scribe-step-text">56. It stil says it's PENDing:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/357aab67-0f92-4d4c-ad73-446de914f1bc/ascreenshot.jpeg?tl_px=0,193&br_px=859,674&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=130,212"/></p><div class="scribe-step"><p class="scribe-step-text">57. Eventually, when the scans are complete, it will start showing more stats (as shown below):</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/22271ac8-baeb-4081-8625-396154177d34/screenshot.jpeg?tl_px=71,0&br_px=1448,514&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">58. Click here</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/d988bc50-43df-4d96-bfa5-fd1aacdb89b0/ascreenshot.jpeg?tl_px=0,0&br_px=859,480&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=9,208"/></p><div class="scribe-step"><p class="scribe-step-text">59. Click here</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/1c08406e-8304-458e-a9c3-58b3b0940e72/ascreenshot.jpeg?tl_px=0,87&br_px=859,568&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=131,212"/></p><div class="scribe-step"><p class="scribe-step-text">60. While the scans are still being processed, it will look sort of blank (but it will show you now have 1 host up and running). Shortly you will see the scans start to finish and display stats about the device or server you are monitoring:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/9275920d-dbc9-4897-a7f9-44b55173bc24/screenshot.jpeg?tl_px=0,0&br_px=1521,864&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">61. Click on the <strong>1 Up</strong> under Host statistics to check the status of the ping:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/78517da6-ea10-471b-8e29-b08eb4340bc1/ascreenshot.jpeg?tl_px=0,113&br_px=688,498&force_format=png&wat_scale=61&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=231,170"/></p><div class="scribe-step"><p class="scribe-step-text">62. Click <strong>EHR-Linux-Server</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/140f55f6-e715-4eff-b9a9-774f7e8132cc/ascreenshot.jpeg?tl_px=0,134&br_px=859,615&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=153,212"/></p><div class="scribe-step"><p class="scribe-step-text">63. The Ping will still say PENDing for a while, but eventually it will finish Pinging and look as shown below.</p>
<p class="scribe-step-text">Now click on <strong>PING</strong>:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/eb8de334-d845-4c94-8677-21a50a98e04e/user_cropped_screenshot.jpeg?tl_px=72,0&br_px=1448,634&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">64. After clicking on the Ping you will see detailed metrics such as: Packet loss, Round trip ping time, if device is up/down, etc...</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/00fa6bde-9eee-4733-9a37-bf996cd9b936/screenshot.jpeg?tl_px=0,0&br_px=1323,941&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">65. Now go back to <strong>Monitor</strong> &gt; <strong>All hosts</strong> &gt; <strong>EHR-Linux-Server</strong></p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/181d421d-d7d3-411e-939a-852e6e07cfcb/ascreenshot.jpeg?tl_px=0,160&br_px=764,587&force_format=png&width=764&wat_scale=68&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=184,188"/></p><div class="scribe-step"><p class="scribe-step-text">66. Step</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/c55a2425-c6c9-4c2a-a81c-2cb5f84f6b95/user_cropped_screenshot.jpeg?tl_px=73,0&br_px=1449,525&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">67. This WARN is warning me that there are several device services that are not being monitored (cpu_loads, kernel, diskstat). This is probably because I'm monitoring a Virtual Machine, but I think more investigation is needed.</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/7c3903f0-f79b-46e9-b7b5-a033109410c3/screenshot.jpeg?tl_px=0,0&br_px=1559,912&force_format=png&width=1120.0"/></p><div class="scribe-step"><p class="scribe-step-text">68. If you scroll down to the bottom of the page, you'll see some extra details describing this type of warning:</p>
</div><p class="scribe-screenshot-container"><img class="scribe-screenshot" width="560" alt="" src="https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-08-08/04421295-a3e8-42a7-9dd2-3f2396a84a3a/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=1513,885&force_format=png&width=1120.0"/></p><br/><h4 class="scribe-footer"><a href="https://scribehow.com/shared/Installing_and_Monitoring_Linux_Servers_with_Checkmk__czKMfEBMTsaDGIDmmFJ6Ig" target="_blank">Made with Scribe</a><br/></h4><br/>

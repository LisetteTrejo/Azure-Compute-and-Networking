<p align="center">
<img height="80%" width="80%" alt="Screenshot 2023-06-28 at 9 54 09 PM" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/4c1cbcaa-84c8-4aa3-9300-9f853f53af46">

</p>

<h1>Description</h1>
Create two virtual machines running Windows 10 and Linux. Work with the Azure Network Security Group (firewalls) and Wireshark (a protocol analyzer) to monitor any traffic coming through the virtual machine and other command line tools.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Wireshark
- Command line

<h2>Operating Systems Used </h2>

- Linux
- Windows 10

<h2>High-Level Deployment and Configuration Steps</h2>

- Create a resource group in Azure Containing both VMs.
- log into VM1 using remote desktop.
- Download Wireshark on VM1.
- Add an inbound rule to VM2 that allows\denys any traffic.

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="80%" height="80%" alt="1" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/932d4c68-6a21-48df-bfec-376f9f16bdd6">

</p>
<p>
Step 1, Create a resource group containing both Virtual Machines, "VM1" running Windows 10 and "VM2" running Linux.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/a0e7cc18-5608-4255-9bd4-e5cdb85c0412">
</p>
<p>
Step 2, Connect to VM1 using remote desktop with VM1's public IP address.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/327ae966-a3b6-4f1e-a924-bfcb218d9aa5">
</p>
<p>
Step 3, In VM1, download Wireshark with default settings. Once installed, you can go ahead and open the software/application. 
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/94ded8f8-503a-44c8-8643-bbfa4377a0f6">
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/ca924f09-7937-4f0d-abf7-147a8b4513bf">

</p>
<p>
Step 4, Click on the blue icon on the left corner and watch live traffic come through the virtual machine.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/e387943e-98b7-4d49-9d1d-c54f5da4d531">
</p>
<p>
Step 5, Filter traffic using ICMP and verify that no traffic is being received except ICMP traffic.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/e02af5e0-300a-4ed5-b815-9cbe53c599bc">
</p>
<p>
Step 6, Get the private IP address from VM2 through Azure.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/dfcf8291-8d02-4458-b52e-e1abc3b9a1c3">
</p>
<p>
Step 7, Go back into VM1, open up Powershell, and ping VM2's private IP address. watch as traffic is received and transmitted (only ICMP traffic).
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/6c93bab6-6016-4baf-a90e-59d229674ab5">
</p>
<p>
Step 8, Ping VM2 using perpetual ping (ping 10.0.0.5 -t), should be non-stop traffic.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/6df5ab95-1607-424d-8200-34789c61a407">
</p>
<p>
Step 9, go back to VM2 in Azure and go into its security group, within inbound security rules, create/add a new inbound rule denying any ICMP traffic.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/3736f94a-1e3f-43b4-b60f-9c77f88a2e8b">
</p>
<p>
Step 10, Go into VM1 and watch as all ICMP traffic starts getting timed out because of the inbound rule that was added.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/b4888e76-a681-42bd-9e8c-79859777b841">
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/56e03782-a306-48fc-90b4-6ed89e907dab">
</p>
<p>
Step 11, Go back into VM2's inbound security rules and edit the new rule that was added to "Allow" ICMP traffic, verify in VM1 that ICMP traffic is not being timed out. (Ctrl C to stop ping). 
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/2566b7cf-7d00-40fa-81fe-a084defaa2b3">
</p>
<p>
Step 12, Filter all traffic by SSH and SSH into VM2 through the command line using VM2's username @ (private IP address) and watch as SSH traffic comes through.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/8197faf4-5bb7-4ccd-86e1-0ec542c0a113">
</p>
<p>
Step 13, to continue logging into the SSH terminal put in the password for VM2's username. NOTE: you won't be able to see your password as it is being typed, once you are done, press Enter. Once you start typing commands you'll see traffic coming into Wireshark. To exit SSH, type "Exit" and press enter.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/6b45ce5f-be2b-431b-b87f-0f2872c1ead8">
</p>
<p>
Step 14, Set your filter to DHCP traffic in wire shark. In the command line renew VM1's IP address using the ipconfig/renew command, and watch as traffic is being received.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/04ba4b60-2d57-48d0-bb23-81767867557c">

</p>
<p>
Step 15, Set your Filter to DNS traffic and watch as some traffic comes through, In the command line see what Google's IP address is with the nslookup www.google.com command. As you press Enter, more traffic will be generated.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/e54b609e-a974-40b7-8539-4ae5e61a830a">
</p>
<p>
Step 16, Set your filter to RDP and watch as traffic comes through. It should be non-stop traffic due to VM1 being a remote desktop.
</p>
<br />

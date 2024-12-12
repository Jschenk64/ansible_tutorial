# CRA-Playbook

This is going to be awesome Ansible tutorial! 

This Ansible playbook is designed to deploy the "Techmax" website to CentOS servers. Here's a step-by-step breakdown of what each task does:

 1. **Define the Playbook:**

   - The playbook is named **"Deploy Techmax website"**.
   - It targets all hosts in the inventory.
   - It uses `become: true`, indicating tasks requiring elevated privileges (root) will be run with `sudo`.

 2. **Tasks:**

   - **Update CentOS Servers:**
     - Uses the `yum` module to update all packages (`name: "*"`) to their latest versions.
     - Ensures the package cache is refreshed.

   - **Install Apache Server:**
     - Installs the Apache HTTP server (`httpd`) using the `yum` package manager.
     - Ensures Apache is installed with the latest version.

   - **Download Web Files from GitHub:**
     - Downloads a zip file of the Techmax website's code from the specified GitHub repository URL to `/var/www/html/techmax-main.zip`.

   - **Unzip the Zip Folder:**
     - Extracts the downloaded zip file to `/var/www/html/`.
     - The `remote_src: true` parameter ensures the file is already on the server.

   - **Copy Web Files to HTML Directory:**
     - Copies all extracted files from `/var/www/html/techmax-main/` to `/var/www/html/`.

   - **Remove the Extracted Directory:**
     - Deletes the `/var/www/html/techmax-main` directory after the files have been copied.

   - **Remove the Zip File:**
     - Deletes the `/var/www/html/techmax-main.zip` file to clean up unnecessary files.

   - **Start and Enable Apache Server:**
     - Starts the Apache service and ensures it is enabled to start on boot using the `service` module.

### Summary:
The playbook updates the server, installs Apache, downloads and deploys the Techmax website files from GitHub, cleans up temporary files, and ensures the Apache web server is running and enabled. This effectively sets up the server to host the Techmax website.

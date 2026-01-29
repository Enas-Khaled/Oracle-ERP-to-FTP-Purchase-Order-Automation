# Oracle-ERP-to-FTP-Purchase-Order-Automation
An automated integration solution built using Oracle Integration Cloud (OIC) to synchronize Purchase Orders (PO) from Oracle ERP Cloud to an external vendor FTP server in real-time.

### Overview
Manual file transfers between procurement systems and vendors often lead to delays and data entry errors. This project automates the entire lifecycle:

Trigger: A Purchase Order is approved and becomes "Open" in Oracle ERP.

Process: OIC captures the event, transforms the data into a vendor-specific JSON format.

Delivery: The file is securely uploaded via the FTP Adapter to a specific directory.

### Tech Stack
Middleware: Oracle Integration Cloud (OIC) Gen 2/3

ERP: Oracle Fusion ERP Cloud

Protocol: FTP/SFTP

Data Format: JSON / XML

Tools: Xftp (for verification), OIC Mapper (XSLT)

### Project Structure
Integration: App-driven orchestrated flow.

Connections: * ERP_Cloud_Connection: To subscribe to PO events.

FTP_Connection: To deliver files to the remote server.

Pathing Configuration: * Target Directory: /home/user1/upload/users/PO

### Setup & Configuration
1. FTP Directory Setup
Ensure the target directory exists and has the correct permissions (CHMOD 755 or 775):


2. OIC Connection
Configure the FTP Adapter with the Host, Port, and SFTP credentials.

Set the Output Directory to the absolute path identified in the server configuration.

3. Transformation
Map the ERP Purchase Order Number and Line Items to the target JSON schema using the OIC Data Mapper.

### Demonstration
The workflow follows these steps:

PO Creation: A PO is created in Oracle Cloud.

Approval: Once approved, the status changes to Open.

Transmission: OIC triggers and sends a PO_%.json to the FTP server.

Verification: The file appears in Xftp with matching data integrity (Order ID verification).

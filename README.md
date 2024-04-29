#	INTRODUCTION
It has prompted the cybersecurity community to continue to think of ways on how to address the menace of ransomware in a relatively short time frame. These malicious apps, which chops victims’ data and request ransom for it return, can have a great ramification to the human, the companies, and the
 
critical infrastructure globally. Nowadays, more urgent defense measures, consist of primarily, providing better prevention, detection, and response mechanisms are needed than at any time. To close this gap, this project focuses on the detailed investigation of ransomware behaviors and countermeasures, inside a properly secured and well-managed testbed.
In order to collect important data and to know the real effect of the disruption, we designed and executed our research in a sensor mimic environment, which is safe and prevents real world harm. Such a method Our experiments yielded wonderful insights on the strengths and weaknesses current ransomware mitigation methods towards removing this signifi- cant threat to all computer users. Our research has highlighted that the operation of the current detection mechanisms are effective in identifying ransomware activities but there are good chances at the same time to improve the systems, which take less time of response and error rate. For the third point, our experiences have shown that having fall over systems as well as having those tested from time to time is paramount the recovery process.
These results are presented and elaborated in the corre- sponding sections in the body of this report. The make an invaluable contribution of their experience into the sphere of cybersecurity, thus favor the creation of more durable protec- tion against the constantly growing problem of ransomware
#	APPROACH
Our project aimed to comprehensively study the lifecycle of a ransomware attack within a controlled and secure en- vironment. To achieve this, we structured our approach into distinct phases, each crucial for understanding, simulating, de- tecting, and mitigating ransomware threats effectively. Below, we provide a detailed breakdown of each phase, along with architecture diagrams and code snippets where applicable.
A.	Ransomware Development
In the initial phase of our project, we focused on developing a custom ransomware prototype. Our goal was to create a functional ransomware script capable of encrypting files within a specified directory. The script was implemented in Python, leveraging cryptographic libraries to ensure secure encryption and decryption processes. Figure 1 illustrates the architecture of our ransomware development phase.
![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/034e0114-74e2-40e2-8375-3fa0a770c966)

Fig. 1. Architecture of Ransomware Development Phase

The Python code snippet below demonstrates the encryption function used in our ransomware script:
\small import os
from cryptography.fernet import Fernet

def encrypt_files(directory, key): cipher_suite = Fernet(key)
 
for root, _, files in os.walk(dir): for file in files:
file_path = os.path.join(root,file) with open(file_path,’rb’) as orig_file: original_data = original_file.read() encrypted_data = cipher_suite.enc(orig_data)
with open(file_path,’wb’)as enc_file: encrypted_file.write(encrypted_data)
This function encrypts all files within the specified directory using the AES encryption algorithm provided by the Cryptog- raphy library.
B.	Deployment and Infection
Once the ransomware prototype was developed, we simu- lated its deployment through various infection vectors, includ- ing phishing emails, compromised USB drives, and remote ex- ploits. Our approach involved crafting realistic attack scenarios within our controlled environment to observe how ransomware spreads and behaves. Figure 2 depicts the architecture of our deployment and infection phase.
![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/7f2b3db3-3b8e-46b5-8af2-696d31319df2)

Fig. 2. Architecture of Deployment and Infection Phase

The following Python code snippet illustrates how we simu- lated a phishing email campaign to distribute the ransomware:
import smtplib
 
msg.attach(MIMEText(body, ’plain’))

server=smtplib.SMTP(’smtp.google.com’,587) server.starttls() server.login(’attacker@example.com’, ’password’) server.sendmail(’attacker@example.com’, ’victim@example.com’, msg.as_string()) server.quit()

send_phishing_email()
This code snippet demonstrates how we sent a malicious email with an infected attachment to simulate a phishing attack.
C.	Monitoring and Detection
In the monitoring and detection phase, we implemented a robust monitoring system to detect ransomware activity within our environment. This involved real-time monitoring of file system changes, network traffic analysis, and anomaly detection techniques. Figure 3 showcases the architecture of our monitoring and detection phase.
![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/27ed2e33-a33e-4b8c-8cb1-9de6617b9411)

Fig. 3. Architecture of Monitoring and Detection Phase

The following Python code snippet demonstrates how we monitored file system changes using the ‘watchdog‘ library:
from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler
 
from email.mime.multipart import MIMEMultipart
 
from email.mime.text import MIMEText

def send_phishing_email(): msg = MIMEMultipart()
msg[’From’] = ’attacker@example.com’ msg[’To’] = ’victim@example.com’ msg[’Subject’] = ’’
body = ""
 
class FileChangeHandler(FileSystemEventHandler): def on_modified(self, event):
print(f’File {event.src_path} has been mod

def start_file_monitoring(directory): event_handler = FileChangeHandler() observer = Observer() observer.schedule
 
(event_handler, directory,recursive=Tru observer.start()
This code snippet sets up a file system event handler to monitor modifications within a specified directory.
D.	Mitigation and Recovery
Upon detecting ransomware activity, our mitigation and re- covery phase focused on isolating infected systems, containing the spread of ransomware, and initiating recovery procedures from backups. This phase aimed to minimize the impact of ransomware attacks and restore affected systems to a secure state. Figure 4 illustrates the architecture of our mitigation and recovery phase.
![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/a069a7ce-13c1-49e2-84c4-119aa28a0632)

Fig. 4. Architecture of Mitigation and Recovery Phase

Although no specific code snippet is provided for this phase, our mitigation and recovery procedures involved automated responses triggered by ransomware detection alerts, including isolating infected systems from the network and initiating file restoration processes from secure backups.
article [utf8]inputenc graphicx caption
#	RESULTS
A.	Ransomware Deployment
The ransomware tool was successfully deployed, encrypting all targeted files within the ”critical” directory, as evidenced by the screenshots and system logs.

![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/f3d37576-0622-4d1c-8c01-f939e388e9e6)

Fig. 5. Encrypted File Structure
 

 
![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/894c5c1e-fad0-49dd-b216-9169f84eeece)

Fig. 6. Encryption Process Logs

![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/940b7146-b3a9-4f3c-8b41-cb0bf29fd1dd)

Fig. 7. System Load During Encryption


B.	Infection Mechanism
Our simulated phishing email effectively delivered the ran- somware executable, leading to a high rate of infection among the test subjects.

![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/0149d7d6-633c-403d-8422-e40d9868372f)

Fig. 8. Phishing Email Simulation


C.	Monitoring and Detection
The monitoring system demonstrated a robust ability to detect ransomware activities promptly, with minimal false positives.
 
 

 


![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/e0542382-98a2-41ac-ada7-127732aa79a0)

Fig. 9. Infection Rate Statistics
![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/4908914d-4125-48ed-9dde-bc1a194b6a3d)
 
Fig. 13. Log Entries of Detected Activity


D.	Mitigation and Recovery
The response to detection was swiftly executed, isolating the infected system and restoring the integrity of the data from backups.
 











![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/832c35ed-a3aa-4c5d-9987-56665db63164)

Fig. 10. System Alerts on Infection

![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/88109ea8-725a-4785-b279-61d24f897d4f)

Fig. 11. Detection Time Line Graph

 
![image](https://github.com/KondaraoLagadapati/A-Study-Of-Ransomware-Attack-Mitigation-Virtualized-Environments/assets/148697986/21079043-8024-4be8-ae24-be5881c1aff8)

Fig. 12. Alert System Interface
 
#	CONCLUSION
The results indicate that our implementation effectively simulated the ransomware attack, with successful encryption, high infection rates, prompt detection, and efficient recovery

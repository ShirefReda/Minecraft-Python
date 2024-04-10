import os
import subprocess
import tarfile
import urllib.request

def download_file(url, filename):
    urllib.request.urlretrieve(url, filename)

def extract_tar(filename, destination):
    with tarfile.open(filename, 'r:gz') as tar:
        tar.extractall(destination)

def create_eula_file():
    with open('eula.txt', 'w') as f:
        f.write('eula=true')

def create_launch_script(ram):
    with open('lunch.py', 'w') as f:
        f.write(f'''#!/usr/bin/env python3
import subprocess

subprocess.run(["./java/jdk-17/bin/java", "-Xms{ram}g", "-Xmx{ram}g", "-jar", "./server.jar"])

print("FINISHED")
print("THX FOR TIME (Shiref Reda)")
print("fb.com/shiref.reda.official")
print("t.me/instantlly")
print("BYE")
''')

def main():
    url = input("Enter the link to download: ")
    download_file(url, 'server.jar')
    
    create_eula_file()
    
    download_java = input("Do you want to download Java? (yes/no): ")
    if download_java.lower() == 'yes':
        java_url = "https://download.java.net/java/GA/jdk17/0d483333a00540d886896bac774ff48b/35/GPL/openjdk-17_linux-x64_bin.tar.gz"
        download_file(java_url, 'java.tar.gz')
        os.makedirs('java')
        extract_tar('java.tar.gz', 'java')
        os.remove('java.tar.gz')  # Remove the compressed file after extraction
        
    create_launch = input("Do you want to create a launch script? (yes/no): ")
    if create_launch.lower() == 'yes':
        ram = input("Enter the amount of RAM in gigabytes (min is 1): ")
        create_launch_script(ram)
        os.chmod('lunch.py', 0o755)
        print("Launch script created successfully as 'lunch.py'.")

if __name__ == "__main__":
    main()

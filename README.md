import os
import zipfile

def create_folder(folder_path):

    # Create the folder if it doesn't exist

    if not os.path.exists(folder_path):

        os.makedirs(folder_path)

        print(f"Folder '{folder_path}' created.")

    else:

        print(f"Folder '{folder_path}' already exists.")

def extract_files(zip_file_path, extract_to_path):

    # Check if the zip file exists

    if not os.path.exists(zip_file_path):

        print(f"The zip file '{zip_file_path}' does not exist.")

        return

    # Open the zip file
    #print("================================================zip file path:", zip_file_path)

    with zipfile.ZipFile(zip_file_path,'r') as zip_ref:

        # Extract all contents to the specified path, replacing existing files

        zip_ref.extractall(extract_to_path)

    print(f"Files extracted to '{extract_to_path}'.")

def display_new_files(extract_to_path, old_files):

    # Get a list of all files in the extraction directory

    all_files = os.listdir(extract_to_path)

    # Find newly extracted files

    new_files = [file for file in all_files if file not in old_files]

    # Display only the new files

    print("Newly extracted files:")

    for file in new_files:

        print(file)

# Main program

zip_file_path = 'example3.zip'  # Path to your ZIP file

extract_to_path = 'extracted_folder'  # Path where you want to extract the contents

# Create the folder if it doesn't exist

create_folder(extract_to_path)

# Extract files into the folder

extract_files(zip_file_path, extract_to_path)

# Get a list of existing files before extraction

old_files = os.listdir(extract_to_path)

# Display only the newly extracted files

display_new_files(extract_to_path, old_files)

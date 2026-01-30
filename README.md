import os
import shutil

def organize_files(folder_path):
    if not os.path.exists(folder_path):
        print("Folder not found.")
        return

    for file in os.listdir(folder_path):
        file_path = os.path.join(folder_path, file)

        if os.path.isfile(file_path):
            extension = file.split(".")[-1].lower()
            folder_name = extension.upper()
            target_folder = os.path.join(folder_path, folder_name)

            if not os.path.exists(target_folder):
                os.makedirs(target_folder)

            shutil.move(file_path, os.path.join(target_folder, file))

    print("Files organized successfully ✔")

if __name__ == "__main__":
    target_folder = input("Enter the folder path to organize: ")
    or

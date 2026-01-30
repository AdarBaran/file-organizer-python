import os
import shutil

def organize_files(folder_path):
    if not os.path.exists(folder_path):
        print("Klasör yok hacı.")
        return

    for file in os.listdir(folder_path):
        file_path = os.path.join(folder_path, file)

        if os.path.isfile(file_path):
            ext = file.split(".")[-1].lower()
            ext_folder = os.path.join(folder_path, ext.upper())

            if not os.path.exists(ext_folder):
                os.makedirs(ext_folder)

            shutil.move(file_path, os.path.join(ext_folder, file))

    print("Dosyalar adam edildi ✔")

if __name__ == "__main__":
    target_folder = input("Düzenlenecek klasör yolunu gir: ")
    organize_files(target_folder)

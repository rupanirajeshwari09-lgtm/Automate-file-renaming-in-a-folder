# Task 4: Automate File Renaming in a Folder
# Using os, numpy, pandas, and matplotlib

import os
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Step 1: Folder path
folder_path = "sample_files"   # Change folder name if needed

# Step 2: Create folder if it does not exist
if not os.path.exists(folder_path):
    os.makedirs(folder_path)

# Step 3: Create sample text files
for i in range(5):
    file_name = f"oldname_{i+1}.txt"
    with open(os.path.join(folder_path, file_name), "w") as file:
        file.write(f"This is sample file {i+1}")

print("Sample files created successfully!\n")

# Step 4: Get all files in folder
files = os.listdir(folder_path)

# Step 5: Rename files automatically
renamed_files = []

for index, file in enumerate(files):
    old_path = os.path.join(folder_path, file)

    # New file naming pattern
    new_name = f"file_{index+1}.txt"
    new_path = os.path.join(folder_path, new_name)

    # Rename file
    os.rename(old_path, new_path)

    renamed_files.append(new_name)

    print(f"Renamed: {file} --> {new_name}")

# Step 6: Store renamed files using pandas
df = pd.DataFrame({
    "Renamed Files": renamed_files
})

print("\nUpdated File List:")
print(df)

# Step 7: Use numpy for file numbering
file_numbers = np.arange(1, len(renamed_files) + 1)

# Step 8: Plot renamed files using matplotlib
plt.figure(figsize=(6,4))
plt.plot(file_numbers, file_numbers, marker='o')

plt.title("Automated File Renaming")
plt.xlabel("File Number")
plt.ylabel("Renamed Count")

plt.grid(True)
plt.show()# Automate-file-renaming-in-a-folder
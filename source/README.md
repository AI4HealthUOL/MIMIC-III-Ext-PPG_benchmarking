

### Initial Setup

1. **Download Required Files**:
   - For each dataset, first generate the corresponding `signals.npy` and `metadata.csv` 
   
    You need to download the signals and metadata directly from PhysioNet. Please note that the PhysioNet WFDB signals contain multiple channels, including PPG, ECG, ABP, and RESP. Since this project only required PPG, we extracted the PPG channel from the downloaded WFDB files and converted it into .npy format.

2. **Organize Files**:
   - Create a folder named `data` in your project directory.
   - Place the downloaded `signals.npy` and `metadata.csv` files inside this `data` folder.

### Memmap and df_memmap Files Generation

1. **Run the Conversion Script**:
   - Use the `memmap_df_conversion.py` script to generate the `memmap` and `df_memmap` files.

2. **Generated Files**:
   - After running the script, the following files will be generated in the `data` folder:
     - `df_memmap.pkl`
     - `memmap.npy`
     - `memmap_meta.npz`

### Final File Organization

1. **Create a New Folder**:
   - Create a new folder to store the final set of files (this is a folder that you ahould address it later in the code) 

2. **Move Generated Files**:
   - Move the generated `df_memmap.pkl`, `memmap.npy`, and `memmap_meta.npz` files to this new folder.

3. **Download Additional Files**:
   - From the repository, download the following files located in the "extra required files" folder:
     - `mean.npy`
     - `lbl_itos.npy`
     - `std.npy`

4. **Complete the Final Folder**:
   - Place the `mean.npy`, `lbl_itos.npy`, and `std.npy` files into the new folder created in step 1.
   - This folder should now contain the following six files:
     - `df_memmap.pkl`
     - `memmap.npy`
     - `memmap_meta.npz`
     - `mean.npy`
     - `lbl_itos.npy`
     - `std.npy`

5. **Specify Path for Use**:
   - When you need to access the dataset, specify the path to this final folder using the `--data` flag in the terminal.

# Examples for processing the datasets 


# Training models for blood pressure prediction


| key        | value                                                                                                                                                                       |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| dataset    |                                                                                                                                                                    |
| model      | XResNet1d101/LeNet1d                                                                                                                       |
| script     | .../required_codes_files/main_ppg_bp.py                     |
|train command    | `python main_ppg_bp.py --data ./path/to/folder/with/six/final/files --input-size 3750 --architecture XResNet1d101/Lenet1d --finetune-dataset mimic_ppg_bp  --select-input-channel 0 --refresh-rate 1 --batch-size 512 --epoc 50 --normalize` |
| comment    |        |

# Training models for classification tasks (AF,SAA, ARRH tasks)

| key        | value                                                                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
|dataset    |                                                                                                                                                                     
| model      | XResNet1d101/XResNet1d50/Inception1d/LeNet1d                                                                                                                           |
| script     | .../required_codes_files/main_ppg_af.py                           |
| train command    | `python main_ppg_af.py --data ./path/to/folder/with/six/final/files --input-size 3750 --architecture XResNet1d101/Lenet1d --finetune-dataset mimic_ppg_af1_2/mimic_ppg_af2_2/mimic_ppg_af3_2  --select-input-channel 0 --refresh-rate 1 --batch-size 512 --epoc 50 --normalize`  |
| comment    |               |





# RRAv0_1.py - Validación de Pacientes

## Setup and run

### Option 1: Conda (`environment.yml`)
```bash
conda env create -f environment.yml
conda activate RRApp
streamlit run RRAv0_1.py
```

## Folder structure
```text
Radiology_Report_App/
├── RRAv0_1.py
├── README.md
├── requirements.txt
├── environment.yml
└── Data/
    ├── Raw/
    └── Processed/
```

### Option 2: pip (`requirements.txt`)
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
streamlit run RRAv0_1.py
```

## How to use
1. In the sidebar, upload the patient CSV (`.csv`). The app accepts `;` or `,` as the delimiter.
2. For each patient, fill:
   - `Coincidencia` (required)
   - `Dispositivos` (required; select at least one)
   - `Etiqueta`
   - `Observacion`
3. Click `Agregar` to save the updates for that patient.
4. Use `Descargar CSV actualizado` in the sidebar to download the latest validated CSV.

## Files written to disk
- Uploaded CSV is stored as `Data/Raw/<original_filename>`.
- Validated CSV is continuously saved to `Data/Processed/<base>_validado.csv`,
  where `<base>` is the uploaded filename without the extension (e.g. `Book1.csv` -> `Data/Processed/Book1_validado.csv`).

## Expected columns
The app reads columns like `subject_id`, `study_id`, `Reporte`, `URL`, `Etiqueta`, `Dispositivos_`, `Coincidencia`, and `Observacion`.
If `Etiqueta` exists, already-labeled rows (non-empty `Etiqueta`) are detected automatically.


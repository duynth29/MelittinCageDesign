# De novo Design of Protein Cages to Facilitate Melittin Production

![Melittin Cage Design Process](figs/Melittin_cage_design.gif)

This repo is about script of using SLIMshot to design cage that facilitate Melittin production. 
SLIMshot is a protein design and validation pipeline focused on de novo sequence generation and structure-based filtering for targeted binders and complexes. It integrates a diffusion-based sequence generator with SE(3)-equivariant models, topology control, AlphaFold2-based complex validation, ProteinMPNN for redesign, and PyRosetta for structural filtering and relaxation. 

# Folder Organization

- `final_binder_designs/`: Final passing designs after all filters.
  - Contains relaxed PDBs renamed with `design_name_id_relaxed_SLIM_A/B.pdb`.
- `final_binder_designs_stats.csv`: Summary table of selected binders and key scores.
- `mpnn/`: ProteinMPNN redesign outputs grouped by batch ranges.
  - `<batch_range>/binder_alone/`: Predicted structures of redesigned binders alone.
  - `<batch_range>/complex_structure/`: Predicted complexes for redesigned binders.
  - `mpnn_redesigned_binders.csv`: Combined metadata for redesigned sequences.
- `pyrosetta/`: PyRosetta relaxation/filtering outputs grouped by batch ranges.
  - `<batch_range>/relaxed_seq_[a|b]_<id>_mpnn<k>.pdb`: Relaxed chain A/B structures.
- `validation/`: AF2/ColabDesign predictions from the initial design stage.
  - `<batch_range>/`: Per-batch complex predictions and intermediate files.
  - `SLIM_structure/`: SLIM-only structure predictions used during validation.
  - `SLIM_binder_from_PG_design.csv`: Scores/metadata for validated designs.
- `trajectories/`: Sampler generation artifacts and metadata.
  - `<batch_range>/`: Per-batch generation traces/records.
  - `args.json`: Arguments used for this run (provenance).
- `figs/`: Plots and visual summaries of this run.
  - `Melittin_cage_design.gif`: Overview animation of the design workflow/results.
  - `ranking_by_ipTM.pdf`, `ipTM_distribution_*.pdf`, `design_pipeline_bar_plot.pdf`, etc.
- `1_Melittin_cage_design_analysis.ipynb`: Notebook for downstream analysis/plots.
- `top_binders/`: Optional curated copies of top designs (if populated).

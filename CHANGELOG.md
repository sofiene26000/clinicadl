# Changelog

Main changes to this code/ project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).


## ClinicaDL 1.5.1

### Fixed

* Fix retrocompatibility for new option in maps.json,

### Changed

* Change MapsManager architecture by adding Callbacks, 

### New

* Add `--fully_sharded_data_parallelism` option,
* Add `--emisions_calculator` option with codecarbon,
* Add the semi-supervised domain adaptation network proposed for the MICCAI DART workshop.
  

## ClinicaDL 1.5.0

### Fixed

* Fix `adapt` command 

### Changed

* SSIM is now executed on GPU when possible

### New

* Add new command `generate artifacts` to generate noise/contract/motion
* Add options for data augmentation
* Add fine-tuning option
* Add `--amp` for automatic mixed precision
* Add `--track_exp` option to track your parameters during training with MLflow or WandB
  


## ClinicaDL 1.4.0

### Fixed

* Fix `--diagnoses` and `--merged_tsv` option bug in `clinicadl get-labels`
* Fix Pathlib bugs 
* Fix `get_tsv_paths` function bug.
* Fix a bug for which it was impossible to use predict without specifying the splits and selection metrics.

### Changed

* Changed default batch size to 8 for `clinicadl predict`
* Changed VAEs main class

### New

* Add `--n_proc` option in `clinicadl generate` pipelines for parallelization.
* Add `--split` to `clinicadl predict`
* Add new VAE networks.
* Add pytorch function to summarize
* Add `--size_reduction` and `--size_reduction_factor` options to `clinicadl train`, `clinicadl predict` and `clinicadl interpret`.
* Add SSIM2D, SSIM3D metrics for VAE.
* Add `--save_latent_space` option to `clinicadl train` and `clinicadl predict`.
* Add `clinicadl generate trvial_motion`
* Add Data augmentation with torchio



## ClinicaDL 1.3.1

### Fixed

* Fix TypeError when running ClinicaDL.
* Fix `--extract_json` option bug in `clinicadl prepare-data`.
* Fix `clinicadl tsvtools get-labels` error finding `clinica iotools missing-modalities` output. 

### Changed

* Changed `clinicadl tsvtools get-labels` output directory.

### New 

* Add `--caps_directory` option in `clinicadl tsvtools get-labels`.
## ClinicaDL 1.3.0

### New 

* Add new command `quality-check pet-linear`.
* Add new command `generate hypometabolic`.
* Add new network architecture: `Resnet3D` and `SqueezeExcitationCNN`.
* Add `flair-linear` modality for `prepare-data` command.
* Add pytorch profiler.
* Add `--save_nifti` option for `interpret`command.
* Add `--output_dir` argument for `tsvtools get-labels` command

### Changed

** Core: **

* Transition from os to pathlib.
* Update data CI.
* Improve maps_manager.
* Change `--acq_label` option for `--tracer`.
* Update tutorial.
  

## ClinicaDL 1.2.0

### Changed

** Core: **

* Add ClinicaDL installation with pipx.
* Improve logging.
* Add method argument to the interpret command to choose between the new Grad-CAM method and the gradient method.
* Change `extract` command to `prepare-data`.
* Change output of `get-labels`, `split` and `kfold` commands to one TSV per split instead of one per label.
* Change `tsvtool` command to `tsvtools`.
* Change `tsvtools getlabels` command to `tsvtools get-labels` and remove the progression column in the TSV output.
* Add new commands: `tsvtools get-progression`, `tsvtools get-metadata`, `tsvtools prepare-experiment` (split + kfold), and `tsvtools adapt`.
* Update data CI.
* Add a new model for quality check 

### Fixed

- Fix `quality-check t1-linear` 


## ClinicaDL 1.1.1

### Changed

** Core: **

- Dependencies versions were updated in order to support Python equal or
greater than 3.8.
- Security updates for some dependencies.
- Include the `--save_tensor` and `--save_nifty` options into the `predict`
sub-command (before `save_tensor` was also subcommand`).
- Update some paper references in the documentation.
- Add a description for the available models.
- Add the flag `--model_layers` to the `clinicadl train list_models` subcommand
to visualize the model layers.

### Fixed

- Fix bug when using the `clinicadl train list_models` command.

## ClinicaDL 1.1.0

### Changed

** Core: **

- Add new VAE models for training.
- Add multiprocessing for the `extract` task. 
- Add tests to validate `resume` and `quality-check` functionalities.
- Update minimal version for first level dependencies: clinica, scikit-learn,
  scikit-image.
- Add a new Makefile to the root of the repository in order to facilitate
  sysadmin frequent tasks. The CI script was also modified.

** Command line:**

- Update of the train command line: now all actions related to training
  (resume, list models, tasks…) are sub-commands of the command `clinicadl
  train`. Task is now a sub-command, and not an argument.
- Add command to list the available models for the training task and the
  details of each model.
- Add an option to the command `save-tensor` to save the reconstruction
  outputs as nifti files.
- Add command `clinicadl train from_json` to train again the same experiment
  from a JSON file generated by ClinicaDL.

### Fixed

- Allow the user to choose the optimizer and the metric independently of the
  performed task.
- Logger does not display output according to the `--verbose` option during
  the training tasks. This behavior is fixed.
- Behavior of `resume` was changed.
- Reader to request BIDS/CAPS datasets changed its interface in the recent
  version of Clinica (>=0.5.4). Code using these functions was adapted.
- Exceptions raised are now more specific and detailed.
- Documentation was updated.


## ClinicaDL 1.0.4

### Changed

** Core: **

Switch to Poetry to manage production and development requirements.
Update requirements.
Improve metrics for multi-class settings.
Remove NaN values in input data.
Allow to choose the name of the JSON file produced by `extract`.
Improve logs.

** Command line:**
Add `selection_metrics` option in `clinicadl train` (already available in TOML file).
Print help if no argument is given.

### Fixed

Fix label code generation
Remove all occurrences of a group in a MAPS when choosing the `overwriting` option.
Fix `resume` when the training.tsv file is empty.

## ClinicaDL 1.0.3 (release bugfix)

### Fixed

- Fix import module for VAE architectures.


## ClinicaDL 1.0.2

### Changed

**Core:**

- Clinica version dependency.
- Update documentation, with proofreading.
- Change the test for `extract`.

### Fixed

- Use the GPU option on the command line interface.
- Fix the train task when invoking the CLI.
- Replace the `predict` arguments passed through the CLI.
- Fix issue when using multiple cohorts.

## ClinicaDL 1.0.1

### Changed

**Functionalities:**

- `extract` improve this functionality with more expressive and easy to understand flags.
- Change the test for `extract`.

## ClinicaDL 1.0

Welcome in **ClinicaDL 1.0.0** ! 

This is a new version of ClinicaDL with some major changes in the source code.
All the main pipelines have been refactored. ClinicaDL now used is now working
with classes instead of function for easier maintenance and better
scalability. We introduce in this version our new data structure called MAPS
to unify ClinicaDL outputs.

This release also include a major command line refactoring with the
introduction of [Click](https://click.palletsprojects.com/en/8.0.x/) library.
Major changes in several pipelines interfaces have been implemented. For
instance the preprocessing pipeline has been split. Train pipeline has also
been refactored to reduce the number of options. The goal is to make ClinicaDL
easier to use, to maintain, and adapt the command line to the MAPS.

ClinicaDL aim for more reproducibility: some configuration files are saved in
the MAPS to reproduce experiments in the same condition (with same
environment and same parameters). In addition, we added some options to fix
the random processes seed and use Pytorch's latest enhancement for a
deterministic behavior.

Other improvement and small fix have also been implemented.

Be careful this version breaks the backward compatibility with previous versions.

### Added

**Pipelines:**

- New `extract` pipeline to convert nifti images in Pytorch tensors. This
  pipeline now saves a preprocessing json file with all the information needed
  for the train pipeline.

**Core:**

- New folder structure: MAPS (Model Analysis and Processing Structure) for ClinicaDL outputs.
- New class MapsManager for MAPS to ease the interface with the MAPS: launch various tasks such as 
    training and prediction, save outputs, read files...
- Other new classes to make ClinicaDL code more scalable: SplitManager, TaskManager, Network...
- Now takes pet-linear images as possible data modality.
- Possibility to fix the seed for a deterministic behavior.

**Other:**

- New arguments for ROI in random search.

### Changed

**Pipelines:**

- `train` pipeline has now a new command line. Please see the doc for more information.
- `train` now accept a TOML configuration file to simplify the command line.
- `train resume` is now named `resume`.
- `random-search generate` is now named `random-search`
- `random-search`now use TOML configuration file instead of JSON.
- `generate` pipeline to generate synthetic dataset (random, trivial and Shepp-Logan).
- `quality-check` pipeline to perform quality check on Clinica t1-linear and t1-volume outputs.

**Core:**

- Major refactoring of the source code repository organization: now ClinicaDL core 
  respects the command line hierarchy as is in Clinica repository.
- Command line: we now use [Click](https://click.palletsprojects.com/en/8.0.x/) instead of Argparse.

**Other:**

- Console logs enhancement.
- Replace tensorboardx dependency with torch.utils.tensorboard to remove
  tensorboardx from requirement.
- GitHub repository name is now ClinicaDL and not AD-DL anymore.

- We will now use [GitHub
discussion](https://github.com/aramis-lab/clinicadl/discussions) instead of
[Google Group](https://groups.google.com/g/clinica-user).

### Deprecated

### Removed

**Pipelines:**

- `clinicadl preprocessing` pipelines have been removed. They now have new names (see above).
- `clinicadl preprocessing run` has now completely been removed. Please use Clinica for preprocessing.
- `train_from_json` pipeline has been replaced with TOML configuration file.
- `clinicadl random-search analysis` pipeline has been removed.

**Core:**

- T1-extensive preprocessing is not supported by ClinicaDL anymore.

### Fixed

- Fix multi-class classification.
- Fix classification when only one ROI is given.
- Fix tsvtools when diagnosis column value is not identical to tsv file name.
- Fix `clinicadl tsvtool split` when n_test is 1.
- Fix ROI when user provides 3D tensor for ROI.
- Fix the use of GPU on a machine with more than ong GPU (such a computer cluster). 
  ClinicaDL will now select a free GPU that as permission.
- Fix an error where diagnosis column was automatically overwritten
  by the name of the file during split or kfold.

### Security

## ClinicaDL 0.2.2

### Added

- New functionality `clinicadl random-search analysis` to obtain the histogram
  of the balanced accuracy over a random search folder.
- New functionality `clinicadl train from_json` to train a model with
  parameters defined in a JSON file.
- New functionality `clinicadl train resume` to resume a prematurely stopped
  training task.
- Possibility to learn the gray matter intensities with the binary
  classification during training, based on `t1-volume` outputs.
- Refactor code style using Black tool.

### Changed

- Previous `clinicadl random-search` is now `clinicadl random-search generate`
- Cross-validation and computational arguments of `clinicadl random-search
  generate` are now defined in `random_search.json`.
- Remove tensorboardx dependency.

## ClinicaDL 0.2.1

### Added

- the `multi_cohort` flag in train allows to train on several CAPS at the same time.

### Changed

- `clinicadl train roi` now allows any ROI defined by a mask.
- Update README.md to avoid duplicates.
- JSON files are added for `clinicadl classify` and `clinicadl tsvtool getlabels|split|kfold`

### Removed

- Scripts and data related to MedIA publication.


## ClinicaDL 0.2.0

### Added

- New functionality `clinicadl interpret`  to generate saliency maps linked
  to pretrained models based on groups of individual images.
- New functionality `clinicadl random-search` to sample random networks from a
  predefined hyperparameter space.
- Slice subparsers for `autoencoder`/`cnn`/`multicnn` to be homogeneous with other
  parsers.
- roi parser has now `multicnn` option.	
- Add generic options to command line: `--verbose`, `--version` and
  `--logname`.

### Changed

- Behaviour of `clinicadl quality-check t1-volume`.
- Simplify `clinicadl tsvtools` behaviour when using getlabels, split and
  analysis.
- Update documentation.

### Fixed

- Fix broken file when running preprocessing in t1-extensive.


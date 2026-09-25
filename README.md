# tWRM8 (temporal Worldvolume Reconstructiona and Morphometry)

**Spatiotemporal hypervolume analysis for dynamic biological signals**

`tWRM8` is a Python-based analysis platform for extracting and characterizing dynamic events from time-resolved biological imaging data.

Rather than treating a biological signal as a sequence of independent images or a static region of interest, tWRM8 represents each event as a continuous object extending through space and time. These event-centered **4D hypervolumes** can then be quantified by their morphology, duration, intensity, recurrence, propagation, interactions, and higher-order population behavior.

The goal is to make the full spatiotemporal structure of a biological event directly measurable.

## Concept

Conventional image analysis generally asks:

> What is happening in this image?

tWRM8 instead asks:

> What object does this event form across time?

A transient signal occupying coordinates

`x, y, z`

over successive values of

`t`

defines a four-dimensional structure.

tWRM8 provides tools for detecting these structures and converting them into quantitative biological descriptors.

## Core capabilities

tWRM8 supports analysis of time-resolved fluorescence and other multidimensional imaging datasets, including multichannel hyperstacks.

Current functionality includes:

- Dynamic ROI and event detection
- Threshold-based and machine-learning-assisted ROI generation
- 3D + time event reconstruction
- Event-centered hypervolume generation
- Multichannel event analysis
- Boolean operations between channels
- Temporal filtering of intersecting events
- Raw fluorescence intensity analysis
- Dynamic F/F0 quantification
- Local background correction
- Event morphology measurements
- Event duration and temporal descriptors
- Propagation analysis
- Recurrence analysis
- Population-level event characterization
- Hypervolume classification
- Automated event reports
- Disk-backed processing for large datasets
- Export of event-level analysis data
- Serialized event datasets for downstream analysis
- Fingerprint generation across recordings
- Meta-fingerprint construction
- Between-condition fingerprint comparison
- Variability visualization
- Linear discriminant analysis
- Feature-weight analysis
- Statistical export and downstream analysis

## Analysis philosophy

The fundamental analysis unit in tWRM8 is not a static ROI.

It is an **event**.

An event has:

- spatial extent
- temporal extent
- morphology
- intensity
- trajectory
- propagation behavior
- recurrence
- relationships with events in other channels

This representation allows biological signals to be compared based on their complete dynamic phenotype rather than a single amplitude, area, or time point.

## Multichannel analysis

tWRM8 can analyze channels independently or determine relationships between events across channels.

For example, in a two-channel experiment containing a particle signal in one channel and a calcium signal in another, the software can identify spatiotemporal intersections and apply temporal constraints to distinguish biologically meaningful responses.

Events can be filtered according to criteria such as:

- first appearance time
- trigger time
- response occurring before or after another event
- maximum trigger time
- experimental intervention windows

Filtered event populations can subsequently be exported for independent analysis.

## Dynamic fluorescence analysis

For dynamically changing ROIs, simple pixel-wise F/F0 calculations can become misleading because the pixels constituting an event may change over time.

tWRM8 therefore associates fluorescence measurements with the evolving event geometry itself.

This enables intensity measurements to remain tied to the biological structure as it expands, contracts, propagates, appears, or disappears.

Both raw intensity and normalized dynamic fluorescence measurements can be retained for downstream analysis.

## Fingerprints

Individual recordings can be summarized as multidimensional **dynamic fingerprints**.

A fingerprint describes the statistical behavior of the event population within a recording using selected spatiotemporal descriptors.

This allows comparisons between experimental conditions at a higher organizational level than individual events.

Multiple recordings can also be combined into **meta-fingerprints**, preserving both the central tendency and variability of each experimental condition.

## Dimensionality reduction and discrimination

tWRM8 includes tools for examining which event features contribute most strongly to differences between experimental conditions.

Linear discriminant analysis can be used to:

1. project high-dimensional fingerprints into a reduced feature space,
2. visualize separation between experimental groups,
3. identify descriptors contributing most strongly to that separation, and
4. export the underlying data for independent statistical analysis.

This allows the software to move beyond event detection toward characterization of complete dynamic phenotypes.

## Example applications

tWRM8 was designed for dynamic biological microscopy and is particularly suited to datasets involving:

- intracellular calcium signaling
- cyclic nucleotide signaling
- membrane or extracellular particle interactions
- endothelial signaling
- vascular physiology
- subcellular microdomains
- organelle-associated signaling
- propagation phenomena
- multichannel interaction experiments
- heterogeneous cellular populations

The underlying framework is not limited to a particular fluorophore, biological system, or imaging modality.

## Large datasets

Multidimensional biological imaging datasets can become extremely large.

tWRM8 includes disk-backed and adaptive processing strategies intended to reduce unnecessary duplication of image data and allow analysis of datasets that exceed practical in-memory limits.

Intermediate data and event information can be stored separately from the original image stack so that downstream visualization and fingerprint analysis do not require repeatedly loading the complete source dataset.

## Outputs

Depending on the analysis workflow, tWRM8 can generate:

- event-level measurements
- dynamic ROI traces
- raw fluorescence data
- normalized fluorescence data
- hypervolume reports
- event visualizations
- multidimensional fingerprints
- condition-level fingerprints
- variability estimates
- LDA projections
- discriminant feature weights
- analysis CSV files
- serialized event datasets
- publication-oriented figures

## Terminology

### Hypervolume

A biological event represented across three spatial dimensions and time.

### Fingerprint

A multidimensional summary of the dynamic-event population within a recording.

### Meta-fingerprint

A condition-level representation constructed from multiple recording fingerprints while retaining information about biological variability.

## Status

tWRM8 is active research software under continuing development.

Interfaces, analysis parameters, file formats, and internal representations may evolve as the platform is expanded and validated across additional biological datasets.

For scientific use, analysis parameters should be retained alongside exported datasets to ensure reproducibility.

## Citation

A formal software citation will be added as tWRM8 approaches a stable public release.

Until then, users should cite the repository and the relevant version or commit used for analysis.

## Author

**C. Michael Francis**  
Department of Physiology & Cell Biology  
University of South Alabama

## Scope

tWRM8 is intended as a general framework for quantitative analysis of dynamic biological events.

Its central premise is simple:

> **Time should be treated as part of biological morphology, not merely as the axis along which images were collected.**

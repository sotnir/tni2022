---
title: "Image Processing, Quantification, Visualization"
teaching: Self-paced
exercises: 15
instructor:
- Yukai Zou
objectives:
- "Recap what you've learned"
keypoints:
- "A summary of everything so far"
---

# Mount BIU research filestore

## DataLad

## Amazon S3 Bucket

# Organise the pseudonimysed DICOM to source folder

## Dcm2niix extract info

> sudo bash code/bids_1_dicom_to_source.sh TNI001

## Docker: why it is helpful

> sudo bash code/bids_2_source_to_rawdata.sh TNI001

## Step 1: HeudiConv

## Step 2: BIDS validator

## Defacing

Defacing refers to the processing of an anatomical MRI image so that the face is removed. Defacing is a mandatory step for anonymization of brain MRI scans. All human brain imaging data should be defaced prior to analysis and sharing.

[bids_pydeface](https://github.com/cbinyu/pydeface) by the NYU's Center for Brain Imaging is a BIDS-App that defaces images using pydeface. We will use this tool to deface the anatomical image.

> ## References
> - Eke et al., International data governance for neuroscience. [[link](https://doi.org/10.1016/j.neuron.2021.11.017)]
> - [BIDSonym](https://peerherholz.github.io/BIDSonym/)
> - Theyers et al., Multisite Comparison of MRI Defacing Software Across Multiple Cohorts. [[link](https://doi.org/10.3389/fpsyt.2021.617997)]
> - Schwarz et al., Changing the face of neuroimaging research: Comparing a new MRI de-facing technique with popular alternatives. [[link](https://doi.org/10.1016/j.neuroimage.2021.117845)]
> - Buimer et al., De-identification procedures for magnetic resonance images and the impact on structural brain measures at different ages. [[link](https://doi.org/10.1002/hbm.25459)]

(Optional) When encountering permission issue, enter the following command:
> sudo chmod a+w *

Run the following commands:

```
docker run --name Deface_container \
           --user $userID \
           --rm \
           --volume "$rawdatadir":/bids_dataset \
           cbinyu/bids_pydeface \
                 --skip_bids_validator \
                 /bids_dataset /bids_dataset participant --participant_label "${sID}"
           > "$logdir/sub-${sID}_$scriptname.log" 2>&1
```

<img src="{{ page.root }}/tni2022/assets/img/defaced.png" 
alt="Defaced image" width="80%"/>

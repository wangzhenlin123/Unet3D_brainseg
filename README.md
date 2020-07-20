# Unet3D: Brain Tissue Segmentation
<strong>Editor: Ching-Ting Kurt Lin</strong>
<br>A Unet3D model for brain tissue segmentation by using MRI T1-weighted images.<br><br>
<br><strong>Unet3D Model Diagram</strong><br>
<br><a href="https://imgur.com/juLtdhU"><img src="https://i.imgur.com/juLtdhU.png" title="Unet3D Model Diagram" /></a>

<br><strong><u>Modules needed:</u></strong><br>
numpy, nibabel, matplotlib, keras, opencv-python(cv2), skicit-image(skimage), scipy

<br><strong><u>How to Use:</u></strong><br>

<menu><li>Prepare</li><br>
<p>&nbsp;&nbsp;&nbsp;&nbsp;The structure of the files and the folders should be the same as the picture below.</p>
<a href="https://imgur.com/DGH0y10"><img src="https://i.imgur.com/DGH0y10.png" title="File Structure" width="400" /></a>

<br><li>Preprocessing</li>
  <ol><li>Convert nifti files to numpy matrices:</li>
  <li>(Optional) Data augmentation:</li></ol><br>

<br><li>Training</li>
<p>&nbsp;&nbsp;&nbsp;&nbsp;Open Python and type:
<pre>from Unet3D_brainseg.train import unet3d_train
unet3d_train(X_dir, Y_dir, output_folder, pretrained_weights, batch_size)
&#35; Args:
&#35;    X_dir: Path of the original image matrix(5-D numpy file).
&#35;    Y_dir: Path of the ground truth matrix(5-D numpy file).
&#35;    output_folder: Path to store the weight of the model and line charts of dice_coef, loss and IoU.
&#35;    pretrained_weight: Add if pretrained weight exists. Default is None.
&#35;    batch_size: Number of the samples in each iteration. Default is 1.</p></pre>
  
<br><li>Testing</li>
<p>&nbsp;&nbsp;&nbsp;&nbsp;Open Python and type:
<pre>from Unet3D_brainseg.predict import unet3d_predict
unet3d_predict(weight_dir, X_dir, ori_folder, output_folder, channel_order)
&#35; Args:
&#35;    weight_dir: Path of the weight of the model(h5 file).
&#35;    X_dir: Path of the original image matrix(5-D numpy file).
&#35;    ori_folder: Path of the original image file(3-D nifti). This path should be same as ori_folder in nii2npy function.
&#35;    output_folder: Path to store the report of the tissue segmentation.
&#35;    channel_order: The order of the channel(LCSF, LCRB, LGM, LWM, RCSF, RCRB, RGM, RWM). Default is [1,2,3,4,5,6,7,8].</p></pre></menu>

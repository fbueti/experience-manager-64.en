---
title: Camera Raw support
description: Learn how to enable Camera Raw support in Adobe Experience Manager Assets.
contentOwner: AG
feature: Developer Tools
role: Admin
exl-id: 637c57ae-55a6-4032-9821-b55839b3e567
---
# Use Camera Raw to process images {#camera-raw-support}

You can enable the Camera Raw support to process raw file formats, such as CR2, NEF, and RAF, and render the images in JPEG format. The functionality is supported in Adobe Experience Manager Assets using the [Camera Raw package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) available from Software Distribution.

>[!NOTE]
>
>The functionality supports only JPEG renditions. It is supported on Windows 64 bit, Mac OS, and RHEL 7.x.

To enable Camera Raw support in Adobe Experience Manager Assets, follow these steps:

1. Download the [Camera Raw package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) from the Software Distribution.

1. Access `https://[aem_server]:[port]/workflow`. Open the **[!UICONTROL DAM Update Asset]** workflow.

1. Open the **[!UICONTROL Process Thumbnails]** step.

1. Provide the following configuration in the **[!UICONTROL Thumbnails]** tab:

    * **[!UICONTROL Thumbnails]**: `140:100:false, 48:48:false, 319:319:false`
    * **[!UICONTROL Skip Mime Types]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![chlimage](assets/chlimage_1-334.png)

1. In the **[!UICONTROL Web Enabled Image]** tab, in the **[!UICONTROL Skip List]** field, specify `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![chlimage](assets/chlimage_1-335.png)

1. From the side panel, add the **[!UICONTROL Camera Raw/DNG Handler]** step below the **[!UICONTROL Thumbnail creation]** step.

1. In the **[!UICONTROL Camera Raw/DNG Handler]** step, add the following configuration in the **[!UICONTROL Arguments]** tab:

   * **[!UICONTROL Mime Types]**: `image/dng` and `image/x-raw-(.*)`
   * **[!UICONTROL Command]**:

     * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
     * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
     * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
     * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`

   ![chlimage_1-336](assets/chlimage_1-336.png)

1. Click **[!UICONTROL Save]**.

>[!NOTE]
>
>Ensure that the above configuration is the same as the **[!UICONTROL Sample DAM Update Asset With Camera RAW and DNG Handling Step]** configuration.

You can now import camera raw files into [!DNL Experience Manager] Assets. After you install the Camera RAW package and configure the required workflow, **[!UICONTROL Image Adjust]** option appears in the list of side panes.

   ![chlimage_1-337](assets/chlimage_1-337.png)

   *Figure: Options in the side pane*

   ![chlimage_1-338](assets/chlimage_1-338.png)

   *Figure: Use option to make lightweight edits to your images*

After saving the edits to a Camera Raw image, a new rendition `AdjustedPreview.jpg` is generated for the image. For other image types except Camera Raw, the changes are reflected in all the renditions.

## Best practices, known issues, and limitations {#best-practices}

The functionality has the following limitations:

* The functionality supports only JPEG renditions. It is supported on Windows 64 Bit, Mac OS, and RHEL 7.x.
* Metadata writeback is not supported for RAW and DNG formats.
* The Camera Raw library has limitations around the total pixels it can process at a time. Currently, it can process a maximum of 65000 pixels on the long side of a file or 512 MP whatever criteria is encountered first.

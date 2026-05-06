# QR-Code-Generator-in-Google-Colab
A simple Google Colab tutorial for creating a downloadable QR code from any URL.

## Method 1: Download and Run in Google Colab

1. Download the notebook file:

   `QR_GoogleColab.ipynb`

2. Open [Google Colab](https://colab.research.google.com/).

3. Click:

   `File > Upload notebook`

4. Upload the file:

   `QR_GoogleColab.ipynb`

5. In the notebook, replace the example URL with your own URL:

   ```python
   url = "https://www.sciencedirect.com/science/article/pii/S0141813025028880"

6. Run the notebook cell.

   `Run all`
8. The QR code will be created, displayed in Google Colab, and downloaded automatically as a PNG image.



## Method 2: Open Google Colab and Paste the Code

1. Open [Google Colab](https://colab.research.google.com/).

2. Click:

   `File > New notebook`

3. Insert a code cell.

4. Paste the following code into the code cell:

   ```python
   # Install required package
   !pip install qrcode[pil]

   import qrcode
   from PIL import Image
   from google.colab import files

   # Paste your URL here (ADD YOUR URL HERE)
   url = "https://www.sciencedirect.com/science/article/pii/S0141813025028880"

   # Create QR code
   qr = qrcode.QRCode(
       version=None,
       error_correction=qrcode.constants.ERROR_CORRECT_H,
       box_size=18,
       border=4,
   )

   qr.add_data(url)
   qr.make(fit=True)

   # Generate image
   img = qr.make_image(
       fill_color="black",
       back_color="white"
   ).convert("RGB")

   # Save file
   out_path = "sciencedirect_article_qr_code.png"
   img.save(out_path, quality=95)

   # Display QR code in Colab
   display(img)

   # Download the QR code
   files.download(out_path)

6. Run the notebook cell.

   `Run all`
8. The QR code will be created, displayed in Google Colab, and downloaded automatically as a PNG image.

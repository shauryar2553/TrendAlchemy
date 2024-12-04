# Trend Identification Model

## Overview
Fast fashion has dramatically accelerated the rate at which trends emerge, leaving consumers overwhelmed by endless options and a lack of interaction in online shopping. The result? A confusing and impersonal experience when selecting apparel. Enter TrendAlchemy, your personal stylist, powered by cutting-edge technology.
We combine data from Instagram's top influencers with advanced machine learning techniques to decode dynamic fashion trends. Our model not only identifies trending apparel, colors, and attributes but also visualizes these trends over time through insightful graphical representations.

## Objective
In a world where fashion changes in the blink of an eye, keeping up with trends can feel impossible. TrendAlchemy bridges the gap between trends and consumers, streamlining shopping on platforms like Myntra by filtering products based on the latest styles. Think of it as your budget-friendly, tech-savvy fashion guru!

## Procedure

### Data Collection

1. **Instagram Scraping**: 
   - We created an Instagram account following top fashion influencers.
   - Instagram's algorithm prioritizes popular posts in the feed.
   - Using this feature, we developed `instagram_scraper1.py`, which outputs `profile.txt`, `profiles.csv`, and `datetime.csv`, detailing profile names and timestamps of posts.
   
2. **Image Downloading**:
   - Run `syntax.txt` to download images posted after a specified timestamp, stored in `time.txt`.
   - The images are saved in a designated folder.
   - Execute `saveimages.py` to provide `profile.txt` to our software, which downloads images with custom timestamps and saves them in the required directory.

This process creates the foundational dataset for subsequent steps.

### Semantic Segmentation
Due to time constraints, we used COCO weights to pre-train our Mask-RCNN model, fine-tuning it on approximately 40,000 images from the I-Materialist Dataset on Kaggle. We utilized the Matterport implementation of Mask-RCNN, producing segmentation masks to isolate apparel from backgrounds.

### Attribute Recognition
- **Model**: An encoder-decoder model is employed, with InceptionV3 as the encoder and an LSTM-based model as the decoder.
- **Process**: Masks are fed into this model, generating a feature vector that is decoded to identify attributes.
- **Color Detection**: K-Means Clustering is used to detect colors.

The final output includes a list of trending colors and attributes for users to choose from. We deployed this model using Flask to create an interactive website, allowing users to filter products based on these attributes.

## Technologies Used
- Python
- OpenCV
- Flask
- SQL
- Jupyter

## References
- [Mask-RCNN Original Paper](https://arxiv.org/abs/1703.06870)
- [Matterport Implementation](https://github.com/matterport/Mask_RCNN)
- [Semantic Segmentation Model](https://github.com/manas3858/iMat-Fashion/)
- [Starter Kernel for iMaterialist (Kaggle)](https://www.kaggle.com/ramswaroopbhakar14/training-inception-v3-for-fashion-attributes)

run app.py to run it on local host <br>
By integrating these technologies, we aim to enhance the user's shopping experience by offering personalized and trend-based recommendations.

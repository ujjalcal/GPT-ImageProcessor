This image processor takes a Google Drive folder as input, iterates through all the image files in that folder, and sequentially processes each file using an external **OpenAI Vision API** (or a similar image processing API). The extracted information from each processed image is then stored in an output folder as summary files.  

The processing pipeline follows these steps:  
1. **Read Images** – The processor scans the input Google Drive folder for images.  
2. **API Call for Processing** – Each image is sent to an API (e.g., OpenAI Vision API) for analysis.  
3. **Extract and Store Information** – The extracted data is saved in an output folder as summaries.  
4. **Repeat Until Completion** – The process continues until all images in the input folder are processed.  

### **Batch Processing Consideration**
Currently, the processor handles images one by one in a sequential manner. However, **batch processing (e.g., processing 3 images at a time)** has not yet been implemented.  

**Justification for Sequential Processing:**  
- The API might have rate limits or restrictions that prevent batch submission.  
- Sequential execution ensures **controlled processing** without overwhelming system resources.  
- Some APIs may require independent requests per image rather than batch submission.  
- Batch processing needs additional logic to handle parallel execution, retries, and error handling.  

To improve efficiency, a batch processing mechanism can be introduced, where multiple images are processed in parallel before storing the summaries. Implementing this would optimize processing time while ensuring API constraints are respected.

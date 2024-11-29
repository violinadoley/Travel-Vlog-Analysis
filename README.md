# Travel Vlog Analysis 

This project uses **Gemini 1.5 Pro** to analyze travel vlogs and extract structured information, such as places, activities, best times to visit, traveler types, and recommended dishes. The approach caters to two types of videos:

1. **Videos with audio voiceovers**
2. **Videos without audio voiceovers**

The focus is on improving output accuracy and minimizing irrelevant information while adapting to diverse content styles.

---

## Approach

### Videos with Audio Voiceovers
1. **Audio Extraction**: Extract the audio from the video using `yt-dlp`.
2. **Transcription**: Convert the audio to text using the **Whisper** model.
3. **Analysis**: Use **Gemini 1.5 Pro** to analyze the transcription with a clear prompt for insights.

### Videos without Audio Voiceovers
1. **Frame Extraction**: Extract frames from the video at regular intervals using **OpenCV**.
2. **Scene Description**: Process the frames using a vision-language model like **BLIP** to generate captions.
3. **Analysis**: Analyze the scene descriptions using **Gemini 1.5 Pro**.

---

## Example Outputs

### Output for Videos Without Audio Voiceovers

1. **Cityscape with Pagoda**
   - **Name**: Unspecified City (likely in East Asia)
   - **Description**: Features a prominent pagoda tower with a mountain backdrop.
   - **Type**: City
   - **Relevant Information**:
     - **Best time to visit**: Not specified
     - **Type of traveler**: Cultural and historical enthusiasts
     - **Potential local cuisine**: East Asian dishes

2. **Serene Countryside**
   - **Name**: Unspecified Countryside
   - **Description**: Green fields, blue skies, and blossoming trees.
   - **Type**: Experience
   - **Relevant Information**:
     - **Best time to participate**: Spring (due to blossoms)
     - **Who might enjoy it**: Nature lovers, tranquility seekers

3. **Festive Atmosphere**
   - **Name**: Unspecified Festival/Celebration
   - **Description**: Vibrant scene with colorful flags and balloons.
   - **Type**: Experience
   - **Relevant Information**:
     - **Best time to participate**: Not specified
     - **Who might enjoy it**: Festival enthusiasts, culture lovers

(Additional scenes continue similarly...)

---

### Output for Videos With Audio Voiceovers

1. **Tokyo (Arrival)**
   - **Description**: Arrival at Tokyo airport, navigating public transport.
   - **Type**: City
   - **Relevant Information**:
     - **Best time to visit**: Not specified (fall mentioned as crowded)
     - **Type of traveler**: Urban explorers
     - **Potential local cuisine**: Not experienced yet

2. **Shinagawa Prince Hotel (Tokyo)**
   - **Description**: Room tour showcasing amenities like a bathroom, vanity, and beds.
   - **Type**: Hotel
   - **Relevant Information**:
     - **Target audience**: Budget-conscious travelers
     - **Overall vibe**: Practical and comfortable

3. **Cat Temple (Gotokuji Temple)**
   - **Description**: Known for its cat figurines and association with good luck.
   - **Type**: Landmark
   - **Relevant Information**:
     - **Historical significance**: Maneki-neko beckoning cat tradition
     - **Key features**: Numerous cat figurines

(Additional destinations continue similarly...)

---

## Strategies to Reduce Hallucinations

1. **Handling Missing Information**: Explicitly instructing the model to mention "Not specified" for missing data prevents hallucinations.
2. **Temperature Adjustment**: Lowering the model's temperature reduces creative but inaccurate outputs.
3. **Categorization by Type**: Introducing a "Type" field (e.g., city, hotel, activity) ensures relevant details for each category.
4. **Specific Information Requests**: Including clear instructions on the information required for each "Type" guides the model effectively.

---

## Improvements to the Model's Output

1. **Clearer Instructions and Roles**: Defining the model's role as a "travel expert" enhances task understanding.
2. **Emphasis on Formatting**: Requesting well-structured and easy-to-read output improves presentation quality.
3. **Prompt Refinement**: Iteratively improving the prompt with feedback helps the model align better with expectations.

---

This demonstrates how **Gemini 1.5 Pro** can effectively extract and organize travel insights from diverse video content, catering to different user needs and enhancing travel planning experiences.

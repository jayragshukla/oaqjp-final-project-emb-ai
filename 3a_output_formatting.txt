import json
import requests


def emotion_detector(text_to_analyse):
    url = "https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict"
    headers = {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"}
    myobj = {"raw_document": {"text": text_to_analyse}}
    try:
        response = requests.post(url, json=myobj, headers=headers)
        formatted_response = json.loads(response.text)
        if 'emotionPredictions' not in formatted_response:
            print("Unexpected response format:", formatted_response)
            return None
        return formatted_response['emotionPredictions'][0]['emotion']
    except (requests.exceptions.RequestException, requests.exceptions.ConnectionError) as e:
        print(f"An error occurred: {e}")
        if response.status_code == 400:
            return None
        return None

from EmotionDetection.emotion_detection import emotion_detector
import unittest


class TestEmotionDetection(unittest.TestCase):
    def test_emotion_detection(self):
        result_1 = emotion_detector("I am glad this happened")
        self.assertEqual(result_1["joy"], 0.83237535)
        result_2 = emotion_detector("I am really mad about this")
        self.assertEqual(result_2["anger"], 0.6674731)
        result_3 = emotion_detector("I feel disgusted just hearing about this")
        self.assertEqual(result_3["disgust"], 0.9193782)
        result_4 = emotion_detector("I am so sad about this")
        self.assertEqual(result_4["sadness"], 0.9819713)
        result_5 = emotion_detector("I am really afraid that this will happen")
        self.assertEqual(result_5["fear"], 0.9907291)


unittest.main()

# Speech2Text_Text2Speech
This task has for main goals : 
1- creating service of converting speech to text 
2- extract text to a .txt file
3- link chatbot with the service to send the file (text extractred)
4- reply (read) the bot reply (from chatbot) and save it into .mp3 file.
5- The full package is appended in the files (transcribe.py) after the modification. as well as a demo .txt and .mp3 file.
6- I said "training" to the bot and it replies with the proper answer and saved it into .mp3 file.
7- I face some difficulties at the beginning since I am a new to python but things with tries and goggling go quickly easier.
8 - Thanks to those who are helping us - motivating us all the time - all SmartMethods trainers , faculty , Engineers and supervisors.


Here are some points which builds this task : 

Firstly , we need to import the needed libraries which are : 
#import TTS
from ibm_watson import TextToSpeechV1
from ibm_cloud_sdk_core.authenticators import IAMAuthenticator

#import play sound
from playsound import playsound
#import ibm chatbot
from ibm_watson import AssistantV2
import json
-------------------------------------------------------------------------------------------------------------
We need also to setup text to speech via APIKEY and url : (in my case - not general ):
#This is text to speech for ibm watson
apikey = "389U7hD9D60LkqXKAGwChsiO5-JuwTxsdjPLFGNyaQIs"
url = "https://api.us-south.text-to-speech.watson.cloud.ibm.com/instances/175e2811-9c41-4d4c-a315-6396c49db9f7"
#setup service
authenticator = IAMAuthenticator(apikey)
#new TTS service
tts = TextToSpeechV1(authenticator=authenticator)
#set service url
tts.set_service_url(url)
---------------------------------------------------------------------------------------------------------------

Then we should connect to the chatbot via the server(by session id) and disable SSL verfication : 
#this is chtabot authenticator
        authenticator = IAMAuthenticator('X8QqTW_qZwOq5cZfZBrdvbOty3DjVlg4nge_yUJtS0SW')
        assistant = AssistantV2(
        version='2021-08-03',
        authenticator=authenticator
         )
        assistant.set_service_url('https://api.eu-de.assistant.watson.cloud.ibm.com/instances/6e058c70-ecba-414f-9c21-dfac352dfcfc')
        assistant.set_disable_ssl_verification(True) 
        
-----------------------------------------------------------------------------------------------------------------------
sending text to the bot and get the text from chatbot : I got help from instructors (supervisors) as well as (IBM cloud python ) section.

# Bot-speech polish recognition
#Polish speech recognition and processing to text

#Need library
import speech_recognition as sr
import pyttsx3 as tts


r = sr.Recognizer()
engine = tts.init()

#speed speech
engine.setProperty('rate', 150)

def talk(text):
    engine.say(text)
    engine.runAndWait()

def getText():
    with sr.Microphone() as source:
        try:
            print("Słucham...\nmożesz mówić")
            audio = r.listen(source)
            text = r.recognize_google(audio, language="pl-PL")
            if text != "":
                return text
            return 0
        except:
            return 0
while True:
    txt = getText()
    if not txt == 0:
        print(txt)
        talk(txt)
        break
    else:
        print("Nie udało się rozpoznac ")
        continue

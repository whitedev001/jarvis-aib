# jarvis-aib
sudo apt update
sudo apt install -y python3 python3-pip git zip unzip \
openjdk-17-jdk build-essential
pip install kivy buildozer
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.label import Label
from kivy.uix.textinput import TextInput
from kivy.uix.button import Button

class JarvisApp(App):
    def build(self):
        layout = BoxLayout(orientation='vertical', padding=10, spacing=10)

        self.chat = Label(text="Hello! I am JARVIS 🤖", size_hint_y=0.3)
        self.input = TextInput(hint_text="Type your command...")
        btn = Button(text="Ask JARVIS")

        btn.bind(on_press=self.reply)

        layout.add_widget(self.chat)
        layout.add_widget(self.input)
        layout.add_widget(btn)

        return layout

    def reply(self, instance):
        user = self.input.text.lower()

        if "time" in user:
            self.chat.text = "JARVIS: I can’t tell time yet ⏰"
        elif "hello" in user:
            self.chat.text = "JARVIS: Hello Sir!"
        else:
            self.chat.text = "JARVIS: Command not understood 🤖"

        self.input.text = ""

JarvisApp().run()
buildozer init
title = JARVIS AI
package.name = jarvis
package.domain = org.jarvis
requirements = python3,kivy

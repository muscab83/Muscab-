# Muscab-
Muscab.py
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.label import Label
from kivy.uix.button import Button
from kivy.uix.popup import Popup
from kivy.clock import Clock

class MainLayout(BoxLayout):
    def __init__(self, **kwargs):
        super().__init__(orientation='vertical', padding=20, spacing=10, **kwargs)

        self.add_widget(Label(text="Wi-Fi Networks", font_size='20sp'))

        self.networks = ["Home WiFi", "School Network", "Cafe_Wifi_123", "Open_Network", "MuscabNet"]
        for net in self.networks:
            btn = Button(text=net, on_press=self.fake_hack)
            self.add_widget(btn)

    def fake_hack(self, instance):
        popup = Popup(title='Hacking...',
                      content=Label(text='Please wait...'),
                      size_hint=(None, None), size=(300, 200))
        popup.open()

        Clock.schedule_once(lambda dt: self.show_result(popup), 3)

    def show_result(self, popup):
        popup.dismiss()
        result_popup = Popup(title='Access Denied',
                             content=Label(text='This network is secured.\nTry another one.'),
                             size_hint=(None, None), size=(300, 200))
        result_popup.open()

class MuscabApp(App):
    def build(self):
        self.title = 'Muscab Wi-Fi Hacker'
        return MainLayout()

if __name__ == '__main__':
    MuscabApp().run()

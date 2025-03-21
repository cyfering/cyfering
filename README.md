import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QWidget, QGridLayout, QPushButton


class CustomButton(QPushButton):
    absenta = 0  

    def __init__(self, text, parent=None):
        super().__init__(text, parent)
        self.setStyleSheet('font-size : 15px;')
        self.clicked.connect(self.on_click)  

    def on_click(self):

        CustomButton.absenta += 1
        self.setText(f'Clicked {CustomButton.absenta} times')
        print(CustomButton.absenta)


class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle('TESTING...')
        self.setGeometry(0, 0, 1500, 1500)
        self.initUI()

    def initUI(self):

        central_widget = QWidget(self)
        self.setCentralWidget(central_widget)
        grid_layout = QGridLayout(central_widget)


        self.button1 = CustomButton('9:00 Managementul Serviciilor')
        self.button2 = CustomButton('9:00 Managementul Operational')
        self.button3 = CustomButton('16:30 Proiecte Economice')
        self.button4 = CustomButton('18:00 Proiecte Economice')
        self.button5 = CustomButton('7:30 Analiza Strategica')
        self.button6 = CustomButton('9:00 IMM')
        self.button7 = CustomButton('9:00 Tehnici profesionale')


        grid_layout.addWidget(self.button1, 1, 0)
        grid_layout.addWidget(self.button2, 1, 1)
        grid_layout.addWidget(self.button3, 3, 2)
        grid_layout.addWidget(self.button4, 4, 2)
        grid_layout.addWidget(self.button5, 1, 3)
        grid_layout.addWidget(self.button6, 1, 3)
        grid_layout.addWidget(self.button7, 1, 4)


def main():
    app = QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec_())


if __name__ == '__main__':
    main()

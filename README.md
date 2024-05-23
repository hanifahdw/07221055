PyQt5 import QtCore, QtGui, QtWidgets

from menu_ohm import MenuOHM
from menu_gaya import MenuGaya
from menu_daya import MenuDaya
from menu_glb import MenuGLB

class MenuWindow(object):
    def MenuUI (self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(500, 500)
        self.centralwidget = QtWidgets.QWidget(MainWindow)
        self.centralwidget.setObjectName("centralwidget")

        self.judul = QtWidgets.QLabel(self.centralwidget)
        self.judul.setGeometry(QtCore.QRect(100, 50, 400, 50))
        self.judul.setFont(QtGui.QFont('Arial', 20))
        self.judul.setObjectName("judul")

        self.subjudul = QtWidgets.QLabel(self.centralwidget)
        self.subjudul.setGeometry(QtCore.QRect(150, 75, 400, 50))
        self.subjudul.setObjectName("subjudul")

        self.radioButton = QtWidgets.QRadioButton(self.centralwidget)
        self.radioButton.setGeometry(QtCore.QRect(100, 100, 200, 50))
        self.radioButton.setObjectName("radioButton")

        self.radioButton_2 = QtWidgets.QRadioButton(self.centralwidget)
        self.radioButton_2.setGeometry(QtCore.QRect(100, 125, 200, 50))
        self.radioButton_2.setObjectName("radioButton_2")

        self.radioButton_3 = QtWidgets.QRadioButton(self.centralwidget)
        self.radioButton_3.setGeometry(QtCore.QRect(100, 150, 200, 50))
        self.radioButton_3.setObjectName("radioButton_3")

        self.radioButton_4 = QtWidgets.QRadioButton(self.centralwidget)
        self.radioButton_4.setGeometry(QtCore.QRect(100, 175, 200, 50))
        self.radioButton_4.setObjectName("radioButton_4")

        self.radiogroup = QtWidgets.QButtonGroup()
        self.radiogroup.addButton(self.radioButton)
        self.radiogroup.addButton(self.radioButton_2)
        self.radiogroup.addButton(self.radioButton_3)
        self.radiogroup.addButton(self.radioButton_4)

        self.btn_lanjut = QtWidgets.QPushButton(self.centralwidget)
        self.btn_lanjut.setGeometry(QtCore.QRect(150, 220, 200, 50))
        self.btn_lanjut.setObjectName("btn_lanjut")
        self.btn_lanjut.clicked.connect(self.lanjut)

        MainWindow.setCentralWidget(self.centralwidget)
        self.statusbar = QtWidgets.QStatusBar(MainWindow)
        self.statusbar.setObjectName("statusbar")
        MainWindow.setStatusBar(self.statusbar)

        self.retranslateUi(MainWindow)

    def lanjut(self):
        if self.radioButton.isChecked():
            self.window = QtWidgets.QMainWindow()
            self.ui = MenuOHM()
            self.ui.MenuOHMUI(self.window)
            self.window.show()
        elif self.radioButton_2.isChecked():
            self.window = QtWidgets.QMainWindow()
            self.ui = MenuGaya()
            self.ui.MenuGayaUI(self.window)
            self.window.show()
        elif self.radioButton_3.isChecked():
            self.window = QtWidgets.QMainWindow()
            self.ui = MenuDaya()
            self.ui.MenuDayaUI(self.window)
            self.window.show()
        elif self.radioButton_4.isChecked():
            self.window = QtWidgets.QMainWindow()
            self.ui = MenuGLB()
            self.ui.MenuGLBUI(self.window)
            self.window.show()
        

    def retranslateUi(self, MainWindow):
        _translate = QtCore.QCoreApplication.translate
        MainWindow.setWindowTitle(_translate("MainWindow", "Rumus Fisika"))
        self.judul.setText(_translate("MainWindow", "Kalkulator Rumus Fisika"))
        self.subjudul.setText(_translate("MainWindow", "Pilih salah satu rumus di bawah ini:"))
        self.radioButton.setText(_translate("MainWindow", "Hukum OHM"))
        self.radioButton_2.setText(_translate("MainWindow", "Gaya"))
        self.radioButton_3.setText(_translate("MainWindow", "Daya"))
        self.radioButton_4.setText(_translate("MainWindow", "GLB"))
        self.btn_lanjut.setText(_translate("MainWindow", "Lanjut"))


if __name__ == "__main__":
    import sys
    app = QtWidgets.QApplication(sys.argv)
    MainWindow = QtWidgets.QMainWindow()
    ui = MenuWindow()
    ui.MenuUI(MainWindow)
    MainWindow.show()
    sys.exit(app.exec_())

# Paint-Application
------------------------------------------------------------------
## Introduction
A Paint Application is a Main window application where you can draw with your mouse what you want with specification of size and color of Pen ,you can also clear all the content of image or  a part with white color,finally you can save the image as format png ,or close the application.</br>
![image](https://user-images.githubusercontent.com/93142901/152665942-81340109-8c21-4501-aba6-6cde52287e40.png)
## PaintApplication(interior design)
The first step for creating any application is building the interface ,For do this task we will use QT Designer for creating an MainWindow Application As you see in the image(for central widgt we used the  code to input image in the central widget) :
![image](https://user-images.githubusercontent.com/93142901/152666407-7c3b5fb5-6a61-46dd-b820-9175e937a53f.png)
## PaintApplication(Functionality)
 An application to respond to a mouse mouvement.
 we must use the following events :
 ```cpp
  //evenemet de peinture
 void paintEvent(QPaintEvent *e) override;
 //l'evenement d'appui sur la souris
 void mousePressEvent(QMouseEvent *e) override;
 //l'evenement de deplacement de la souris 
 void mouseMoveEvent(QMouseEvent *e) override ;
 //evenements de relachement de la souris 
  void mouseReleaseEvent(QMouseEvent *e) override ;
 ```
For implementation of paintEvent 




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
For implementation of mousePressEvent :
```cpp
 void PaintAPP::mousePressEvent(QMouseEvent *e){

    //nous appuyons sur la souris
    //on active la peinture
    ispaint=true;
    //le premiere point c'est la position de cursus
    Begin=e->pos();
    e->accept();

  }
``` 
wen we press on mouse we will activate the variable ispaint for degin the paint from the position of the mouse(Begin).</br>

For implementation of mouseMoveEvent :
```cpp
 void PaintAPP::mouseMoveEvent(QMouseEvent *e){
    if(!ispaint){
       e->accept();
       return;
    }
    QPen pen(color);
    pen.setCapStyle(Qt::RoundCap);
    pen.setWidth(size);
    Painter->setPen(pen);
    End=e->pos();
    //paint une line qui a un point de depart la positin de cursus et un point de fin la position final de cursus
    Painter->drawLine(Begin,End);
    Begin=End;
     update();
    e->accept();
}
``` 
When we draw we check if ispaint is activated or not if is activated we draw the a line tha has as the first position of cursus as a begin point and the final position as a end point,we must update for update the operation.</br>
For implementation of mouseReleaseEvent :
```cpp
  void PaintAPP::mouseReleaseEvent(QMouseEvent *e){
   ispaint=false;
   e->accept();
   }
``` 
for mouseRelease event is for desactivate the paint if we the user not press the mouse
### Pen Size Action
When the user click on this action he will show a small dialog where he can input the Pen Size value, we will get this value and put it in a size variable and set as a pen whidth.</br>
```cpp
  
void PaintAPP::on_actionPen_Size_triggered()
{
   size=QInputDialog::getInt(this, "choose your pen size","Pen size :",30 ,1);
}
```
### Color Action
```cpp
 void PaintAPP::on_actionColor_triggered()
{
    color =QColorDialog::getColor(Qt::black,this,"color de  ");

 }
```
When the user click on this action ,he will show a small dialog where he can choose an color value, we will get this value and put it in a color variable and set as a pen color.</br>
### Save Action
```cpp
   void PaintAPP::on_actionSave_triggered()
   {
    QString fileName = QFileDialog::getSaveFileName(this, tr("Save Image File"),
                                                    QString(),tr("Images (*.png)"));
    if (!fileName.isEmpty())
    {
      Image->save(fileName);
    }
   }
 ```
  When the user click on this action ,he will show a small dialog where he can choose when he want save his image as a png format.</br>
### Clear All Action
```cpp
 void PaintAPP::on_actionClear_All_triggered()
  {
     Image->fill(Qt::white);
     update();
 }
   
```
for clear the content we fill the image with the original color ;white.
### AboutQt Action
```cpp
   void PaintAPP::on_actionAbout_Qt_triggered()
  {

  QMessageBox ::aboutQt(this,"about QT");
  }
   
```
we use a message box for display informations about Qt
### Go Action
```cpp
void PaintAPP::on_actionGo_triggered()
{
    close();
}
   
```
for close the application we use the methode close()
## Conclusion
this application is a very basic application every one can do it ,i am sorry because i couldn't  create more options as we saw in class QPainter and more Actions .






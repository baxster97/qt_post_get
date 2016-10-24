# qt_post_get
This is an example to make HTTP POST and GET requests in Qt with C++
I have been uploaded all files of the project, but the main things are:

1)Add QT += network in .pro

2)include important Qnetwork libraries
#include <QtNetwork/QNetworkAccessManager>
#include <QtNetwork/QNetworkRequest>
#include <QtNetwork/QNetworkReply>
#include <QHttpMultiPart>
#include <QUrl>
#include <QUrlQuery>

3)GET REQUEST EXAMPLE
    QEventLoop eventLoop;
    QNetworkAccessManager mgr;
    QObject::connect(&mgr, SIGNAL(finished(QNetworkReply*)), &eventLoop, SLOT(quit()));
    QNetworkRequest req( QUrl( QString("http://test.com/test.php?get=test")));   //DON'T FORGET TO CHANGE
    QNetworkReply *reply = mgr.get(req);
    eventLoop.exec();
    
4)POST REQUEST EXAMPLE
    QEventLoop eventLoop;
    QNetworkAccessManager manager;
    QUrl url("http://test.com/test.php"); //DON'T FORGET TO CHANGE
    QNetworkRequest request(url);
    request.setHeader(QNetworkRequest::ContentTypeHeader, "application/x-www-form-urlencoded");
    QObject::connect(&manager, SIGNAL(finished(QNetworkReply*)), &eventLoop, SLOT(quit()));
    QNetworkReply *reply = manager.post(request,"get=name");
    eventLoop.exec();

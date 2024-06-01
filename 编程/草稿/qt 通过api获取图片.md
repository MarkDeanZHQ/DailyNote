# 1

## 临时保存图片
> 如果你需要在应用程序退出时删除临时保存的多张图片，你可以使用 QTemporaryDir 来创建临时目录，并在退出时删除整个目录。以下是一个简单的示例代码，演示了如何使用 QTemporaryDir 保存多张图片并在退出时删除：

```cpp
#include <QCoreApplication>
#include <QNetworkAccessManager>
#include <QNetworkRequest>
#include <QNetworkReply>
#include <QFile>
#include <QDir>
#include <QTemporaryDir>
#include <QCoreApplication>

class ImageDownloader : public QObject {
    Q_OBJECT

public:
    ImageDownloader(QObject *parent = nullptr) : QObject(parent) {
        manager = new QNetworkAccessManager(this);

        // 替换为你要下载的图片 URL 列表
        imageUrls = {
            QUrl("https://example.com/image1.jpg"),
            QUrl("https://example.com/image2.jpg"),
            // Add more URLs as needed
        };

        // 连接信号槽
        connect(manager, &QNetworkAccessManager::finished, this, &ImageDownloader::onFinished);

        // 创建临时目录
        if (tempDir.isValid()) {
            qDebug() << "Temporary directory created:" << tempDir.path();
        } else {
            qDebug() << "Failed to create temporary directory.";
        }
    }

    void downloadImages() {
        for (const QUrl &imageUrl : imageUrls) {
            // 发送 GET 请求下载图片
            QNetworkRequest request(imageUrl);
            manager->get(request);
        }
    }

    void cleanup() {
        // 删除临时目录及其内容
        tempDir.remove();
        qDebug() << "Temporary directory deleted:" << tempDir.path();
    }

private slots:
    void onFinished(QNetworkReply *reply) {
        if (reply->error() == QNetworkReply::NoError) {
            // 从网络回复中读取图片数据
            QByteArray imageData = reply->readAll();

            // 创建临时文件
            QFile file(tempDir.filePath(QString("downloaded_image_%1.jpg").arg(imageCounter++)));
            if (file.open(QIODevice::WriteOnly)) {
                // 将图片数据保存到临时文件
                file.write(imageData);
                file.close();
                qDebug() << "Image saved to" << file.fileName();
            } else {
                qDebug() << "Failed to save image.";
            }
        } else {
            qDebug() << "Download failed:" << reply->errorString();
        }

        // 如果所有图片都已经下载完成，执行清理操作
        if (imageCounter == imageUrls.size()) {
            cleanup();
            QCoreApplication::quit();
        }

        // 清理资源
        reply->deleteLater();
    }

private:
    QNetworkAccessManager *manager;
    QVector<QUrl> imageUrls;
    QTemporaryDir tempDir;
    int imageCounter = 0;
};

int main(int argc, char *argv[]) {
    QCoreApplication app(argc, argv);

    // 创建 ImageDownloader 对象
    ImageDownloader downloader;

    // 下载多张图片并保存到临时目录
    downloader.downloadImages();

    return app.exec();
}

#include "main.moc"

```

> 在这个示例中，我使用 QTemporaryDir 创建了一个临时目录，用于保存多张图片。在 onFinished 函数中，我创建了临时文件并将图片数据保存到这些文件中。当所有图片都下载完成后，执行 cleanup 函数，删除整个临时目录及其内容。你需要替换 imageUrls 为你要下载的图片 URL 列表。


### 保存图片

> 你可以使用 Qt 的 QNetworkAccessManager 来下载图片并保存到本地文件。以下是一个简单的示例代码，演示了如何通过 URL 获取图片并保存到本地：

```cpp
#include <QCoreApplication>
#include <QNetworkAccessManager>
#include <QNetworkRequest>
#include <QNetworkReply>
#include <QFile>
#include <QDir>

class ImageDownloader : public QObject {
    Q_OBJECT

public:
    ImageDownloader(QObject *parent = nullptr) : QObject(parent) {
        manager = new QNetworkAccessManager(this);

        // 替换为你要下载的图片 URL
        imageUrl = QUrl("https://example.com/image.jpg");

        // 连接信号槽
        connect(manager, &QNetworkAccessManager::finished, this, &ImageDownloader::onFinished);
    }

    void downloadImage(const QString &outputFilePath) {
        // 发送 GET 请求下载图片
        QNetworkRequest request(imageUrl);
        manager->get(request);

        // 保存图片的本地路径
        saveFilePath = outputFilePath;
    }

private slots:
    void onFinished(QNetworkReply *reply) {
        if (reply->error() == QNetworkReply::NoError) {
            // 从网络回复中读取图片数据
            QByteArray imageData = reply->readAll();

            // 将图片数据保存到本地文件
            QFile file(saveFilePath);
            if (file.open(QIODevice::WriteOnly)) {
                file.write(imageData);
                file.close();
                qDebug() << "Image saved to" << saveFilePath;
            } else {
                qDebug() << "Failed to save image.";
            }
        } else {
            qDebug() << "Download failed:" << reply->errorString();
        }

        // 清理资源
        reply->deleteLater();
        QCoreApplication::quit();
    }

private:
    QNetworkAccessManager *manager;
    QUrl imageUrl;
    QString saveFilePath;
};

int main(int argc, char *argv[]) {
    QCoreApplication app(argc, argv);

    // 创建 ImageDownloader 对象
    ImageDownloader downloader;

    // 替换为你想保存的本地文件路径
    QString localFilePath = QDir::currentPath() + "/downloaded_image.jpg";

    // 下载图片并保存到本地文件
    downloader.downloadImage(localFilePath);

    return app.exec();
}

#include "main.moc"

```
> 在这个例子中，ImageDownloader 类继承自 QObject，它使用 QNetworkAccessManager 发送 GET 请求下载图片，然后将图片数据保存到本地文件。你只需要将 imageUrl 替换为你要下载的图片 URL，将 localFilePath 替换为你想保存的本地文件路径。这个示例使用了同步的方式，如果你需要异步下载，可以在 onFinished 函数中处理下载完成的逻辑。


## 查询字符串/文件唯一名
>在Qt中，你可以使用QUrl类来处理和构建URL，包括自定义查询字符串。以下是一个简单的例子，演示如何创建带有自定义查询字符串的URL：

```cpp
#include <QCoreApplication>
#include <QUrl>
#include <QUrlQuery>
#include <QDebug>

int main(int argc, char *argv[])
{
    QCoreApplication a(argc, argv);

    // 创建一个QUrl对象
    QUrl url("https://example.com");

    // 创建一个QUrlQuery对象
    QUrlQuery query;

    // 添加查询字符串参数
    query.addQueryItem("r18", "1");
    query.addQueryItem("keyword", "白丝");
    query.addQueryItem("num", "3");

    // 将QUrlQuery对象附加到QUrl对象
    url.setQuery(query);

    // 输出构建完成的URL
    qDebug() << "Custom URL with Query String: " << url.toString();

    return a.exec();
}

```
> 在这个例子中，首先创建了一个QUrl对象，然后使用addQueryItem方法添加查询字符串的参数和值。最后，通过toString方法将QUrl对象转换为字符串，以输出构建完成的URL。

### 文件唯一名
> 在Qt中，你可以使用QUuid类生成唯一的随机标识符，作为图片文件的名称。QUuid生成的标识符是基于UUID (Universally Unique Identifier) 的，几乎是唯一的。 

以下是一个示例，演示如何生成随机的文件名并保存图片：
```cpp
#include <QCoreApplication>
#include <QImage>
#include <QDir>
#include <QUuid>
#include <QDateTime>
#include <QDebug>

void saveImage(const QImage &image, const QString &folderPath)
{
    // 生成唯一的文件名
    QString fileName = QUuid::createUuid().toString().remove('{').remove('}');
    fileName.append(".png");

    // 构建完整的文件路径
    QString filePath = folderPath + QDir::separator() + fileName;

    // 保存图片
    if (image.save(filePath)) {
        qDebug() << "Image saved successfully:" << filePath;
    } else {
        qDebug() << "Failed to save image:" << filePath;
    }
}

int main(int argc, char *argv[])
{
    QCoreApplication a(argc, argv);

    // 指定保存图片的文件夹路径
    QString folderPath = "path/to/your/folder";

    // 创建一个简单的 QImage，你可以替换成你的实际图像数据
    QImage sampleImage(100, 100, QImage::Format_RGB32);
    sampleImage.fill(Qt::red);

    // 批量保存图片，可以根据你的需要调整次数
    for (int i = 0; i < 10; ++i) {
        saveImage(sampleImage, folderPath);
    }

    return a.exec();
}


```

>在这个例子中，QUuid::createUuid()生成一个UUID，然后通过toString()转换为字符串形式，最后通过简单的处理得到文件名。这个文件名可以用于保存图片。请确保指定了正确的文件夹路径。
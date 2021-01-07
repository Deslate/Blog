# Control the camera

2019.11.16. 10:00

This passage is written in Chinese since there it's almost the same as the English version on [official website](https://developer.android.com/training/camera/cameradirect.html#java).

> 直接使用安卓框架API

> 建议在主线程 `onCreate()`中新开一个线程去打开`Camerea`.

## 1.释放并打开相机

使用 `Camera.open()` 可能会抛出异常, 要使用 `try`.

> 自从API 9开始, 相机框架开始支持多个摄像头. 如果你使用旧版 API 然后在没有参数的情况下调用 `open()` , 你会打开第一个后置摄像头

以下是一个官方示例：

```java
private boolean safeCameraOpen(int id) {
    boolean qOpened = false;

    try {
        releaseCameraAndPreview();
        camera = Camera.open(id);
        qOpened = (camera != null);
    } catch (Exception e) {
        Log.e(getString(R.string.app_name), "failed to open Camera");
        e.printStackTrace();
    }

    return qOpened;
}

private void releaseCameraAndPreview() {
    preview.setCamera(null);
    if (camera != null) {
        camera.release();
        camera = null;
    }
}
```

## 2. 创建相机预览

用户在按下快门键时经常需要看到预览。你可以使用`SurfaceView`来显示你的相机传感器采集到的数据。

### 预览类

为了进行预览，你需要创建预览类。预览类需要实现（implement）`android.view.SurfaceHolder.Callback`接口，这个接口用于将图片信息从相机硬件传给应用程序。

```java
class Preview extends ViewGroup implements SurfaceHolder.Callback {

    SurfaceView surfaceView;
    SurfaceHolder holder;

    Preview(Context context) {
        super(context);

        surfaceView = new SurfaceView(context);
        addView(surfaceView);

        // 加载一个SurfaceHolder.Callback来让我们可以在下层surface被创建和销毁时得到通知
        holder = surfaceView.getHolder();
        holder.addCallback(this);
        holder.setType(SurfaceHolder.SURFACE_TYPE_PUSH_BUFFERS);
    }
...
}
```

正如下面要讲的，预览类必须在动态图像显示被启动之前传递给相机类。

### 设置和启动预览

一个相机实例和与他相关的预览必须以特定的顺序创建：相机在前。在下面的代码中，初始化相机的过程被概括，所以一旦用户改变相机，`Camera.startPreview()`就会在`setCamera()` 方法中被调用。

```java
public void setCamera(Camera camera) {
    if (mCamera == camera) { return; }

    stopPreviewAndFreeCamera();

    mCamera = camera;

    if (mCamera != null) {
        List<Size> localSizes = mCamera.getParameters().getSupportedPreviewSizes();
        supportedPreviewSizes = localSizes;
        requestLayout();

        try {
            mCamera.setPreviewDisplay(holder);
        } catch (IOException e) {
            e.printStackTrace();
        }

        // 重点：调用startPreview()来更新预览界面。预览必须在你能拍照之前开启
        mCamera.startPreview();
    }
}
```

## 调整相机设置

相机设置可以改变相机拍照的方式，从缩放级别到曝光补偿。下面这个例子只改变了预览大小。

```java
@Override
public void surfaceChanged(SurfaceHolder holder, int format, int w, int h) {
    // Now that the size is known, set up the camera parameters and begin
    // the preview.
    Camera.Parameters parameters = mCamera.getParameters();
    parameters.setPreviewSize(previewSize.width, previewSize.height);
    requestLayout();
    mCamera.setParameters(parameters);

    // Important: Call startPreview() to start updating the preview surface.
    // Preview must be started before you can take a picture.
    mCamera.startPreview();
}
```

### 设置预览的方向

大多数相机应用程序将显示锁定到横向模式，因为这是相机传感器的自然方向。此设置不会阻止您拍摄肖像模式的照片，因为设备的方向记录在EXIF头中。setCameradPlayOrientation（）方法允许您更改预览的显示方式，而不影响图像的录制方式。但是，在API级别14之前的Android中，必须在更改方向之前停止预览，然后重新启动它。

## 拍照

一旦预览开始，使用[`Camera.takePicture()`](https://developer.android.com/reference/android/hardware/Camera.html#takePicture(android.hardware.Camera.ShutterCallback, android.hardware.Camera.PictureCallback, android.hardware.Camera.PictureCallback)) 方法来拍照。你可以创建[`Camera.PictureCallback`](https://developer.android.com/reference/android/hardware/Camera.PictureCallback.html) 和 [`Camera.ShutterCallback`](https://developer.android.com/reference/android/hardware/Camera.ShutterCallback.html) 对象并把它们传递给[`Camera.takePicture()`](https://developer.android.com/reference/android/hardware/Camera.html#takePicture(android.hardware.Camera.ShutterCallback, android.hardware.Camera.PictureCallback, android.hardware.Camera.PictureCallback)) . 如果你想不停抓取图像，你可以创建一个实现[`onPreviewFrame()`](https://developer.android.com/reference/android/hardware/Camera.PreviewCallback.html#onPreviewFrame(byte[], android.hardware.Camera)) 的 [`Camera.PreviewCallback`](https://developer.android.com/reference/android/hardware/Camera.PreviewCallback.html) 

对于介于两者之间的内容，您可以仅捕获选定的预览帧，或设置延迟操作以调用[`takePicture()`](https://developer.android.com/reference/android/hardware/Camera.html#takePicture(android.hardware.Camera.ShutterCallback, android.hardware.Camera.PictureCallback, android.hardware.Camera.PictureCallback))。

### 重启预览

拍摄完一张照片后，必须重新启动预览，用户才能拍摄另一张照片。在本例中，通过重载快门按钮来完成重新启动。

```java
@Override
public void onClick(View v) {
    switch(previewState) {
    case K_STATE_FROZEN:
        camera.startPreview();
        previewState = K_STATE_PREVIEW;
        break;

    default:
        camera.takePicture( null, rawCallback, null);
        previewState = K_STATE_BUSY;
    } // switch
    shutterBtnConfig();
}
```

## 停止预览，释放相机

当预览界面被销毁时释放相机。以下是预览类中的方法

```java
@Override
public void onClick(View v) {
    switch(previewState) {
    case K_STATE_FROZEN:
        camera.startPreview();
        previewState = K_STATE_PREVIEW;
        break;

    default:
        camera.takePicture( null, rawCallback, null);
        previewState = K_STATE_BUSY;
    } // switch
    shutterBtnConfig();
}
```


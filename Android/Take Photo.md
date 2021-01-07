# Take photo 

[Preference: lesson form official ducument](https://developer.android.com/training/camera/photobasics)

(to be completed)

> This lesson teaches how to capture a photo by [delegating]( [delegate.md](../English/Vocabulary/delegate.md) ) the work to another camera app on the device.

> (If you'd rather build your own camera functionality, see [Controlling the Camera](https://developer.android.com/training/camera/cameradirect.html).([See My note](Control the camera.md))



```java
static final int REQUEST_IMAGE_CAPTURE = 1;

private void dispatchTakePictureIntent() {
    Intent takePictureIntent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
    if (takePictureIntent.resolveActivity(getPackageManager()) != null) {
        startActivityForResult(takePictureIntent, REQUEST_IMAGE_CAPTURE);
    }
}
```

```java
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    if (requestCode == REQUEST_IMAGE_CAPTURE && resultCode == RESULT_OK) {
        Bundle extras = data.getExtras();
        Bitmap imageBitmap = (Bitmap) extras.get("data");
        imageView.setImageBitmap(imageBitmap);
    }
}
```


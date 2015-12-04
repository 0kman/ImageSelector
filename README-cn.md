# Android Image Selector
 

## Demo
 
 #### [English Doc](https://github.com/yancyworld/ImageSelector/blob/master/README.md)
 
 
![](https://github.com/yancyworld/ImageSelector/blob/master/resource/ImageSelector.gif)

[Download Apk](https://github.com/yancyworld/ImageSelector/blob/master/resource/app-debug.apk)
 
## ʹ��˵��

### ����һ��

#### �� Gradle ��Ӧ�� imageselector ����

```groovy
dependencies {
        compile 'com.android.support:appcompat-v7:22.2.1'
        compile 'com.android.support:support-v4:22.2.1'
        
        compile 'com.yancy.imageselector:imageselector:1.0.0'
        
}
```



### �������

�� `AndroidManifest.xml` �� ��� ����Ȩ��

```xml
<!-- ��sdcard�ж�ȡ���ݵ�Ȩ�� -->
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<!-- ��sdcard��д�����ݵ�Ȩ�� -->
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<!-- ��sdcard�д���/ɾ���ļ���Ȩ�� -->
<uses-permission android:name="android.permission.MOUNT_UNMOUNT_FILESYSTEMS" />


```

�� `AndroidManifest.xml` ��  `application` �ڵ���  ��� ���� Activity

```xml
<activity
    android:name="com.yancy.imageselector.ImageSelectorActivity"
    android:configChanges="orientation|screenSize" />
    

```


### ��������

�����´�����ӵ� ����Ҫ��ת�� λ����
 
```java
private static int REQUEST_IMAGE = 1;


    Intent intent = new Intent(MainActivity.this, ImageSelectorActivity.class);  
    
    intent.putExtra(ImageSelectorActivity.EXTRA_SHOW_CAMERA, true);     // �Ƿ������  Ĭ�� ����
    
    intent.putExtra(ImageSelectorActivity.EXTRA_SELECT_COUNT, 9);      //  ���������ѡ�������ÿ�ѡͼƬ��������� Ĭ�� 9 ��
    
    /**
     * ����ģʽ
     * ��ѡ  :    ImageSelectorActivity.MODE_SINGLE
     * ��ѡ  :    ImageSelectorActivity.MODE_MULTI
     */
    intent.putExtra(ImageSelectorActivity.EXTRA_SELECT_MODE, ImageSelectorActivity.MODE_MULTI);     // ��ѡ
    
    startActivityForResult(intent, REQUEST_IMAGE);

```        
 
��  `onActivityResult` �л�ȡѡ�е���Ƭ·�� ���� :
 
```java
    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        if (requestCode == REQUEST_IMAGE && resultCode == RESULT_OK && data != null) {
        
            // Get Image Path List
            List<String> pathList = data.getStringArrayListExtra(ImageSelectorActivity.EXTRA_RESULT);

            for (String path : pathList) {
                Log.i("ImagePathList", path);
            }

        }
    }
```

[����ʾ��](https://github.com/yancyworld/ImageSelector/blob/master/app/src/main/java/com/yancy/imageselectordemo/MainActivity.java)
 
====
 

## Thanks

- [Glide](https://github.com/bumptech/glide)

##About me
 
I am a student in mainland China. I love Google, love Android, love everything that is interesting. If you get any problems when using this library or you have an internship opportunity, please feel free to [email me](mailto:yancy_world@outlook.com). :smiley:

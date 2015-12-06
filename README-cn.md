# ImageSelector ���
Android�Զ�����ᣬʵ�������ա�ͼƬѡ�񣨵�ѡ/��ѡ����ImageLoader�ް� ���ɿ�����ѡ��

## Demo
 
#### [Ӣ�İ��ĵ�](https://github.com/yancyworld/ImageSelector/blob/master/README.md)
 
 
![](https://github.com/yancyworld/ImageSelector/blob/master/resource/ImageSelector.gif)

[Download Apk](https://raw.githubusercontent.com/YancyYe/ImageSelector/master/resource/app-debug.apk)
 

## ��������
* UI�ظ�
* ���й��ܿ�����
* ���OOM���
* ͼƬ�ֶ�ѡ��
* ֧�ֺ����Ӣ��


## ��ͼչʾ
![](https://github.com/YancyYe/ImageSelector/blob/master/resource/ImageSelector.png)

 
## ʹ��˵��

### ����һ��

#### ͨ��Gradleץȡ

```groovy
dependencies {
    compile 'com.yancy.imageselector:imageselector:1.1.0'
}
```



### �������

�� `AndroidManifest.xml` �� ��� ����Ȩ��

```xml
<!-- ��sdcard�ж�ȡ���ݵ�Ȩ�� -->
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<!-- ��sdcard��д�����ݵ�Ȩ�� -->
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />

```


### ��������

#####���� ͼƬ������ (���п��԰��� ϲ��  ʹ�ò�ͬ�� ������ͼƬ���ؿ�� ����ΪGlideʾ��)


```java
public class GlideLoader implements com.yancy.imageselector.ImageLoader {

    @Override
    public void displayImage(Context context, String path, ImageView imageView) {
        Glide.with(context)
                .load(path)
                .placeholder(com.yancy.imageselector.R.mipmap.imageselector_photo)
                .centerCrop()
                .into(imageView);
    }

}

```    

##### ����ImageSelector

```java
 ImageConfig imageConfig
        = new ImageConfig.Builder(MainActivity.this , new GlideLoader())
        // ����� 4.4 ���ϣ����޸�״̬����ɫ ��Ĭ�Ϻ�ɫ��
        .steepToolBarColor(getResources().getColor(R.color.blue))
        // ����ı�����ɫ ��Ĭ�Ϻ�ɫ��
        .titleBgColor(getResources().getColor(R.color.blue))
        // �ύ��ť�������ɫ  ��Ĭ�ϰ�ɫ��
        .titleSubmitTextColor(getResources().getColor(R.color.white))
        // ������ɫ ��Ĭ�ϰ�ɫ��
        .titleTextColor(getResources().getColor(R.color.white))
        // ������ѡ   ��Ĭ��Ϊ��ѡ��  (��ѡ Ϊ singleSelect)
        .mutiSelect()
        // ��ѡʱ���������   ��Ĭ�� 9 �ţ�
        .mutiSelectMaxSize(9)
        // ��ѡ���ͼƬ·��
        .pathList(path)
        // ���պ��ŵ�ͼƬ·����Ĭ�� /temp/picture��
        .filePath("/ImageSelector/Pictures")
        // �������չ��� ��Ĭ�Ͽ�����
        .showCamera()
        .build();


ImageSelector.open(imageConfig);   // ����ͼƬѡ����
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

[����ʾ��](https://github.com/YancyYe/ImageSelector/blob/master/app/src/main/java/com/yancy/imageselectordemo/MainActivity.java)
 
====
 
## ��������
* QQ: 297555818
* Email: [yancy_world@outlook.com](mailto:yancy_world@outlook.com)

## Thanks

- [Glide](https://github.com/bumptech/glide)

##About me
 
I am a student in mainland China. I love Google, love Android, love everything that is interesting. If you get any problems when using this library or you have an internship opportunity, please feel free to [email me](mailto:yancy_world@outlook.com). :smiley:

## License
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

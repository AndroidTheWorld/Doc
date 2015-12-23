Android-Gradle�����ű�����
------

### Build.gradle

������һ��Android module�ڵ�build.gradle�ű���Gradle�ǻ���Groovy��һ��DSL�������ض����ԣ����ԣ���gradle���棬��ÿһ�Դ����ų�֮Ϊһ���հ�
```groovy
apply plugin: 'com.android.application'

android {
    compileSdkVersion 21
    buildToolsVersion "21.1.2"

    defaultConfig {
        applicationId "com.clock.gradleusage"
        minSdkVersion 14
        targetSdkVersion 21
        versionCode 1
        versionName "1.0"
    }
    buildTypes {
        debug {

        }
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }

    lintOptions {
        checkReleaseBuilds false
        // Or, if you prefer, you can continue to check for errors in release builds,
        // but continue the build even when errors are found:
        abortOnError false
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'com.android.support:appcompat-v7:21.0.3'
}
```
��������������ű������ط�����˼�����á�

### Android Plugin
```groovy
apply plugin: 'com.android.application'
```
* ������δ����Ǹ���GradleҪ����һ��`com.android.application`�������AndroidStudio����ͨ��module��������������
* �����library module�ģ����������`com.android.library`

### Manifest and defaultConfig

�������⼸������Ҳ��ԱȽ���Ϥ���ܶ����˼�壬��Щ������ԭ�ȵ�adt����������Manifest�ļ��н������á�
```groovy
	compileSdkVersion 21
    buildToolsVersion "21.1.2"

    defaultConfig {
        applicationId "com.clock.gradleusage"
        minSdkVersion 14
        targetSdkVersion 21
        versionCode 1
        versionName "1.0"
    }
```
* compileSdkVersion��buildToolsVersion���ֱ��Ǳ���SDK�İ汾�ź͹������module�Ĺ��ߵİ汾��
* applicationId: ��ǰmodule�İ���
* ���������Զ���֮ǰManifest�����еģ����ﲻ׸��

### BuildTypes

����һ�ι������͵����ýű�
```groovy
	buildTypes {
        debug {

        }
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
```
* debug��release���ֱ��ǶԴ�debug��release�������ã�AndroidStudioĬ�����ɵĹ����ű�ֻ��release������
* minifyEnabled�� �Ƿ���д������
* proguardFiles: ���û������򣬴˴����÷�Ϊ`proguard-android.txt`��`proguard-rules.pro`�����֣�����������ļ���ͬ��ɴ����������
* proguard-android.txt�� AndroidStudioĬ�ϵĻ���������`ASĿ¼\sdk\tools\proguard\proguard-android.txt`
* proguard-rules.pro: AndroidStudioΪÿ��module���ɵ��Զ�����������ļ����ڶ�Ӧ�����moduleĿ¼��

### LintOptions

�����lint�������ã�`checkReleaseBuilds false`��`abortOnError false`����ȡ���������ʱ��lint������
```groovy
	lintOptions {
        checkReleaseBuilds false
        // Or, if you prefer, you can continue to check for errors in release builds,
        // but continue the build even when errors are found:
        abortOnError false
    }
```

### Dependencies

����ⲿ����Ҫ�ǶԵ�ǰmodule����������
```groovy
	dependencies {
		compile fileTree(dir: 'libs', include: ['*.jar'])
		compile 'com.android.support:appcompat-v7:21.0.3'
	}
```
module�µ�������Ϊ����������Զ���������֡����������Ҿ���Ҳ��������Ϊ�ڲ������������˼���������Ŀ���λ��module֮�ڣ���Զ�������Ļ����Ҳ�ȽϺ���⣬�������������������module֮�⣬������Project�µ������ط�����������Զ�̵ķ�������
* `compile fileTree(dir: 'libs', include: ['*.jar'])`���ڱ�����������ʾ����ʱ�����module�µ�libs�ļ����е�����jar�ļ���������Ҫʹ�õ�����jar�Ĺ���ֻ��ֱ�ӽ�jar���뵽module�µ�libs�ļ��м���
* `compile 'com.android.support:appcompat-v7:21.0.3'`����Զ����������ʾ������module���ĳ����
* ��������ĳ���ڲ�����Ҳ�����������dependencies�հ��м���`compile files('libs/***.jar')`
* ������ĳ��module�������Ҳ��Ҫ��dependencies�հ��м���`compile project(':����������module��')`

### �ܽ�

��ն�gradle��Android�����µ�Ӧ�����˸�СС���ܽᣬ��һЩ���ܻ�û�ἰ�����磺`ǩ��������`��`���������Զ������`��`����jar��aar`�����ݡ�����Ҫ�������ټ������ƻ��ܡ�
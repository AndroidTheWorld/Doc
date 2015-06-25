# 2_Gradle�﷨��������

�ڴ�ADTת�Ƶ�AndroidStudio�¿�������Ȼ������Gradle�ű����������.����һ���ű��������ǰ������˽������﷨������ת�ƿ��������Ĺ����У�Ҳ��ʼ�Ӵ�ѧϰGradle���ڴ�����һЩ�ܽᣬ�����Լ�����.

## GradleΪ����

��һ�ν���Gradle���������˴��µ��˽⡣���������ձ��˵����`Gradle����Groovy����Ϊ����������JavaӦ��Ϊ��������DSL�������ض����ԣ��﷨���Զ�����������.`�������������ɻ����е���������ģ�����ץס�������ص㣺
> 1.Gradle��һ������
> 2.Gradle��һ���Զ�����������
��Ȼ���Ӹ����ϵò����ܺõ���⣬��ô��Ϊѧϰһ�����Ժ�һ�����ߣ�ֻ��ͨ��ʹ������ǿ����͹����ϵ��˽���.

## Projects��tasks

Gradle������κζ������ǻ���`Projects(��Ŀ)`��`Tasks(����)`����������������������Gradle�ٷ��ų���ָ���ֲ�����ô�����ģ�
* ÿһ������������һ������projects���ɵ�.һ��project���״���ʲô������������Gradle��ʲô.�ٸ�����,һ��project���Դ���һ��JAR����һ����ҳӦ��.��Ҳ���ܴ���һ�������� ZIPѹ����,���ZIP�����������������Ŀ��JARs���ɵ�.����һ��project��һ����Ҫ����������ĳ������.�����Դ���һ��**Ҫ������,���粿�����Ӧ��.
* ÿһ��project����һ������tasks���ɵ�.һ��task����һЩ����ϸ���Ĺ���.�����Ǳ���һЩclasses,����һ��JAR,����javadoc,��������ĳ��Ŀ¼��ѹ���ļ�.
��AndroidStudio��������һ��apk�İ�װ��������Ҫ������build.gradle�ű����й���.��ʱ`����apk��`����һ������Ϳ�������Ϊһ��Project��Ҫ��һ��ʲô�£���������apk��ֻ��һ���Ƚϴ�һͳ�ĸ���.����Ĺ�����Ҫ���и��ָ��������ã��������ð汾�ţ���ͼ���Android����ƽ̨�����ǩ����.��Щ�൱��`����apk��`���Projects��һ����������Ӳ��裬Ҳ����Gradle�е�Tasks.

## Hello world
�˽��ŵ�һЩ��������֮������Ҫ�Ļ��ǿ�ʼ���ִ���ʵս�������Լ��ĵ�һ��Gradle�����ű�build.gradle
```groovy
task hello {
    doLast {
        println 'Hello world!'
    }
}
```
����������,����ű����ڵ��ļ���Ȼ������`gradle -q hello`��ִ�й����ű������ڿ���̨���ڵõ��������
```
> gradle -q hello
Hello world!
```
�������build.gradle�Ĺ����ű�������һ��������task������hello�����Ҽ�����һ��action.��������`gradle hello`,Gradleִ�н���hello��task,Ҳ����ִ���������ṩ��action.��� action��һ��������һЩGroovy����ıհ����������hello��task����ִ����һ��doLast��action�����action�����ڿ���̨�����`hello world`,gradle�ṩ��doLast��doFirst������action.
��task������Ͽ�����ʵtask�հ����ڲ��Ǳ����ֳ�Ϊһ������action���.���ˣ�����Ҳ������һ�����¹�ϵ����
> Project��һ�������ɸ�Task��ɣ�Task��һ�������ɸ�Action���
�����ٲ���˵��һ��`gradle -q`��������ã�����q��ʾGradle������Quietģʽ��������ģʽ����ֻ�ῴ��task���������Ϣ�������������в�����������Ϣһ�ɲ����ڿ���̨�Ĵ����������
��ƽʱ��AS�±���android moudleʱ����ῴ��Message���ڻ�����������������Ĺ���������ϸ��Ϣ
```
Information:Gradle tasks [:baidumap:assembleDebug]
:baidumap:preBuild UP-TO-DATE
:baidumap:preDebugBuild UP-TO-DATE
:baidumap:checkDebugManifest
:baidumap:preReleaseBuild UP-TO-DATE
:baidumap:prepareComAndroidSupportAppcompatV72103Library UP-TO-DATE
:baidumap:prepareComAndroidSupportSupportV42103Library UP-TO-DATE
:baidumap:prepareDebugDependencies
:baidumap:compileDebugAidl UP-TO-DATE
:baidumap:compileDebugRenderscript UP-TO-DATE
:baidumap:generateDebugBuildConfig UP-TO-DATE
:baidumap:generateDebugAssets UP-TO-DATE
:baidumap:mergeDebugAssets UP-TO-DATE
:baidumap:generateDebugResValues UP-TO-DATE
:baidumap:generateDebugResources UP-TO-DATE
:baidumap:mergeDebugResources UP-TO-DATE
:baidumap:processDebugManifest UP-TO-DATE
:baidumap:processDebugResources UP-TO-DATE
:baidumap:generateDebugSources UP-TO-DATE
:baidumap:processDebugJavaRes UP-TO-DATE
:baidumap:compileDebugJava UP-TO-DATE
:baidumap:compileDebugNdk UP-TO-DATE
:baidumap:compileDebugSources UP-TO-DATE
:baidumap:preDexDebug UP-TO-DATE
:baidumap:dexDebug UP-TO-DATE
:baidumap:validateDebugSigning
:baidumap:packageDebug UP-TO-DATE
:baidumap:zipalignDebug UP-TO-DATE
:baidumap:assembleDebug UP-TO-DATE
Information:BUILD SUCCESSFUL
Information:Total time: 31.254 secs
Information:0 errors
Information:0 warnings
Information:See complete output in console
```
����ģʽ������Quietģʽǡ���෴�ģ�Gradle�г���Quietģʽ�⣬�����������ֹ���ģʽ������������ϸ��ѧϰ�ܽᡣ

## 
---
title: TestNG 的简单使用
date: 2019-07-28 16:33:35
tags: testng
---

简单的介绍 Java 的自动化测试框架 TestNG。

<!--more -->

## Testng 简介

> TestNG是一个Java语言的测试框架，由Cédric Beust受到JUnit和NUnit的启发而创建。TestNG的设计目标是，覆盖更广泛的测试类别范围：单元测试、功能测试、端到端测试、集成测试等，并且功能更强大、更易于使用。 -- Wiki百科

## 安装

在 *IntelliJ IDEA* 中创建 Java 项目，选择 ***Maven*** ，*Maven* 是 **Apache Maven是一个软件项目管理和理解工具。基于项目对象模型（POM）的概念，Maven可以从一个中心信息管理项目的构建，报告和文档** 。创建完成后，在 *pom.xml* 文件中加入如下的内容。

```bash

<repositories>
        <repository>
            <id>jcenter</id>
            <name>bintray</name>
            <url>http://jcenter.bintray.com</url>
        </repository>
    </repositories>

    <dependencies>
        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>6.10</version>
            <scope>test</scope>
        </dependency>

    </dependencies>

```

然后在右下角的提示框中点击 *enable* ，开始自动下载 Testng 所需要的依赖。

##　注解

| 注解 | 描述 |
| :---- | :---- |
| @BeforeSuite | 在该套件中的所有测试都运行在注释的方法之前，仅运行一次 |
| @AfterSuite | 在该套件的所有测试都运行在注解之后，仅运行一次。 |
| @BeforeClass | 在调用当前类的第一个测试方法之前运行，注释方法仅运行一次 |
| @AfterClass | 在调用当前类的第一个测试方法之后运行，注释方法仅运行一次 |
| @BeforeTest | 注释的方法将在属于 `<test>` 标签内的类的所有测试方法运行之前运行 |
| @AfterTest | 注释的方法将在属于 `<test>` 标签内的类的所有测试方法之后运行 |
| @BeforeGroups | 配置方法将在之前运行组列表。此方法保证在调用属于这些组中的任何一个的第一个测试方法之前不久运行 |
| @AfterGroups | 此配置方法将在之后运行组列表，该方法保证在调用属于任何这些组的最后一个测试方法之后不久运行 |
| @BeforeMethod | 注释方法将在每个测试方法之前运行 |
| @AfterMethod | 注释方法将在每个测试方法之后运行 |
| @DataProvider | 标记一种方法来提供测试方法的数据。注释方法必须返回一个 `Object[][]` ，其中每个 `Object[]` 可以被分配给测试方法的参数列表。要从该 `DataProvider` 接收数据的 `@Test` 方法需要使用与此注释名称相等的 `dataProvider`名称 |
| @Factory | 将一个方法标记成工厂，返回 `TestNG` 将被用作测试类的对象。该方法必须返回 `Object[]` 。 |
| @Listeners | 定义测试类上的侦听器。 |
| @Parameters | 描述如何将参数传递给 `@Test` 方法。 |
| @Test | 将类或方法标记为测试的一部分。 |

## 关于 ***testng.xml*** 文件的解析

首先在刚创建的时候，找不到这个文件，首先要开始创建这个文件。 在 *IntelliJ IDEA* 中安装 ***Create TestNG XML*** 这个插件，然后右键点击项目名称，找到菜单中的 *Creat TestNG XML* 的选项。点击之后，就会生成一个 *testng.xml* 的文件，具体如下图。

{% asset_img 生成testng文件.png %}

首先， ***testng.xml*** 的文件样式如下面所示。

```xml
<suite name="Suite1" verbose="1" >
  <test name="Nopackage" >
    <classes>
       <class name="NoPackageTest" />
    </classes>
  </test>

  <test name="Regression1">
    <classes>
      <class name="test.sample.ParameterSample"/>
      <class name="test.sample.ParameterTest"/>
    </classes>
  </test>
</suite>
```

+ `<suite>...</suite>` 表示定义了的一个测试套件。

  + `name` 定义测试套件的名称。

  + `verbose` 定义命令行信息打印等级，不会影响测试报告输出内容；可选值(1|2|3|4|5)

+ `<test>...</test>` 表示定义了一个测试。

  + name 定义测试的名称

+ `<classes>...</classes>` 表示定义一组测试类

  + `<class>...</class>` 表示定义一个测试类。

    + `name` 指定要运行的测试类。

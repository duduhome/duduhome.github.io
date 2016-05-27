---
title: "Jar"
layout: page
date: 2099-06-02 00:00
---
[TOC]

# Jmeter的Jar #
## 引入jmeter相关pom依赖 ##
将systemPath改为jmeter所在jar包的地址

	 <dependency>
            <groupId>com.dianping</groupId>
            <artifactId>ApacheJMeter_core</artifactId>
            <version>1.0.0</version>
            <scope>system</scope>
            <systemPath>/Users/zjj/Downloads/apache-jmeter-2.13/lib/ext/ApacheJMeter_core.jar</systemPath>
        </dependency>
        <dependency>
            <groupId>com.dianping</groupId>
            <artifactId>ApacheJMeter_java</artifactId>
            <version>1.0.0</version>
            <scope>system</scope>
            <systemPath>/Users/zjj/Downloads/apache-jmeter-2.13/lib/ext/ApacheJMeter_java.jar</systemPath>
        </dependency>
        <dependency>
            <groupId>com.dianping</groupId>
            <artifactId>jorphan</artifactId>
            <version>1.0.0</version>
            <scope>system</scope>
            <systemPath>/Users/zjj/Downloads/apache-jmeter-2.13/lib/jorphan.jar</systemPath>
        </dependency>
        <dependency>
            <groupId>com.dianping</groupId>
            <artifactId>logger</artifactId>
            <version>1.0.0</version>
            <scope>system</scope>
            <systemPath>/Users/zjj/Downloads/apache-jmeter-2.13/lib/logkit-2.0.jar</systemPath>
        </dependency>
        <dependency>
            <groupId>com.dianping</groupId>
            <artifactId>avalon</artifactId>
            <version>1.0.0</version>
            <scope>system</scope>
            <systemPath>/Users/zjj/Downloads/apache-jmeter-2.13/lib/avalon-framework-4.1.4.jar</systemPath>
        </dependency>
	
## 创建测试类 ##

类继承AbstratJavaSampleClinet

	 public class createCase extends AbstractJavaSamplerClient{。。。}
	
## 设置传入的参数 ##
可设置多个参数，设置的参数会在Jmeter的参数列表中展示

	 public Arguments getDefaultParameters() {
        Arguments params = new Arguments();
        params.addArgument("num1", "");
        params.addArgument("num2", "");
        return params;
    }
    
## 初始化方法 ##
实际运行时每个线程只运行一次，在测试方法前运行

	//初始化一下数据之类
	 public void setupTest(JavaSamplerContext arg0) {。。。}
	
## 测试方法 ##
测试的循环体，会根据线程数和循环次数的不同执行多次

	 public SampleResult runTest(JavaSamplerContext arg0) {
	    arg0.getParameter("num1");//获取jmeter中设置的参数值
        SampleResult sr = new SampleResult();
        sr.setSampleLabel("Java请求哦"); //java请求的label，会在jmeter中展示
        try {
            sr.sampleStart();// jmeter 开始统计响应时间标记
            resultData=cscCaseService.asyncCreateCscCase(cscCaseDto);
            if (resultData != null) {
                sr.setResponseData("结果是："+resultData.toString(), null);
                sr.setDataType(SampleResult.TEXT);
            }
             System.out.println(resultData.toString());
            sr.setSuccessful(true);
        } catch (Exception e) {
            sr.setSuccessful(false);
            e.printStackTrace();
        } finally {
            sr.sampleEnd();// jmeter 结束统计响应时间标记
        }
        return sr;
    }


## 结束方法 ##
实际运行时每个线程只运行一次，在测试方法结束后运行

    public void teardownTest(JavaSamplerContext arg0) {
        System.out.println("end");
        System.out.println("The cost is" + 1000);
    }
		
	

	
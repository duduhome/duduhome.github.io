---
title: "TestNg"
layout: page
date: 2099-06-02 00:00
---
[TOC]

# 环境 #

	 Intellij + Java
	 
jar包依赖  

	 TestNg-6.8.jar
	 
# 基本方法#
创建一个测试类

	 public class testCreateCaseForMovie {
	 	@BeforeClass(alwaysRun = true)//测试方法运行之前执行的
     	public void setUp() throws Exception {
        	driver = new FirefoxDriver();
        	baseUrl = "http://10.66.59.27:8080";
        	driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
        }

	 	@Test//主要测试流程
	 	public void test111() throws Exception {
        	driver.get(baseUrl);
        	driver.findElement(By.id("login-username")).clear();
        	driver.findElement(By.id("login-username")).sendKeys("alisa.zhao");
        	driver.findElement(By.id("login-password")).clear();
        	driver.findElement(By.id("login-password")).sendKeys("Dp16603655");
        	driver.findElement(By.name("commit")).click();
        }

	 	@AfterClass(alwaysRun = true)//测试方法结束后执行
	 	public void tearDown() throws Exception {
        	driver.quit();
        }
    }
    
# 运行 #
##直接执行##
直接右击@test 方法执行

## 配置xml ##
按照suilt group class 执行

	 <?xml version="1.0" encoding="UTF-8"?>
		<!DOCTYPE suite SYSTEM "http://beust.com/testng/testng-1.0.dtd" >
		<suite name="suite1">
    		<test name="test" verbose="10">//verbose是详细程度，10是最详细
        		<classes>
            		<class name="com.tgb.test.TestcaseLogin" />
        		</classes>
    		</test>
		</suite>

# 注解 #



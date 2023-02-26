---
layout: post
title: Java | Mapstruct 简单入门
---

`Mapstruct` 是一款对象映射工具，使用编译时生成器生成代码，没有反射的性能困扰。

<!--more-->

# 简单入门

官方文档：https://mapstruct.org/

## 引入依赖

这里以 `Maven` 为主，其他打包工具请参考官方文档。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project>
    <properties>
        <org.mapstruct.version>1.4.2.Final</org.mapstruct.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.mapstruct</groupId>
            <artifactId>mapstruct</artifactId>
            <version>${org.mapstruct.version}</version>
            <optional>true</optional>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source> <!-- depending on your project -->
                    <target>1.8</target> <!-- depending on your project -->
                    <annotationProcessorPaths>
                        <path>
                            <groupId>org.mapstruct</groupId>
                            <artifactId>mapstruct-processor</artifactId>
                            <version>${org.mapstruct.version}</version>
                        </path>
                        <!-- other annotation processors -->
                    </annotationProcessorPaths>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

如果你同时使用了 `Lombok` 工具，编译时可能会报错，请参考以下方式解决：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project>
    <properties>
        <org.mapstruct.version>1.4.2.Final</org.mapstruct.version>
        <lombok.version>1.18.24</lombok.version>
        <lombok-mapstruct-binding.version>0.2.0</lombok-mapstruct-binding.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>${lombok.version}</version>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.mapstruct</groupId>
            <artifactId>mapstruct</artifactId>
            <version>${org.mapstruct.version}</version>
            <optional>true</optional>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source> <!-- depending on your project -->
                    <target>1.8</target> <!-- depending on your project -->
                    <annotationProcessorPaths>
                        <path>
                            <groupId>org.mapstruct</groupId>
                            <artifactId>mapstruct-processor</artifactId>
                            <version>${org.mapstruct.version}</version>
                        </path>
                        <path>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok</artifactId>
                            <version>${lombok.version}</version>
                        </path>
                        <path>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok-mapstruct-binding</artifactId>
                            <version>${lombok-mapstruct-binding.version}</version>
                        </path>
                        <!-- other annotation processors -->
                    </annotationProcessorPaths>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

**提示：由于 `Lombok` 和 `Mapstruct` 都是编译时工具，因此设置 `<optional>true</optional>` 可以有效缩减最终生成的 jar
包体积。**

## 使用方法

参考 `Mapper` 的 API 注释：

```java

@Mapper
public interface CarMapper {
    CarDto toCarDto(Car source);
}
```

编译后，生成如下内容：

```java

@Generated(
        value = "org.mapstruct.ap.MappingProcessor",
        date = "2022-05-31T10:16:12+0800",
        comments = "version: 1.4.2.Final, compiler: javac, environment: Java 1.8.0_301 (Oracle Corporation)"
)
public class CarMapperImpl implements CarMapper {

    @Override
    public CarDto toCarDto(Car source) {
        if (source == null) {
            return null;
        }

        CarDto carDto = new CarDto();

        carDto.setName(source.getName());
        return carDto;
    }

}
```
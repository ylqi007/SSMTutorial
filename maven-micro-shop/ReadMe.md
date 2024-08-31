1. 父工程是不打包的，因此将父工程的packing改为pom
2. 父工程不做代码管理，因此删掉src目录
3. 创建子工程`user-service`,并将其从maven的jar工程改为改为web工程，通过JBLJavaToWeb
4. 同理创建子工程`order-service`
5. 创建通用的普通jar工程`common-service`, 后期放通用工具类的，是普通的java工程，稍后需要将这个工程放入maven的本地仓库，供`user-service`和`order-service`两个子工程使用。能放入maven本地仓库的工程都应该是普通jar工程。
6. 进行依赖管理
7. 子工程之间的引用。要想`user-service`和`order-service`可以引用`common-io`，需要将`common-io`部署到本地maven仓库or私服。
   1. `maven install`
   2. 
   ```shell
   [INFO] --- install:3.1.2:install (default-install) @ common-service ---
   [INFO] Installing /Users/ylqi007/Work/IDEA/SSMTutorial/maven-micro-shop/common-service/pom.xml to /Users/ylqi007/.m2/repository/com/atguigu/common-service/1.0.1/common-service-1.0.1.pom
   [INFO] Installing /Users/ylqi007/Work/IDEA/SSMTutorial/maven-micro-shop/common-service/target/common-service-1.0.1.jar to /Users/ylqi007/.m2/repository/com/atguigu/common-service/1.0.1/common-service-1.0.1.ja
   ```
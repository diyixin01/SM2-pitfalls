# SM2-shortcoming

# 代码介绍
该project主要介绍了几种SM2签名的缺陷
# 运行指导
直接运行即可
# 实验原理及其代码介绍
# 泄露k导致d泄露


![image](https://user-images.githubusercontent.com/75195549/181471493-4a5a3cc8-843f-42a1-9c9e-07f4fbec9930.png)


敌手可以直接使用受害者A签过的sig以及泄露的k求解d


![image](https://user-images.githubusercontent.com/75195549/181473187-25ae8405-e883-4213-b880-5147b1e9d3f7.png)


结果如下：

![image](https://user-images.githubusercontent.com/75195549/181472229-040f02fe-c8f8-4f6f-b3bb-89dda5637686.png)


# 某个用户重复使用k时会导致其私钥d泄露



![image](https://user-images.githubusercontent.com/75195549/181472308-6f3353bd-713f-4cc8-afe0-a9e3a08809bd.png)



敌手可以使用受害者A利用相同k签的sig1和sig2直接计算其私钥d

![image](https://user-images.githubusercontent.com/75195549/181473252-b3f771d2-6e5e-4cf6-804c-dcc08492330f.png)



结果如下：

![image](https://user-images.githubusercontent.com/75195549/181472449-0f8b0145-4b2d-46d2-ade1-e810bed03602.png)




# 不同用户重复使用相同k签名导致他们可以计算对方的私钥d



![image](https://user-images.githubusercontent.com/75195549/181472536-500a74bf-2323-4a3a-8cc7-a87328588f9c.png)



一方只需获取另一方的某个签名即可直接计算其私钥


![image](https://user-images.githubusercontent.com/75195549/181473293-ed431782-c1e2-42da-9c32-6618b4774f60.png)




结果如下：


![image](https://user-images.githubusercontent.com/75195549/181472631-c90ba284-cfc2-452c-841f-e74af3a40902.png)




# 使用与ECDSA相同的d与k


![image](https://user-images.githubusercontent.com/75195549/181472756-7e978958-a9bf-44e9-bdcb-aa7cc1c3273a.png)



对于ECDSA签名，不验证消息m的情况下可以伪造签名

当敌手获得一个签名（r，s）时，在不验证消息m的情况下可以伪造（r1，s1）通过验证。

只需生成随机u，v∈[1，n-1]，计算R=[u]G＋[v]P，那么r1=Rx%n，s1=（r1*invert（v，n））%n


![image](https://user-images.githubusercontent.com/75195549/181473352-a8f98e3f-dad1-4f00-991c-43bd995c872e.png)



结果如下：


![image](https://user-images.githubusercontent.com/75195549/181473421-b15f3cfd-741a-420e-8f8c-eb5917a33486.png)




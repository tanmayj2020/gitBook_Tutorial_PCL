# PCL-Python 기반 I/O

> Jupyter 버젼은 [[이곳]](https://github.com/adioshun/gitBook_Tutorial_PCL/blob/master/Beginner/Part01-Chapter01-PCL-Python.ipynb)에서 확인 가능 합니다. 

## 1. 읽기 

```python 
import pcl

pc = pcl.load("./sample/lobby.pcd") # "pc.from_file" Deprecated
print(pc)
```

## 2. 생성 

```python 
import pcl
import numpy as np


pc_array = np.array([[1, 2, 3], [3, 4, 5]], dtype=np.float32)
print(pc_array)


#방법 1
pc = pcl.PointCloud(pc_array)
print(pc)

#방법 2
pc = pcl.PointCloud()
pc.from_array(pc_array)
print(pc)
```

---


## 3. 쓰기 

```python 
import pcl

# 방법 1
pcl.save(pc, 'pc2pcd.pcd') 
#pcl.save_XYZRGBA(pc, 'pc2pcd.pcd') #RGB-D센서에서 주로 사용, x,y,z좌표 이외 색상 정보 포함


# 방법 2
pc.to_file('pc2pcd.pcd')


```

---

## 4. 변환 

추후 군집화, 분류, 전처리를 위해서 일반적으로 Numpy로 변환 하여 작업을 수행하므로 변환 과정에 대하여 살펴 보겠습니다. 

```python 
import pcl
import numpy as np

# PC to Numpy
pc_array = pc.to_array()

print("pc_array size : {}".format(pc_array.size))
print("pc Type : {}".format(type(pc)))
print("pc_array Type : {}".format(type(pc_array)))

# Numpy to PC 
pc_new = pcl.PointCloud()
pc_new.from_array(pc_array) # 2.생성 방법과 동일 

```

---

## 5. 정보 출력 


```python 
import pcl
pc = pcl.load("./sample/lobby.pcd") 


print("포인트 수 : {}".format(pc)) 
print("포인트 수 : {}".format(pc.size)) 



# 포인트 값 
print ('Loaded ' + str(pc.width * pc.height) + ' data points from test_pcd.pcd with the following fields: ')

for i in range(0, 10):#pc.size):
    print ('x: ' + str(pc[i][0]) + ', y : ' + str(pc[i][1]) + ', z : ' + str(pc[i][2]))

```
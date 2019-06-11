# PCL-Python 기반 노이즈 제거 


## 1. Statistical Outlier Removal

> Jupyter 버젼은 [[이곳]](https://github.com/adioshun/gitBook_Tutorial_PCL/blob/master/Beginner/Part01-Chapter04-PCL-Python.ipynb)에서 확인 가능 합니다. 



```python 

def do_statistical_outlier_filtering(pcl_data,mean_k,tresh):
    '''
    :param pcl_data: point could data subscriber
    :param mean_k:  number of neighboring points to analyze for any given point
    :param tresh:   Any point with a mean distance larger than global will be considered outlier
    :return: Statistical outlier filtered point cloud data
    eg) cloud = do_statistical_outlier_filtering(cloud,10,0.001)
    : https://github.com/fouliex/RoboticPerception
    '''
    outlier_filter = pcl_data.make_statistical_outlier_filter()
    outlier_filter.set_mean_k(mean_k)
    outlier_filter.set_std_dev_mul_thresh(tresh)
    return outlier_filter.filter()

    
cloud = do_statistical_outlier_filtering(cloud,10,0.001)
    
```

    입력 cloud포맷 : pcl_xyz 
    pcl_xyz = pcl_helper.XYZRGB_to_XYZ(pcl_xyzrgb)
    pcl_xyzrgb시 : TypeError: __cinit__() takes exactly 1 positional argument (0 given) 에러 



---
## 2. Radious Outlier Removal



> [추후 추가](https://github.com/strawlab/python-pcl/blob/master/examples/official/Filtering/remove_outliers.py)
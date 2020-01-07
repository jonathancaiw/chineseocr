集成classification实现营业执照识别

1、复制classification及如下文件至项目根目录：
data
    neimeng、pingfang
model
    __init__.py、nn_config.py、nn_model.py、regression_config.py、regression_model.py、rnn_config.py、rnn_model.py
__init__.py、algorithm.py、config.py、data.py、data_cleaning.py、dataset.py、model*.pt、post_processing.py、predict.py


2、修改config.py
# 数据集路径
DATA_PATH = 'classification/data'
# 模型路径
MODEL_PATH = 'classification'

3、修改app.py
#新增import
import sys

sys.path.append(os.getcwd() + '/classification')
from classification import post_processing

#新增返回值
prediction = 'timeout'

#class OCR POST通用识别新增返回值
prediction = post_processing.test(result)

#修改class OCR POST返回值
return json.dumps({'prediction': prediction, 'res': res, 'timeTake': round(timeTake, 4)}, ensure_ascii=False)

4、修改config.py为cconfig.py

5、修改algorithm.py、data.py的import config为import cconfig

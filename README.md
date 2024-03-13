### 训练配置：
在项目的data文件夹下，新建一个yaml文件作为配置文件，在里面配置数据路径（注意数据要做成yolo的格式）

### 训练过程

修改device、cfg、worker这几个变量即可。

```bash
python train_dual.py --workers 2 --device 0 --batch 8 --data data/visdrone.yaml --img 640 --cfg models/detect/yolov9-c.yaml --weights '' --name yolov9-c --hyp hyp.scratch-high.yaml --min-items 0 --epochs 500 --close-mosaic 15
```

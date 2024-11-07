
## 源码下载



```


|  | git clone https://github.com/eosphoros-ai/DB-GPT.git |
| --- | --- |


```

## Miniconda环境安装


**Miniconda 安装**



```


|  | mkdir -p ~/miniconda3 |
| --- | --- |
|  | wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh |
|  | bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3 |
|  | rm -rf ~/miniconda3/miniconda.sh |


```

**初始化Miniconda**



```


|  | ~/miniconda3/bin/conda init bash |
| --- | --- |
|  |  |


```

使conda环境生效：



```


|  | source ~/.bashrc |
| --- | --- |


```

之后就有conda基础环境了，会看到在终端用户名前面添加了(base)标志


**创建Python虚拟环境**



```


|  | python >= 3.10 |
| --- | --- |
|  |  |
|  | conda create -n dbgpt_env python=3.10 |
|  |  |
|  | conda activate dbgpt_env #之后conda环境就变成(dbgpt_env) tom@ubuntu:/home/apps$ |
|  |  |
|  | # it will take some minutes |
|  |  |
|  | pip install -e ".[default]" -i https://mirrors.aliyun.com/pypi/simple/ |
|  |  |


```

**复制环境变量**



```


|  | cp .env.template  .env |
| --- | --- |


```

## 模型部署


### 下载Embedding 模型



```


|  | cd DB-GPT |
| --- | --- |
|  |  |
|  | mkdir models and cd models |
|  |  |
|  | git lfs install |
|  |  |
|  | git clone https://huggingface.co/GanymedeNil/text2vec-large-chinese |


```

下载模型比较慢，使用huggingface的镜像站



```


|  | git clone https://hf-mirror.com/GanymedeNil/text2vec-large-chinese |
| --- | --- |


```

model.safetensor 和 pytorch\_model.bin 文件较大可以手动下载放到text2vec\-large\-chinese文件目录里


### 配置代理


资源有限，此处采用代理模式安装，代理模式就是采用其他大模型厂商提供的API接口


此处采用智谱的glm\-4模型



```


|  | LLM_MODEL=zhipu_proxyllmi |
| --- | --- |
|  | PROXYLLM_BACKEND=glm-4 |
|  | EMBEDDING_MODEL=text2vec |
|  | PROXY_SERVER_URL=https://open.bigmodel.cn/api/paas/v4/chat/completions |
|  | ZHIPU_PROXY_API_KEY= |


```

## 测试数据


加载默认的测试数据到SQLite数据库中



```


|  | bash ./scripts/examples/load_examples.sh |
| --- | --- |


```

## 运行服务



```


|  | python dbgpt/app/dbgpt_server.py |
| --- | --- |


```

## 访问


[http://localhost:5670](https://github.com)


[![pkbQdXt.png](https://s21.ax1x.com/2024/07/25/pkbQdXt.png)](https://github.com):[蓝猫机场加速器](https://dahelaoshi.com)



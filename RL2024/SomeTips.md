**◇ 如何暂存 实验 中的数据，如 奖励 等，便于后续比较？**

方法一： 暂存在 Google Drive

```
from google.colab import drive
drive.mount('/content/drive')
```

在目录 `/content/drive/MyDrive/` 新建一个文件夹 `DQNs-Test`

```
%cd /content/drive/MyDrive/
!ls
```



在 NoteBook 中存储数据

```
DQNs_df = pd.DataFrame(
    {
        "DQN_shangjiao": smoothed_y
    }
)

DQNs_df.to_csv("/content/drive/MyDrive/DQNs-Test/DQNs_df.csv")
```

方法二： 将.csv 文件存在 github, 每次数据更新后再重新上传。 

```
!wget -q http://www.yoursite.com/file.csv
```

————————————
```
my_df_loaded = pd.read_csv('/content/drive/MyDrive/DQNs-Test/DQNs_df.csv', index_col=0)   # index_col=0 指定行索引的位置
my_df_loaded
```



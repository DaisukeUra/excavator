---
marp: true
paginate: true
theme: default
style: @import url('https://unpkg.com/tailwindcss@^2/dist/utilities.min.css');
---


# おもちゃショベル動かす

---

# 先週までにやったこと

- [ワークスペースの作成](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Creating-A-Workspace/Creating-A-Workspace.html)
- [パッケージの作成](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Creating-Your-First-ROS2-Package.html)
- [pub/sub ノードの作成](https://docs.ros.org/en/jazzy/Tutorials/Intermediate/Writing-an-Action-Server-Client/Py.html)
- [カスタムメッセージのインストール](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Custom-ROS2-Interfaces.html) （ `heavy_equipment_msgs` ）


---

# 今日やること: キー入力でショベルを動かすぞ

## 必要なこと

- ショベルの操作インターフェイス仕様の把握
  - トピック，メッセージ型
- ショベルの操作インターフェイスに向けて命令を発出
- 命令の発出をジョイスティック入力をトリガにする


---

# ジョイスティック入力の確認

1. joy_linux パッケージをインストールする
`sudo apt install ros-${YOUR_ROS_VERSION}-joy-linux`
2. マニュアルは[ココ](https://index.ros.org/p/joy_linux/)
3. メッセージが出ているか確認する
   - `ros2 topic list` でトピックリストを確認
   - `ros2 topic echo ${YOUR_TOPIC_NAME}` でメッセージを確認


---

# ショベル操作のノードを作成

1. `ros2 pkg create` でノード操作用のパッケージを作成
2. 次ページのショベル仕様に合わせてpublisherを設定
3. `ros2 topic echo` でメッセージが出ているかを確認
4. ショベルのモータ電源を入れて動作確認



---

# ショベル仕様

- `/excavator/eclipse/cmd` （ `heavy_equipment_msgs/msg/Excavator` 型）で指令待ち受け
- `heavy_equipment_msgs/msg/Excavator` のそれぞれのフィールドは **-1.0 to 1.0** でPWMのデューティを表す
  - マイナスは逆転，逆転処理（出力ポートの変更）はドライバ側で自動実施


---

# トラブルシューティング

## 通信がうまくいかない

一旦ros2プロセスをすべて削除すると良いです．
`pkill -f ros2`









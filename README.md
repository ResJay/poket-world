# poket-world
想念小时候的宠物小精灵
#### 界面
![](https://raw.githubusercontent.com/ResJay/poket-world/master/GIF.gif)
#### 设计系统
* 对话系统
* 碰撞事件
* 动画脚本
* 导演切换场景
#### 笔记

```
1. 打开物理引擎和碰撞引擎
     cc.director.getPhysicsManager().enabled = true;
        cc.director.getPhysicsManager().debugDrawFlags = cc.PhysicsManager.DrawBits.e_aabbBit |
            cc.PhysicsManager.DrawBits.e_pairBit |
            cc.PhysicsManager.DrawBits.e_centerOfMassBit |
            cc.PhysicsManager.DrawBits.e_jointBit |
            cc.PhysicsManager.DrawBits.e_shapeBit
        ;        var manager = cc.director.getCollisionManager();
        manager.enabled = true;
/*        manager.enabledDebugDraw = true;*/    

2.注册监听键盘事件
 cc.systemEvent.on(cc.SystemEvent.EventType.KEY_DOWN, this.onKeyDown, this);
        cc.systemEvent.on(cc.SystemEvent.EventType.KEY_UP, this.onKeyUp, this);  //
        3.碰撞回调
          onCollisionEnter: function (other, self) {
       if(other.node.getComponents('bala')[0]){this.opera=other.node.getComponents('bala')[0].z}  //获得组件bala和属性z 根据赋值
    },
    onCollisionStay: function (other,self) {
        console.log("stay")

    },
    onCollisionExit: function (other, self) {
        console.log("exit")
    }
    4.生命周期
        update:function (dt) {
    }
    5.预备prefab读取&&音乐事件
          starPrefab: {
            default: null,
            type: cc.Prefab
        },
              audio: {
            url: cc.AudioClip,
            default: null
        }
   this.tPrefab = cc.instantiate(this.starPrefab);  //继承新prefab
        this.tPrefab.parent = this.node.parent;      覆盖父节点到当前node的父节点 简单来说就是设置prefab的位置
```


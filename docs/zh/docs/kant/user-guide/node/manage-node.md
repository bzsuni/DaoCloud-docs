# 运维边缘节点

边缘节点纳管成功后，平台可以对边缘节点执行暂停调度、移除节点操作。

## 暂停调度

应用场景：当需要对节点进行运维操作，用户可以选择暂停调度节点，那么工作负载在节点暂停调度期间，将无法下发到此节点。

> 说明：已经部署到节点的工作负载不影响其正常运行。

操作步骤如下：

1. 进入边缘单元详情页，选择左侧菜单 __边缘资源__ -> __边缘节点__ 。

2. 点击节点列表右侧 __暂停调度__ 按钮，提示暂停调度任务下发成功，稍后点击 __刷新__ 图标，节点状态变更为“健康/暂停调度”。

    ![暂停调度](https://docs.daocloud.io/daocloud-docs-images/docs/zh/docs/kant/images/node-manage-01.png)

3. 如果需要恢复调度，则点击列表右侧 __恢复调度__ 按钮，提示恢复调度任务下发成功，稍后点击 __刷新__ 图标，节点状态将变更为 __健康/可调度__ 。

## 移除节点

操作步骤如下：

1. 进入边缘单元详情页，选择左侧菜单 __边缘资源__ -> __边缘节点__ 。

2. 点击节点列表右侧 __移除节点__ 按钮，弹出确认移除弹框。

    ![暂停调度](https://docs.daocloud.io/daocloud-docs-images/docs/zh/docs/kant/images/node-manage-02.png)

3. 手动完成工作负载和终端设备资源解绑操作。如果节点上的资源已清除，忽略此步骤。

    1. 点击弹框中 __工作负载__ 按钮，跳转到工作负载列表页面。

    1. 找到节点上的工作负载，一一执行删除操作。

    1. 点击弹框中 __终端设备__ 按钮，跳转到终端设备列表页面。

    1. 找到与节点绑定的终端设备，执行解绑操作。

4. 输入框中输入节点名称，点击 __删除__ 按钮，完成节点移除。

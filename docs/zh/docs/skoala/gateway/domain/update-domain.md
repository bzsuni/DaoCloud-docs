# 更新和删除域名

微服务网关支持对统一托管的域名进行全生命周期管理，包括添加、更新、删除域名域名。
通过域名管理，可以将一个域名应用到网关内的多个 API，并且可以配置域名层级的网关策略。

## 更新域名

可以通过两种方式修改域名的基础信息和策略配置。

- 在 `域名管理`页面找到需要更新的域名，在右侧点击 `ⵗ` 选择`修改基础信息`或`修改策略配置`或`修改安全配置`。

    ![在列表页更新基础信息](https://docs.daocloud.io/daocloud-docs-images/docs/zh/docs/skoala/gateway/domain/images/update-domain-1.png)

- 点击域名名称进入域名详情页，在页面右上角点击`修改基础配置`更新基本信息，点击`修改策略配置`更新策略，点击`修改安全配置`更新安全配置。

    ![在详情页更新](https://docs.daocloud.io/daocloud-docs-images/docs/zh/docs/skoala/gateway/domain/images/update-domain-2.png)

## 删除域名

!!! danger

    - 正在被 API 使用的域名无法删除，需要先删除相关的 API 然后才能删除域名。
    - 域名删除后无法恢复。

可以通过两种方式删除域名。

- 在`域名管理`页面找到需要删除的域名，在点击 `ⵗ` 并选择`删除`。

    ![在列表页删除](https://docs.daocloud.io/daocloud-docs-images/docs/skoala/ms-gateway/domain/imgs/delete-domain-1.png)

- 点击域名名称进入域名的详情页，在页面右上角点击 `ⵗ` 操并选择`删除`。

    ![在详情页删除](https://docs.daocloud.io/daocloud-docs-images/docs/skoala/ms-gateway/domain/imgs/delete-domain-2.png)

    如果域名正在被某个 API 使用，需要页面提示点击`查看服务详情`去删除对应的 API。<!--待ui更新后更新描述-->

    ![在详情页删除](https://docs.daocloud.io/daocloud-docs-images/docs/zh/docs/skoala/gateway/domain/images/delete-domain-3.png)

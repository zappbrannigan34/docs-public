## Installing addon

[Several installation options](../../../../concepts/addons-and-settings/addons#features_of_installing_addons) are available for the addon.

Take into account the total [maximum system requirements](../../../../concepts/addons-and-settings/addons) of addons that will be placed on groups of worker nodes. If necessary, [perform manual scaling](../../../scale#masshtabirovanie_grupp_worker_uzlov_3e7a5fdf) groups of worker nodes or [set up automatic scaling](../../../scale#configure_automatic_scaling_for_worker_node_groups_6b2cb0af) before installation.

<tabs>
<tablist>
<tab>Standard installation</tab>
<tab>Installation on dedicated worker nodes</tab>
<tab>Quick installation</tab>
</tablist>
<tabpanel>

1. Install the addon:

   <tabs>
   <tablist>
   <tab>Personal account</tab>
   <tab>Terraform</tab>
   </tablist>
   <tabpanel>

    1. Go to your [VK Cloud personal account](https://cloud.vk.com/app/en).
    1. Select the project where the needed cluster is located.
    1. Go to **Containers → Kubernetes Clusters**.
    1. Click on the name of the cluster.
    1. Go to the **Addons** tab.
    1. If there are already installed addons in the cluster, click the **Add addon** button.
    1. Click the **Install** button on the `capsule` addon card.
    1. Select the needed addon version from the drop-down list.
    1. Click the **Install addon** button.
    1. Edit if necessary:

      - selected version
      - application name
      - namespace where the addon will be installed
      - [addon settings code](#editing_addon_settings_code_during_installation)

        <warn>

        An incorrectly specified settings code can lead to errors during installation or the addon is inoperable.

        </warn>

   1. Click the **Install addon** button.

      The installation of the addon in the cluster will begin. This process can take a long time.

   </tabpanel>
   <tabpanel>

   1. [Complete the Terraform quick start guide](/en/manage/tools-for-using-services/terraform/quick-start) if it is not already done.
   1. Add to your Terraform configuration files that describe the cluster:

      - The [vkcs_kubernetes_addon](https://github.com/vk-cs/terraform-provider-vkcs/blob/master/docs/resources/kubernetes_addon.md) resource.
      - The [vkcs_kubernetes_addon](https://github.com/vk-cs/terraform-provider-vkcs/blob/master/docs/data-sources/kubernetes_addon.md) data source.
      - The [vkcs_kubernetes_addons](https://github.com/vk-cs/terraform-provider-vkcs/blob/master/docs/data-sources/kubernetes_addons.md) data source.

      If necessary, adapt the usage examples given for resource and data sources to your task and Terraform configuration (see the links above).

   1. Make sure the configuration files are correct and contain the necessary changes:

      ```bash
      terraform validate && terraform plan
      ```

   1. Apply the changes:

      ```bash
      terraform apply
      ```

   </tabpanel>
   </tabs>

1. (Optional) [Check out the official Capsule documentation on working with the addon](https://capsule.clastix.io/docs/general/tutorial).

</tabpanel>
<tabpanel>

1. Prepare a dedicated group of worker nodes to install the addon, if it has not already been done:

   <tabs>
   <tablist>
   <tab>Personal account</tab>
   </tablist>
   <tabpanel>

   1. Go to your [VK Cloud personal account](https://cloud.vk.com/app/en).
   1. Select [project](/en/base/account/concepts/projects), where the cluster will be placed.
   1. Go to **Containers** → **Kubernetes clusters**.
   1. Find the cluster you need in the list.
   1. Make sure that the cluster has a dedicated group of worker nodes that will host addons.

      If there is no such group — [add it](../../../manage-node-group#add_worker_node_group).

   1. [Customise](../../../manage-node-group#customise_labels_and_taints) for this node group, if it hasn't already been done:

      - **Kubernetes labels**: key `addonNodes`, value `dedicated`.
      - **Node taints**: effect `NoSchedule`, key `addonNodes`, value `dedicated`.

   </tabpanel>
   </tabs>

1. Install the addon:

   <tabs>
   <tablist>
   <tab>Personal account</tab>
   <tab>Terraform</tab>
   </tablist>
   <tabpanel>

   1. Go to your [VK Cloud personal account](https://msk.cloud.vk.com/app/en).
   1. Select [project](/en/base/account/concepts/projects), where the cluster will be placed.
   1. Go to **Containers** → **Kubernetes clusters**.
   1. Click on the name of the desired cluster.
   1. Go to **Addons** tab.
   1. If there are already installed addons in the cluster, click on the **Add addon** button.
   1. Click the **Install** button on the `capsule` addon card.
   1. Выберите нужную версию аддона из выпадающего списка.
   1. Нажмите кнопку **Установить аддон**.
   1. Select the necessary addon version from the drop-down list.
   1. Click the **Install addon** button.
   1. Edit if necessary:

      - selected version
      - application name
      - the name of the namespace where the addon will be installed
      - [addon settings code](#editing_addon_settings_code_during_installation)

   1. Set the necessary tolerations and nodeSelector in the addon setup code:

      <tabs>
      <tablist>
      <tab>Tolerations</tab>
      <tab>nodeSelector</tab>
      </tablist>
      <tabpanel>

      ```yaml
      tolerations:
        - key: "addonNodes"
          operator: "Equal"
          value: "dedicated"
          effect: "NoSchedule"
      ```

      Set this toleration for the `tolerations` field.

      </tabpanel>
      <tabpanel>

      ```yaml
      nodeSelector:
        addonNodes: dedicated
      ```

      Set this selector for the `nodeSelector` field.

      </tabpanel>
      </tabs>

      <warn>

      An incorrectly specified settings code can lead to errors during installation or the addon is inoperable.

      </warn>

   1. Click the **Install addon** button.

      The installation of the addon in the cluster will begin. This process can take a long time.

   </tabpanel>
   <tabpanel>

   1. [Complete the Terraform quick start guide](/en/manage/tools-for-using-services/terraform/quick-start) if it is not already done.
   1. Add to your Terraform configuration files that describe the cluster:

      - The [vkcs_kubernetes_addon](https://github.com/vk-cs/terraform-provider-vkcs/blob/master/docs/resources/kubernetes_addon.md) resource.
      - The [vkcs_kubernetes_addon](https://github.com/vk-cs/terraform-provider-vkcs/blob/master/docs/data-sources/kubernetes_addon.md) data source.
      - The [vkcs_kubernetes_addons](https://github.com/vk-cs/terraform-provider-vkcs/blob/master/docs/data-sources/kubernetes_addons.md) data source.

      If necessary, adapt the usage examples given for resource and data sources to your task and Terraform configuration (see the links above).

   1. Make sure the configuration files are correct and contain the necessary changes:

      ```bash
      terraform validate && terraform plan
      ```

   1. Apply the changes:

      ```bash
      terraform apply
      ```

   </tabpanel>
   </tabs>

1. (Optional) [Check out the official Capsule documentation on working with the addon](https://capsule.clastix.io/docs/general/tutorial).

</tabpanel>
<tabpanel>

<info>

Editing the addon settings code is not supported during the quick installation.

If this is not suitable for you, perform a **standard installation** or **installation on dedicated worker nodes**.

</info>

1. Install the addon:

   <tabs>
   <tablist>
   <tab>Personal account</tab>
   <tab>Terraform</tab>
   </tablist>
   <tabpanel>

   1. Go to your [VK Cloud personal account](https://msk.cloud.vk.com/app/en).
   1. Select [project](/en/base/account/concepts/projects), where the cluster will be placed.
   1. Go to **Containers** → **Kubernetes clusters**.
   1. Click on the name of the desired cluster.
   1. Go to **Addons** tab.
   1. If there are already installed addons in the cluster, click on the **Add addon** button.
   1. Click the **Install** button on the `capsule` addon card.
   1. Select the necessary addon version from the drop-down list.
   1. Click the **Install addon** button.
   1. Edit if necessary:

      - selected version
      - application name
      - the name of the namespace where the addon will be installed

   1. Click the **Install addon** button.

      The installation of the addon in the cluster will begin. This process can take a long time.

   </tabpanel>
   <tabpanel>

   1. [Complete the Terraform quick start guide](/en/manage/tools-for-using-services/terraform/quick-start) if it is not already done.
   1. Add to your Terraform configuration files that describe the cluster:

      - The [vkcs_kubernetes_addon](https://github.com/vk-cs/terraform-provider-vkcs/blob/master/docs/resources/kubernetes_addon.md) resource.
      - The [vkcs_kubernetes_addon](https://github.com/vk-cs/terraform-provider-vkcs/blob/master/docs/data-sources/kubernetes_addon.md) data source.
      - The [vkcs_kubernetes_addons](https://github.com/vk-cs/terraform-provider-vkcs/blob/master/docs/data-sources/kubernetes_addons.md) data source.

      If necessary, adapt the usage examples given for resource and data sources to your task and Terraform configuration (see the links above).

   1. Make sure the configuration files are correct and contain the necessary changes:

      ```bash
      terraform validate && terraform plan
      ```

   1. Apply the changes:

      ```bash
      terraform apply
      ```

   </tabpanel>
   </tabs>

1. (Optional) [Check out the official Capsule documentation on working with the addon](https://capsule.clastix.io/docs/general/tutorial).

</tabpanel>
</tabs>

## Editing addon settings code during installation

Editing the addon code is applicable for standard installation and installation on dedicated worker nodes.

The full addon setup code along with the description of the fields is available on [GitHub](https://github.com/projectcapsule/capsule/blob/main/charts/capsule/values.yaml).

<err>

Do not delete the `podAnnotations.timestamp` fields or the values set in them. These fields are required for correct installation and operation of the addon.

</err>

After editing the addon code [continue installing the addon](#installing_addon).

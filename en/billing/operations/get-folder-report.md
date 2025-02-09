# Get expense details by folder

You can get a CSV file with your general or per-resource spending details.

## Getting started {#before-you-begin}

1. If you do not have any [folders](../../resource-manager/concepts/resources-hierarchy.md#folder) yet, [create one](../../resource-manager/operations/folder/create.md). In the folder name, specify the project or client to use the folder.

1. [Create a bucket](../../storage/operations/buckets/create.md) in {{ objstorage-full-name }}. {{ yandex-cloud }} will save detail files to this bucket. You can save details in multiple buckets.

   {% note alert %}

   Bucket requirements:

   * Do not make your bucket public; otherwise, anyone will be able to download your expense details from the bucket link.
   * Do not add [encryption](../../storage/concepts/encryption.md) to the bucket.

   {% endnote %}

1. Make sure you have one of the following roles: `billing.accounts.owner`, `billing.accounts.admin`, `billing.accounts.editor`.

## Get expense details {#download-detail}

{% list tabs %}

- Management console

   1. Open the {{ yandex-cloud }} [management console]({{ link-console-main }}).
   1. In the top-left corner, click ![image](../../_assets/console-icons/dots-9.svg) **{{ ui-key.yacloud.iam.folder.dashboard.label_products }}**.
   1. Select ![image](../../_assets/console-icons/credit-card.svg) [**{{ billing-name }}**]({{ link-console-billing }}).
   1. Select the account you want to get details for.
   1. In the left-hand panel, select **{{ ui-key.yacloud.billing.account.switch_exports }}**.
   1. Click **{{ ui-key.yacloud.billing.accounts.button_empty-billing-create }}**.
   1. In the **{{ ui-key.yacloud.billing.account.exports.label_create-export-title }}** window that opens, specify:
      * In the **{{ ui-key.yacloud.billing.account.exports.field_bucket }}** field, the name of the bucket to store the CSV file with details.
      * In the **{{ ui-key.yacloud.billing.account.exports.field_prefix }}** field, the name of the folder for the file. The last character must be `/`.
      * Select the language for product names: English or Russian.
      * Select **{{ ui-key.yacloud.billing.account.exports.label_not-include-resources }}** or **{{ ui-key.yacloud.billing.account.exports.label_include-resources }}** as the detailed view type.

         {% note tip %}

         If you select the **{{ ui-key.yacloud.billing.account.exports.label_include-resources }}** type of details for regular export, you can also view {{ datalens-full-name }}, {{ tracker-full-name }}, and {{ ml-platform-name }} resources in the [`resource_id` field](#format) (e.g., [{{ ml-platform-name }} community IDs](../../datasphere/concepts/community.md)).

         {% endnote %}
   1. Click **{{ ui-key.yacloud.billing.accounts.button_empty-billing-create }}**.

{% endlist %}

A new file with details is created in the bucket daily. The file name contains the prefix and date that details are collected for. The file is overwritten and updated with new data every hour.

The information can be updated in any daily file within a month.

{% note tip %}

Files with details from buckets aren't deleted automatically, but you can set up a deletion schedule. For more information, see [Object lifecycle](../../storage/concepts/lifecycles.md) ({{ objstorage-name }} refers to files in a bucket as _objects_).

{% endnote %}

## Expense details file format {#format}

An uploaded file with details is a CSV table with comma-separated columns. Each row shows the product consumption level per day for the specified folder.

The table contains the following columns:

* `billing_account_id`: [Billing account](../concepts/billing-account) ID.
* `billing_account_name`: Name of the billing account.
* `cloud_id`: ID of the [cloud](../../resource-manager/concepts/resources-hierarchy#cloud) that details are provided for.
* `cloud_name`: Cloud name.
* `folder_id`: Folder ID.
* `folder_name`: Name of the folder at the time of exporting details. This field may be empty if you deleted the folder before exporting the details.
* `resource_id`: Resource ID, resource name, or subscription ID. This field may be empty if the use of the service refers to the entire folder or it does not contain any resources. Correlation between services and `resource_id` column values:
   * {{ compute-name }} and {{ marketplace-name }}: ID of the VM, disk snapshot, disk image, or other resource installed using {{ marketplace-name }}.
   * {{ objstorage-name }}: Bucket name.
   * {{ vpc-name }}: ID of the resource that processes incoming or outgoing traffic.
   * {{ kms-short-name }}: ID of the key.
   * {{ network-load-balancer-name }}: ID of the network load balancer.
   * {{ container-registry-short-name }}: ID of the container.
   * {{ k8s }} and {{ dataproc-name }}: ID of the cluster.
   * {{ mpg-short-name }}, {{ mch-short-name }}, {{ mmg-short-name }}, {{ mmy-short-name }}, {{ mrd-short-name }}, and {{ mkf-name }}: ID of the cluster host.
   * {{ message-queue-name }}: ID of the request.
   * {{ sf-name }}: ID of the function.
   * {{ monitoring-short-name }}, {{ datalens-short-name }}, {{ iot-name }}, {{ speechkit-short-name }}, {{ translate-name }}, and {{ vision-short-name }}: An empty value.
   * Technical support: ID of the subscription.
* `service_id`: ID of the service that the consumed product belongs to.
* `service_name`: Name of the service that the consumed product belongs to.
* `sku_id`: ID of the consumed product.
* `sku_name`: Name of the product.
* `date`: Date that the cost of consumption is charged for. Dates are set as a range from 0:00 to 23:59 (UTC+3).
* `currency`: Billing account currency. Possible values: `RUB`, `USD`, and `KZT`.
* `pricing_quantity`: Amount of product units consumed. The decimal separator is a period.
* `pricing_unit`: Unit of product consumption.
* `cost`: Total cost of consumption. The decimal separator is a period.
* `credit`: Discount amount. The decimal separator is a period.
* `monetary_grant_credit`: Discount from a grant, including the grant for trying the platform. The decimal separator is a period.
* `volume_incentive_credit`: Discount for the volume of product consumption. The decimal separator is a period.
* `cud_credit`: Discount for the [committed volume](../concepts/cvos.md) of the resource. The cost of consumption in excess of the commitment equals the difference between the `cost` and `credit` column values. The decimal separator is a period.
* `misc_credit`: Other types of discounts, including discounts for resource consumption after the grant for trying the platform expires, but before switching to the paid version. The decimal separator is a period.
* `label.user_labels.<label name>`: Labels set for resources. For information about how to manage labels, see [{#T}](../../resource-manager/operations/manage-labels.md).
* `locale`: Language of each exported line. The value of this field determines the `sku_name` column language. Possible values are `en` and `ru`.
* `updated_at`: Date and time of the last line update in [Unix Timestamp](https://www.unixtimestamp.com) format.
* `exported_at`: Date and time when the line was added to the detail file.


{% cut "Deprecated parameters" %}

* `created_at`: Date and time when the specified cost of consumption was charged. In [Unix Timestamp](https://www.unixtimestamp.com) format.
* `label.system_labels.folder_id`: ID of the folder. The value is now displayed in the `folder_id` column.

{% endcut %}


##### See also

* [View usage details for the cloud](check-charges.md)
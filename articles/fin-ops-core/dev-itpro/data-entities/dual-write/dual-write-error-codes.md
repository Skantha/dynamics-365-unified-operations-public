---
title: Error codes for dual-write and Data Integrator
description: This article describes error codes that can occur during table map and project validation for dual-write and Data Integrator.
author: jaredha
ms.date: 03/11/2024
ms.topic: conceptual
ms.custom: 
  - bap-template
audience: IT Pro
ms.reviewer: johnmichalak
ms.search.region: global
ms.author: jaredha
---

# Error codes for dual-write and Data Integrator

[!include [banner](../../includes/banner.md)]

This article describes the error codes that can occur when you use Data Integrator to configure dual-write maps or data integration projects.

| Error code | Message | Details |
| --- | --- | --- |
| DIPV1000 | Connection validation failed | <p>This error indicates that the Power Apps ApiHub connections that are used for data integration with Data Integrator are no longer valid.</p><p>The error message details show the actual cause of the validation failure. You should fix the connections as indicated or re-create the connection sets to ensure that data integration continues to work. For more information about how to use Data Integrator to create connection sets, see [How to create a connection set](/power-platform/admin/data-integrator#how-to-create-a-connection-set).</p> | 
| DIPV1001 | Exceptions encountered during Dual-write project validation | <p>This error indicates that an unknown exception was encountered during dual-write project validation.</p><p>To get help with this error, contact Microsoft Support, and provide the exception details.</p> |
| DIPV1002 | Dual-write only supports mapping between cross-company entities or company-specific entities from both sides | <p>[Cross-company data sharing](../../sysadmin/srs-overview.md) is enabled for the finance and operations apps entity that's used in the table map. However, dual-write isn't supported for an entity when cross-company data sharing is enabled. For more information, see [Limitations](../../sysadmin/srs-overview.md#limitations).</p><p>To fix this error, either disable cross-company data sharing for the finance and operations apps entity, or use a different entity for the table map.</p> |
| DIPV1003 | Integration keys are missing | <p>Integration keys must contain at least one field to uniquely identify a table record. Integration keys are required for both dual-write and Data Integrator to work correctly between Dataverse and finance and operations apps. This error indicates that no integration key is defined for the Dataverse table that's used in the table map.</p><p>To fix this error, follow these steps.</p><ol><li>Open the [Power Apps maker portal](https://make.powerapps.com) in your Dataverse environment.</li><li>Open the table that's defined in the table map.</li><li>Define at least one alternate key for the Dataverse table.</li><li>If you're using dual-write, open the **Dual-write administration** workspace in finance and operations apps, open the table map, and select **Refresh tables**.</li></ol><p>For more information about integration keys, see [What is the purpose of the integration key, and is it mandatory?](dual-write-faq.md#what-is-the-purpose-of-the-integration-key-and-is-it-mandatory)</p> | 
| DIPV1004 | Integration key field isn't bi-directionally mapped | <p>Not all the fields that are used in the integration key are bidirectionally mapped.</p><p>If a dual-write table map is bidirectionally mapped (in other words, if any of the field mappings are bidirectional between finance and operations apps and Dataverse), ensure that all integration key fields are also bidirectionally mapped. By mapping both, you ensure that dual-write live synchronization can find a given record in either finance and operations apps or the Dataverse environment.</p><p>For more information about integration keys, see [What is the purpose of the integration key, and is it mandatory?](dual-write-faq.md#what-is-the-purpose-of-the-integration-key-and-is-it-mandatory)</p> | 
| DIPV1005 | Missing environment info for dataset | <p>This error indicates that the dual-write connection or the Data Integrator connection set is either misconfigured or corrupted.</p><p>To fix this error for dual-write, reset the dual-write connection set by following the steps in [Reset dual-write connections](./reset.md). For Data Integrator, re-create the connection set by following the steps in [How to create a connection set](/power-platform/admin/data-integrator#how-to-create-a-connection-set).</p> | 
| DIPV1006 | Exceptions encountered during project validation | <p>This error indicates that an unknown exception was encountered during dual-write map validation or Data Integrator project validation.</p><p>To get help with this error, contact Microsoft support, and provide the exception details.</p> |
| DIPV1007 | <p>Task has environment that doesn't exist in the connection set | This error indicates that the integration project is either misconfigured or corrupted.</p><p>To fix this error, re-create the data integration project by following the steps in [How to set up a data integration project](/power-platform/admin/data-integrator#how-to-set-up-a-data-integration-project).</p> | 
| DIPV1008 | Data partition isn't valid | The organization mapping in the connection set that the Data Integrator project uses becomes invalid after the customer deletes or changes the name of the business unit in Dataverse or the name of the legal entity in finance and operations apps.</p><p>To fix this error, re-add or rename the missing business unit or legal entity. Alternatively, re-create the connection set and data integration project by following the steps in [How to set up a data integration project](/power-platform/admin/data-integrator#how-to-set-up-a-data-integration-project). |
| DIPV1010 | Mandatory field in destination entity must be mapped | <p>A mandatory field is a field that a value must be provided for when a table record is created through dual-write. This error indicates that not all mandatory fields are being mapped. This situation causes a runtime failure when the dual-write maps are synced during transaction processing.</p><p>To fix this error, ensure that all mandatory fields in the table are correctly mapped to a related field on the target platform.</p> |
| DIPV1011 | Readonly field in destination entity must not be mapped | <p>A read-only field is a field that can't have a value set in either *create* or *update* operations through dual-write. This error indicates that at least one read-only field is incorrectly mapped. This situation causes a runtime failure when the dual-write maps are synced during transaction processing.</p><p>To fix this error, ensure that read-only fields aren't configured for bidirectional mapping.</p> |
| DIPV1012 | Error occurred while parsing Dataverse entity source filter | <p>This error indicates that the Dataverse source filter has either syntax errors or references to invalid fields.</p><p>To fix this error, ensure that the correct syntax is used to define the source filter for the Dataverse entity. For more information, see [Filter your data](customizing-mappings.md#filter-your-data).</p> |
| DIPV1014 | Mapping is missing for integration key | <p>This error indicates that not all fields of the integration key are correctly mapped, or that field mappings are missing.</p><p>Ensure that all integration key fields are mapped, so that the correct records can be found during dual-write synchronization. For more information about integration keys, see [What is the purpose of the integration key, and is it mandatory?](dual-write-faq.md#what-is-the-purpose-of-the-integration-key-and-is-it-mandatory)</p> |
| DIPV1015 | Mapping is missing for integration key for lookup field | This error indicates that the expanded fields (that is, key fields of the referenced entity) aren't mapped. If a lookup field is used as part of the integration key, the expanded fields must also be mapped. |
| DIPV1016 | Missing Organization mapping for destination entity | <p>This error indicates that the dual-write connection or the Data Integrator connection set is either misconfigured or corrupted.</p><p>To fix this error for dual-write, reset the dual-write connection set by following the steps in [Reset dual-write connections](./reset.md). For Data Integrator, re-create the connection set by following the steps in [How to create a connection set](/power-platform/admin/data-integrator#how-to-create-a-connection-set).</p> |
| DIPV1017 | Missing Organization mapping for related entity | <p>This error indicates that the dual-write connection or the Data Integrator connection set is either misconfigured or corrupted.</p><p>To fix this error for dual-write, reset the dual-write connection set by following the steps in [Reset dual-write connections](./reset.md). For Data Integrator, re-create the connection set by following the steps in [How to create a connection set](/power-platform/admin/data-integrator#how-to-create-a-connection-set).</p> |
| DIPV1018 | Missing source schema | <p>This error indicates that there's no cached metadata for the table.</p><p>To fix this error, open the **Dual-write administration** workspace in finance and operations apps, open the table map, and select **Refresh tables**. For information about how to ensure that the schema is updated if the source is a table in finance and operations apps, see [How to ensure data integration is using the most current finance and operations schema](dual-write-troubleshooting.md#how-to-ensure-data-integration-is-using-the-most-current-finance-and-operations-schema).</p> |
| DIPV1019 | Export can't be performed on the table due to the missing versionnumber field | <p>This error indicates that the mapped Dataverse table doesn't have a `versionnumber` field. The table is of a type that isn't supported in dual-write or Data Integrator, such as virtual entities or elastic tables.</p><p>To fix this error, enable the `versionnumber` field on the table, or select a table of a supported type.</p> |
| DIPV1020 | Missing destination schema | <p>This error indicates that there's no cached metadata for the table.</p><p>To fix this error, open the **Dual-write administration** workspace in finance and operations apps, open the table map, and select **Refresh tables**. For information about how to ensure that the schema is updated if the source is a table in finance and operations apps, see [How to ensure data integration is using the most current finance and operations schema](dual-write-troubleshooting.md#how-to-ensure-data-integration-is-using-the-most-current-finance-and-operations-schema).</p> |
| DIPV1021 | Missing source field in the mapping | <p>This error indicates that the source field isn't set for the field map.</p><p>To fix this error, add the source field, or use the **Default value transform** option if the source field isn't required.</p> |
| DIPV1022 | Missing source field in the schema | <p>This error indicates that the source field that's used in the field mapping isn't present in the cached metadata.</p><p>To fix this error, open the **Dual-write administration** workspace in finance and operations apps, open the table map, and select **Refresh tables**. For information about how to ensure that the schema is updated if the source is a table in finance and operations apps, see [How to ensure data integration is using the most current finance and operations schema](dual-write-troubleshooting.md#how-to-ensure-data-integration-is-using-the-most-current-finance-and-operations-schema).</p> |
| DIPV1023 | Duplicate source fields | <p>This error indicates that the same field is used more than once in bidirectional field mappings.</p><p>To fix this error, remove the duplicate field mapping from the table map.</p> |
| DIPV1024 | Missing destination field in the mapping | <p>This error indicates that the destination field isn't set for the field mapping. The destination field must be set for data integration to work correctly.</p><p>To fix this error, ensure that the destination fields of all field maps are set.</p> |
| DIPV1025 | Missing destination field in the schema | <p>This error indicates that the destination field that's used in the field mapping isn't present in the cached metadata.</p><p>To fix this error, open the **Dual-write administration** workspace in finance and operations apps, open the table map, and select **Refresh tables**. For information about how to ensure that the schema is updated if the source is a table in finance and operations apps, see [How to ensure data integration is using the most current finance and operations schema](dual-write-troubleshooting.md#how-to-ensure-data-integration-is-using-the-most-current-finance-and-operations-schema).</p> |
| DIPV1026 | Duplicate destination fields | <p>This error indicates that the same field is used more than once as the destination field in table field maps.</p><p>To fix this error, remove the duplicate field mapping from the table map.</p> |
| DIPV1027 | Map the integration key associated with the entity lookup field to the destination field | This error indicates that a mapping is missing for the integration key for a destination lookup field. The expanded fields (that is, key fields of the referenced entity) aren't being mapped. |
| DIPV1028 | Map the integration key associated with the entity lookup field to the source field | This error indicates that a mapping is missing for the integration key for a source lookup field. The expanded fields (that is, key fields of the referenced entity) aren't being mapped. |
| DIPV1029 | Duplicate value map | <p>This error indicates that two field maps use the same pair of source and destination fields.</p><p>To fix this error, find and remove all duplicates in the map.</p> |
| DIPV1030 | Data type mismatch | <p>This error indicates that the data type of the source field isn't compatible with the destination field. This situation causes runtime synchronization failure or potential data loss.</p><p>Based on the error message details, either change the data types of the fields, or choose a different pair of fields that have compatible data types.</p> |
| DIPV1031 | Missing default transform for mandatory destination field | <p>This error indicates that the default transform should be applied if a mandatory field is used as the destination field. The lack of a default transform causes runtime synchronization failures during integration processing.</p><p>To fix this error, add the default transform that ensures a default value for the mandatory field.</p> |

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
---
title: Regroupement des ressources dans votre application OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 3604f6eaaf0f34a0ff7e54826923c2aa92eef4a2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209765"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Regroupement des ressources dans votre application OLE DB

Pour tirer parti du regroupement dans votre application, vous devez vous assurer que les services OLE DB sont appelés en obtenant votre source de données via `IDataInitialize` ou `IDBPromptInitialize`. Si vous utilisez directement `CoCreateInstance` pour appeler le fournisseur en fonction du CLSID du fournisseur, aucun service OLE DB n’est appelé.

Les services OLE DB maintiennent des pools de sources de données connectées tant qu’une référence à `IDataInitialize` ou `IDBPromptInitialize` est conservée ou tant qu’une connexion est en cours d’utilisation. Les pools sont également gérés automatiquement dans un environnement COM+ 1,0 Services ou Internet Information Services (IIS). Si votre application tire parti du regroupement externe à un environnement IIS ou services COM+ 1,0, vous devez conserver une référence à `IDataInitialize` ou `IDBPromptInitialize` ou maintenir une connexion au moins. Pour vous assurer que le pool n’est pas détruit lorsque la dernière connexion est lancée par l’application, conservez la référence ou conservez la connexion pendant la durée de vie de votre application.

Les services de OLE DB identifient le pool à partir duquel la connexion est dessinée au moment de l’appel de `Initialize`. Une fois la connexion dessinée à partir d’un pool, elle ne peut pas être déplacée vers un autre pool. Par conséquent, évitez de faire des choses dans votre application qui modifient les informations d’initialisation, telles que l’appel de `UnInitialize` ou l’appel de `QueryInterface` pour une interface spécifique au fournisseur avant d’appeler `Initialize`. En outre, les connexions établies avec une valeur prompt autre que DBPROMPT_NOPROMPT ne sont pas regroupées. Toutefois, la chaîne d’initialisation Récupérée à partir d’une connexion établie par le biais d’une invite peut être utilisée pour établir des connexions regroupées supplémentaires à la même source de données.

Certains fournisseurs doivent établir une connexion distincte pour chaque session. Ces connexions supplémentaires doivent être inscrites séparément dans la transaction distribuée, le cas échéant. OLE DBing services met en cache et réutilise une seule session par source de données, mais si l’application demande plusieurs sessions à la fois à partir d’une source de données unique, le fournisseur peut se retrouver en créant des connexions supplémentaires et en effectuant des inscriptions de transactions supplémentaires qui ne sont pas regroupés. Il est plus efficace de créer une source de données distincte pour chaque session dans un environnement mis en pool que de créer plusieurs sessions à partir d’une source de données unique.

Enfin, étant donné qu’ADO utilise automatiquement les services OLE DB, vous pouvez utiliser ADO pour établir des connexions, et le regroupement et l’inscription se produisent automatiquement.

## <a name="see-also"></a>Voir aussi

[Services et regroupement des ressources OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)

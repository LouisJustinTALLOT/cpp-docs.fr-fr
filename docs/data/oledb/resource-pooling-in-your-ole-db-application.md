---
title: Regroupement des ressources dans votre Application OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4798b4bac8cc6f94e5199502a926eb084cc7534a
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340239"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>Regroupement des ressources dans votre application OLE DB
Pour tirer parti du regroupement dans votre application, vous devez vous assurer de services OLE DB sont appelés en obtenant la source de données via `IDataInitialize` ou `IDBPromptInitialize`. Si vous utilisez directement `CoCreateInstance` pour appeler le fournisseur selon le CLSID du fournisseur, aucun service OLE DB n’est appelées.  
  
 Les services OLE DB conservent des regroupements de sources de données connectées tant que référence à `IDataInitialize` ou `IDBPromptInitialize` est détenu ou tant qu’il existe une connexion en cours d’utilisation. Les pools sont également conservées automatiquement dans un environnement de Services COM + 1.0 ou Internet Information Services (IIS). Si votre application tire parti du regroupement en dehors d’un environnement de Services COM + 1.0 ou IIS, vous devez conserver une référence à `IDataInitialize` ou `IDBPromptInitialize` ou maintenir au moins une connexion. Pour vous assurer que le pool de ne pas détruit lorsque la dernière connexion est libérée par l’application, conservez la référence ou maintenir la connexion pour la durée de vie de votre application.  
  
 Services OLE DB identifient le pool à partir de laquelle la connexion est extraite au moment qui `Initialize` est appelée. Une fois que la connexion est extraite d’un pool, il ne peut pas être déplacé vers un autre pool. Par conséquent, évitez de faire les choses dans votre application qui modifient les informations d’initialisation, comme l’appel `UnInitialize` ou en appelant `QueryInterface` pour une interface spécifique au fournisseur avant d’appeler `Initialize`. En outre, les connexions établies avec une valeur d’invite autre que DBPROMPT_NOPROMPT ne sont pas regroupées. Toutefois, la chaîne d’initialisation récupérée à partir d’une connexion établie via l’invite peut être utilisée pour établir des connexions regroupées supplémentaires à la même source de données.  
  
 Certains fournisseurs doivent établir une connexion distincte pour chaque session. Ces connexions supplémentaires doivent être inscrit séparément dans la transaction distribuée, s’il en existe. Services OLE DB met en cache et réutilise une seule session par source de données, mais si l’application demande plus d’une session à la fois à partir d’une source de données, le fournisseur peut finir par effectuer des connexions supplémentaires, ainsi que les inscriptions de transactions supplémentaires qui sont pas regroupée. Il est en fait plus efficace de créer une source de données distincte pour chaque session dans un environnement de bureaux que de créer plusieurs sessions à partir d’une source de données.  
  
 Enfin, étant donné que ADO automatiquement utilise OLE DB services, vous pouvez utiliser ADO pour établir des connexions et le regroupement et l’inscription automatique.  
  
## <a name="see-also"></a>Voir aussi  
 [Services et regroupement des ressources OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)
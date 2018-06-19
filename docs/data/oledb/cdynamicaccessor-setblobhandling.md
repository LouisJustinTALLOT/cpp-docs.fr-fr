---
title: CDynamicAccessor::SetBlobHandling | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
dev_langs:
- C++
helpviewer_keywords:
- SetBlobHandling method
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ee2c2d57f9f413346bb33a178fc3d8fa90439e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095844"
---
# <a name="cdynamicaccessorsetblobhandling"></a>CDynamicAccessor::SetBlobHandling
Définit l’objet BLOB de valeur de la ligne en cours de traitement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `eBlobHandling`  
 Spécifie la façon dont les données BLOB doit être gérée. Elle peut prendre les valeurs suivantes :  
  
-   **DBBLOBHANDLING_DEFAULT**: gérer les données de colonne supérieures à `nBlobSize` (comme défini par `SetBlobSizeLimit`) en tant que données d’objets BLOB et récupérer par le biais d’un `ISequentialStream` ou `IStream` objet. Cette option va tenter de lier chaque colonne contenant des données plus importante que `nBlobSize` ou répertoriés sous la forme **DBTYPE_IUNKNOWN** en tant que données d’objet BLOB.  
  
-   **DBBLOBHANDLING_NOSTREAMS**: gérer les données de colonne supérieures à `nBlobSize` (comme défini par `SetBlobSizeLimit`) en tant que données d’objets BLOB et les récupérer via la référence dans la mémoire allouée par le fournisseur, appartenant à un consommateur. Cette option est utile pour les tables qui ont plus d’une colonne BLOB, et le fournisseur prend en charge qu’un seul `ISequentialStream` objet par l’accesseur.  
  
-   **DBBLOBHANDLING_SKIP**: ignorer (ne pas lier) les colonnes éligibles comme contenant des objets BLOB (l’accesseur ne sera pas lier ou récupérer la valeur de colonne, mais il sera toujours récupérer l’état de colonne et la longueur).  
  
## <a name="remarks"></a>Notes  
 Vous devez appeler `SetBlobHandling` avant d’appeler **ouvrir**.  
  
 La méthode de constructeur [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) définit l’objet BLOB de valeur de la gestion des **DBBLOBHANDLING_DEFAULT**.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)
---
title: CNoMultipleResults, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CNoMultipleResults
- ATL.CNoMultipleResults
- ATL::CNoMultipleResults
dev_langs:
- C++
helpviewer_keywords:
- CNoMultipleResults class
ms.assetid: 343e77c4-b319-476e-b592-901ab9b2f34e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 67658f6edadd7723789288ab268b97cecdd611d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017351"
---
# <a name="cnomultipleresults-class"></a>CNoMultipleResults, classe

Utilisé comme argument template (*TMultiple*) à [CCommand](../../data/oledb/ccommand-class.md) pour créer une commande optimisée qui gère un résultat unique.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CNoMultipleResults  
```  
  
## <a name="remarks"></a>Notes  

Si vous souhaitez une commande pour gérer plusieurs jeux de résultats, utilisez [CMultipleResults](../../data/oledb/cmultipleresults-class.md) à la place.  
  
## <a name="requirements"></a>Configuration requise  

**En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
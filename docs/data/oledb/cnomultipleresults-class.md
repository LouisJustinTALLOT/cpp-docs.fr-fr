---
title: CNoMultipleResults, classe
ms.date: 11/04/2016
f1_keywords:
- CNoMultipleResults
- ATL.CNoMultipleResults
- ATL::CNoMultipleResults
helpviewer_keywords:
- CNoMultipleResults class
ms.assetid: 343e77c4-b319-476e-b592-901ab9b2f34e
ms.openlocfilehash: 59b7b35c350a37f13e1f253bc1430d69521e4fa8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026718"
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
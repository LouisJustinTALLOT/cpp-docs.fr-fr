---
title: WinModule fonctions globales
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 1f1dcb325f8844a74b3dd831a51050083e7ea552
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834399"
---
# <a name="winmodule-global-functions"></a>WinModule fonctions globales

Ces fonctions assurent la prise en charge des `_AtlCreateWndData` opérations de structure.

> [!IMPORTANT]
> Les fonctions listées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|Nom|Description|
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Cette fonction est utilisée pour initialiser et ajouter une structure `_AtlCreateWndData`.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Appelez cette fonction pour extraire une structure `_AtlCreateWndData` existante.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase. h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a> AtlWinModuleAddCreateWndData

Cette fonction est utilisée pour initialiser et ajouter une structure `_AtlCreateWndData`.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>Paramètres

*pWinModule*<br/>
Pointeur vers la structure [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) d’un module.

*pData*<br/>
Pointeur vers la structure [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) à initialiser et à ajouter au module en cours.

*pObject*<br/>
Pointeur vers le pointeur d’un objet **`this`** .

### <a name="remarks"></a>Notes

Initialise une `_AtlCreateWndData` structure, qui est utilisée pour stocker le **`this`** pointeur utilisé pour faire référence aux instances de classe et l’ajoute à la liste référencée par la structure d’un module `_ATL_WIN_MODULE70` . Appelé par [CAtlWinModule :: AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a> AtlWinModuleExtractCreateWndData

Appelez cette fonction pour extraire une structure `_AtlCreateWndData` existante.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Paramètres

*pWinModule*<br/>
Pointeur vers la structure [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) d’un module.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la structure [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) .

### <a name="remarks"></a>Notes

Cette fonction extrait une structure existante `_AtlCreateWndData` de la liste référencée par la structure d’un module `_ATL_WIN_MODULE70` .

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)

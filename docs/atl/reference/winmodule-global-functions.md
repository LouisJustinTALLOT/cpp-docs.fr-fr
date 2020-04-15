---
title: WinModule Fonctions mondiales
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 3d7d001a2835514cc5385a7069c0bcda58cdd88e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329361"
---
# <a name="winmodule-global-functions"></a>WinModule Fonctions mondiales

Ces fonctions fournissent `_AtlCreateWndData` un soutien aux opérations de structure.

> [!IMPORTANT]
> Les fonctions énumérées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Cette fonction est utilisée pour initialiser et ajouter une structure `_AtlCreateWndData`.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Appelez cette fonction pour extraire une structure `_AtlCreateWndData` existante.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData

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

*Pdata*<br/>
Pointeur sur la structure [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) à être paralysé et ajouté au module actuel.

*pObject*<br/>
Pointer vers un objet est **ce** pointeur.

### <a name="remarks"></a>Notes

Initialise une `_AtlCreateWndData` structure, qui est utilisée pour stocker le **pointeur** utilisé pour se référer à des `_ATL_WIN_MODULE70` instances de classe, et l’ajoute à la liste référencée par la structure d’un module. Appelé par [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData

Appelez cette fonction pour extraire une structure `_AtlCreateWndData` existante.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Paramètres

*pWinModule*<br/>
Pointeur vers la structure [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) d’un module.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la structure [_AtlCreateWndData.](../../atl/reference/atlcreatewnddata-structure.md)

### <a name="remarks"></a>Notes

Cette fonction extraira `_AtlCreateWndData` une structure existante de la `_ATL_WIN_MODULE70` liste référencée par la structure d’un module.

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)

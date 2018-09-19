---
title: Fonctions globales WinModule | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs:
- C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70b99ac7790477df88a0e685afd5652a35c06233
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047523"
---
# <a name="winmodule-global-functions"></a>Fonctions globales WinModule

Ces fonctions fournissent la prise en charge de `_AtlCreateWndData` structure des opérations.

> [!IMPORTANT]
> Les fonctions répertoriées dans le tableau suivant ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Cette fonction est utilisée pour initialiser et ajouter une structure `_AtlCreateWndData`.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Appelez cette fonction pour extraire une structure `_AtlCreateWndData` existante.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="atlwinmoduleaddcreatewnddata"></a>  AtlWinModuleAddCreateWndData

Cette fonction est utilisée pour initialiser et ajouter une structure `_AtlCreateWndData`.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>Paramètres

*pWinModule*<br/>
Pointeur vers un module [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) structure.

*pData*<br/>
Pointeur vers le [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) structure devant être initialisé et ajoutées au module actuel.

*pObject*<br/>
Pointeur vers un objet **cela** pointeur.

### <a name="remarks"></a>Notes

Initialise un `_AtlCreateWndData` structure, qui est utilisé pour stocker le **cela** pointeur utilisé pour faire référence aux instances de classe et l’ajoute à la liste référencée par d’un module `_ATL_WIN_MODULE70` structure. Appelé par [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

##  <a name="atlwinmoduleextractcreatewnddata"></a>  AtlWinModuleExtractCreateWndData

Appelez cette fonction pour extraire une structure `_AtlCreateWndData` existante.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Paramètres

*pWinModule*<br/>
Pointeur vers un module [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) structure.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) structure.

### <a name="remarks"></a>Notes

Cette fonction extrait un existant `_AtlCreateWndData` structure à partir de la liste référencée par d’un module `_ATL_WIN_MODULE70` structure.

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)

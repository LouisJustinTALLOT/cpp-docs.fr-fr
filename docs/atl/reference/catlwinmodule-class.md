---
title: Classe CAtlWinModule
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: 40385fd592563837546b483bb80978cde6a56555
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321275"
---
# <a name="catlwinmodule-class"></a>Classe CAtlWinModule

Cette classe fournit un soutien pour les composants de fenêtre ATL.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Constructeur.|
|[CAtlWinModule: :CAtlWinModule](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Ajoute un objet de données.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Retourne un pointeur à l’objet de données du module de fenêtre.|

## <a name="remarks"></a>Notes

Cette classe fournit un soutien pour toutes les classes ATL qui nécessitent des fonctionnalités de fenêtre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Cette méthode est parastérisant et ajoute une `_AtlCreateWndData` structure.

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Paramètres

*Pdata*<br/>
Pointeur `_AtlCreateWndData` sur la structure à être paralysé et ajouté au module actuel.

*pObject*<br/>
Pointer vers un objet est **ce** pointeur.

### <a name="remarks"></a>Notes

Cette méthode appelle [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) qui initialise une structure [_AtlCreateWndData.](../../atl/reference/atlcreatewnddata-structure.md) Cette structure stockera le **pointeur,** utilisé pour obtenir l’instance de classe dans les procédures de fenêtre.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

Constructeur.

```
CAtlWinModule();
```

### <a name="remarks"></a>Notes

En cas d’échec de l’initialisation, une exception **EXCEPTION_NONCONTINUABLE** est soulevée.

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule: :CAtlWinModule

Destructeur.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Cette méthode renvoie `_AtlCreateWndData` un pointeur à une structure.

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la `_AtlCreateWndData` structure précédemment ajoutée avec [CAtlWinModule::AddCreateWndData](#addcreatewnddata), ou NULL si aucun objet n’est disponible.

## <a name="see-also"></a>Voir aussi

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de modules](../../atl/atl-module-classes.md)

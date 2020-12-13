---
description: 'En savoir plus sur : classe CAtlWinModule'
title: CAtlWinModule, classe
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
ms.openlocfilehash: 4ed0c52a59401fa5411fd6d5acbcaf72f31aeb11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152567"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule, classe

Cette classe fournit la prise en charge des composants de fenêtrage ATL.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Constructeur.|
|[CAtlWinModule :: ~ CAtlWinModule](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Ajoute un objet de données.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Retourne un pointeur vers l’objet de données du module de fenêtre.|

## <a name="remarks"></a>Notes

Cette classe fournit la prise en charge de toutes les classes ATL qui requièrent des fonctionnalités de fenêtrage.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a> CAtlWinModule::AddCreateWndData

Cette méthode initialise et ajoute une `_AtlCreateWndData` structure.

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Paramètres

*pData*<br/>
Pointeur vers la `_AtlCreateWndData` structure à initialiser et à ajouter au module en cours.

*pObject*<br/>
Pointeur vers le pointeur d’un objet **`this`** .

### <a name="remarks"></a>Notes

Cette méthode appelle [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) qui initialise une structure [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) . Cette structure stocke le **`this`** pointeur, utilisé pour obtenir l’instance de la classe dans les procédures de fenêtre.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a> CAtlWinModule::CAtlWinModule

Constructeur.

```cpp
CAtlWinModule();
```

### <a name="remarks"></a>Notes

Si l’initialisation échoue, une exception **EXCEPTION_NONCONTINUABLE** est levée.

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a> CAtlWinModule :: ~ CAtlWinModule

Destructeur.

```cpp
~CAtlWinModule();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a> CAtlWinModule::ExtractCreateWndData

Cette méthode retourne un pointeur vers une `_AtlCreateWndData` structure.

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la `_AtlCreateWndData` structure précédemment ajoutée avec [CAtlWinModule :: AddCreateWndData](#addcreatewnddata), ou null si aucun objet n’est disponible.

## <a name="see-also"></a>Voir aussi

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)

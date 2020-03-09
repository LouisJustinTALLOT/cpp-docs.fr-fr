---
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
ms.openlocfilehash: d0bc98fa48f84e67ab38106dea3fe22d5ad1757d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857349"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule, classe

Cette classe fournit la prise en charge des composants de fenêtrage ATL.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Constructeur.|
|[CAtlWinModule :: ~ CAtlWinModule](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Ajoute un objet de données.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Retourne un pointeur vers l’objet de données du module de fenêtre.|

## <a name="remarks"></a>Notes

Cette classe fournit la prise en charge de toutes les classes ATL qui requièrent des fonctionnalités de fenêtrage.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Cette méthode initialise et ajoute une structure `_AtlCreateWndData`.

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Paramètres

*pData*<br/>
Pointeur vers la structure `_AtlCreateWndData` à initialiser et à ajouter au module en cours.

*pObject*<br/>
Pointeur vers **le pointeur this** d’un objet.

### <a name="remarks"></a>Notes

Cette méthode appelle [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) qui initialise une structure [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) . Cette structure stocke le pointeur **This** , utilisé pour obtenir l’instance de la classe dans les procédures de fenêtre.

##  <a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

Constructeur.

```
CAtlWinModule();
```

### <a name="remarks"></a>Notes

Si l’initialisation échoue, une exception **EXCEPTION_NONCONTINUABLE** est levée.

##  <a name="dtor"></a>CAtlWinModule :: ~ CAtlWinModule

Destructeur.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Cette méthode retourne un pointeur vers une structure `_AtlCreateWndData`.

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la structure `_AtlCreateWndData` précédemment ajoutée avec [CAtlWinModule :: AddCreateWndData](#addcreatewnddata), ou null si aucun objet n’est disponible.

## <a name="see-also"></a>Voir aussi

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)

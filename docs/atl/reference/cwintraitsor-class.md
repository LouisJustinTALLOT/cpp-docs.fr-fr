---
title: Cwintraitsor, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3883065d9d7222d5e9d98806f0baadf0bc209213
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072302"
---
# <a name="cwintraitsor-class"></a>Cwintraitsor, classe

Cette classe fournit une méthode pour standardiser les styles utilisés lors de la création d’un objet de fenêtre.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>Paramètres

*t_dwStyle*<br/>
Styles de fenêtre par défaut.

*t_dwExStyle*<br/>
Par défaut des styles de fenêtre étendus.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Récupère les styles étendus pour le `CWinTraitsOR` objet.|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Récupère les styles standards pour le `CWinTraitsOR` objet.|

## <a name="remarks"></a>Notes

Cela [caractéristiques de fenêtre](../../atl/understanding-window-traits.md) classe fournit une méthode simple pour standardiser les styles utilisés pour la création d’un objet de fenêtre ATL. Utiliser une spécialisation de cette classe comme un paramètre de modèle à [CWindowImpl](../../atl/reference/cwindowimpl-class.md) ou l’autre des classes de fenêtre ATL pour spécifier l’ensemble minimal de styles standard et à utiliser pour les instances de cette classe de fenêtre.

Utiliser une spécialisation de ce modèle si vous souhaitez vous assurer que certains styles sont définis pour toutes les instances de la classe de fenêtre tout en autorisant d’autres styles à définir sur une base par instance dans l’appel à [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).

Si vous souhaitez fournir par défaut des styles de fenêtre qui seront utilisées uniquement quand aucun autre style n’est spécifiés dans l’appel à `CWindowImpl::Create`, utilisez [CWinTraits](../../atl/reference/cwintraits-class.md) à la place.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

##  <a name="getwndstyle"></a>  CWinTraitsOR::GetWndStyle

Appelez cette fonction pour récupérer une combinaison (à l’aide de l’opérateur OR logique), des styles standards de la `CWinTraits` objet et les styles par défaut spécifiés par *t_dwStyle*.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Styles utilisés pour la création d’une fenêtre.

### <a name="return-value"></a>Valeur de retour

Une combinaison de styles sont passés dans *dwStyle* et la valeur par défaut que ceux spécifiés par `t_dwStyle`, à l’aide de l’opérateur OR logique.

##  <a name="getwndexstyle"></a>  CWinTraitsOR::GetWndExStyle

Appelez cette fonction pour récupérer une combinaison (à l’aide de l’opérateur OR logique), des styles étendus de la `CWinTraits` objet et les styles par défaut spécifiés par `t_dwStyle`.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Styles étendus utilisés pour la création d’une fenêtre.

### <a name="return-value"></a>Valeur de retour

Une combinaison des styles étendus qui sont passés dans *dwExStyle* et celles spécifiées par défaut `t_dwExStyle`, à l’aide de l’opérateur OR logique

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Présentation des caractéristiques de fenêtre](../../atl/understanding-window-traits.md)


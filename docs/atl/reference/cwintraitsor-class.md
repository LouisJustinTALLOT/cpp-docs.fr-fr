---
title: Classe CWinTraitsOR
ms.date: 11/04/2016
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
ms.openlocfilehash: 825f79190c6f68cd1372154e4e02f430f545aa48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330281"
---
# <a name="cwintraitsor-class"></a>Classe CWinTraitsOR

Cette classe fournit une méthode pour standardiser les styles utilisés lors de la création d’un objet de fenêtre.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
Styles de fenêtre étendus par défaut.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Récupère les styles étendus pour l’objet. `CWinTraitsOR`|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Récupère les styles standard `CWinTraitsOR` pour l’objet.|

## <a name="remarks"></a>Notes

Cette classe [de traits de fenêtre](../../atl/understanding-window-traits.md) fournit une méthode simple pour standardiser les styles utilisés pour la création d’un objet de fenêtre ATL. Utilisez une spécialisation de cette classe comme paramètre de modèle pour [CWindowImpl](../../atl/reference/cwindowimpl-class.md) ou un autre des classes de fenêtre d’ATL pour spécifier l’ensemble minimum de styles standard et étendus à utiliser pour les instances de cette classe de fenêtre.

Utilisez une spécialisation de ce modèle si vous voulez vous assurer que certains styles sont définis pour tous les cas de la classe de fenêtre tout en permettant d’autres styles d’être définis sur une base par instance dans l’appel à [CWindowImpl::Créer](../../atl/reference/cwindowimpl-class.md#create).

Si vous souhaitez fournir des styles de fenêtre par défaut qui ne `CWindowImpl::Create`seront utilisés que lorsqu’aucun autre style n’est spécifié dans l’appel à , utilisez [CWinTraits](../../atl/reference/cwintraits-class.md) à la place.

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle

Appelez cette fonction pour récupérer une combinaison (en utilisant l’opérateur DE LA source d’OR logique) des styles standard de l’objet `CWinTraits` et des styles par défaut spécifiés par *t_dwStyle*.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Styles utilisés pour la création d’une fenêtre.

### <a name="return-value"></a>Valeur de retour

Une combinaison de styles qui sont passés en *dwStyle* et les par défaut spécifiés par `t_dwStyle`, en utilisant l’opérateur OR logique.

## <a name="cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle

Appelez cette fonction pour récupérer une combinaison (en utilisant l’opérateur DE LAmentation logique) des styles étendus de l’objet `CWinTraits` et des styles par défaut spécifiés par `t_dwStyle`.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Paramètres

*dwExStyle (en anglais)*<br/>
Styles étendus utilisés pour la création d’une fenêtre.

### <a name="return-value"></a>Valeur de retour

Une combinaison de styles étendus qui sont passés en `t_dwExStyle` *dwExStyle* et par défaut spécifiés par , en utilisant l’opérateur OR logique

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Comprendre les traits de fenêtre](../../atl/understanding-window-traits.md)

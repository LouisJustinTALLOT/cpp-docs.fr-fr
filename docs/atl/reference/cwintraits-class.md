---
description: 'En savoir plus sur : classe CWinTraits'
title: CWinTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
ms.openlocfilehash: 3f23342cae58d70a602ebce1dcbe7efcddf36781
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140086"
---
# <a name="cwintraits-class"></a>CWinTraits, classe

Cette classe fournit une méthode permettant de standardiser les styles utilisés lors de la création d’un objet Window.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>Paramètres

*t_dwStyle*<br/>
Styles de fenêtre standard par défaut.

*t_dwExStyle*<br/>
Styles de fenêtre étendus par défaut.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinTraits :: GetWndExStyle](#getwndexstyle)|Statique Récupère les styles étendus pour l' `CWinTraits` objet.|
|[CWinTraits :: GetWndStyle](#getwndstyle)|Statique Récupère les styles standard pour l' `CWinTraits` objet.|

## <a name="remarks"></a>Notes

Cette classe de [traits de fenêtre](../../atl/understanding-window-traits.md) fournit une méthode simple pour standardiser les styles utilisés pour la création d’un objet de fenêtre ATL. Utilisez une spécialisation de cette classe en tant que paramètre de modèle dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md) ou une autre des classes de fenêtre d’ATL pour spécifier les styles standard et étendus par défaut utilisés pour les instances de cette classe de fenêtre.

Utilisez ce modèle lorsque vous souhaitez fournir des styles de fenêtre par défaut qui seront utilisés uniquement quand aucun autre style n’est spécifié dans l’appel à [CWindowImpl :: Create](../../atl/reference/cwindowimpl-class.md#create).

ATL fournit trois spécialisations prédéfinies de ce modèle pour les combinaisons couramment utilisées de styles de fenêtre :

- `CControlWinTraits`

   Conçu pour une fenêtre de contrôle standard. Les styles standard suivants sont utilisés : WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN et WS_CLIPSIBLINGS. Il n’existe pas de styles étendus.

- `CFrameWinTraits`

   Conçu pour une fenêtre frame standard. Les styles standard utilisés sont les suivants : WS_OVERLAPPEDWINDOW, WS_CLIPCHILDREN et WS_CLIPSIBLINGS. Les styles étendus utilisés sont les suivants : WS_EX_APPWINDOW et WS_EX_WINDOWEDGE.

- `CMDIChildWinTraits`

   Conçu pour une fenêtre enfant MDI standard. Les styles standard utilisés sont les suivants : WS_OVERLAPPEDWINDOW, WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN et WS_CLIPSIBLINGS. Les styles étendus utilisés sont les suivants : WS_EX_MDICHILD.

Si vous souhaitez vous assurer que certains styles sont définis pour toutes les instances de la classe de fenêtre tout en autorisant la définition d’autres styles pour chaque instance, utilisez [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) à la place.

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="cwintraitsgetwndstyle"></a><a name="getwndstyle"></a> CWinTraits :: GetWndStyle

Appelez cette fonction pour récupérer les styles standard de l' `CWinTraits` objet.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Styles standard utilisés pour la création d’une fenêtre. Si *dwStyle* a la valeur 0, les valeurs de style de modèle ( `t_dwStyle` ) sont retournées. Si *dwStyle* est différent de zéro, *dwStyle* est retourné.

### <a name="return-value"></a>Valeur renvoyée

Styles de fenêtre standard de l’objet.

## <a name="cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a> CWinTraits :: GetWndExStyle

Appelez cette fonction pour récupérer les styles étendus de l' `CWinTraits` objet.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Styles étendus utilisés pour la création d’une fenêtre. Si *dwExStyle* a la valeur 0, les valeurs de style de modèle ( `t_dwExStyle` ) sont retournées. Si *dwExStyle* est différent de zéro, *dwExStyle* est retourné.

### <a name="return-value"></a>Valeur renvoyée

Styles de fenêtre étendus de l’objet.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctionnement des traits de fenêtre](../../atl/understanding-window-traits.md)

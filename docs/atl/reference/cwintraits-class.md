---
title: Classe CWinTraits
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
ms.openlocfilehash: fd73f733e4eff21da92937d1e1b0cce21552a48c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330309"
---
# <a name="cwintraits-class"></a>Classe CWinTraits

Cette classe fournit une méthode pour standardiser les styles utilisés lors de la création d’un objet de fenêtre.

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
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Statique) Récupère les styles étendus pour l’objet. `CWinTraits`|
|[CWinTraits::GetWndStyle](#getwndstyle)|(Statique) Récupère les styles standard `CWinTraits` pour l’objet.|

## <a name="remarks"></a>Notes

Cette classe [de traits de fenêtre](../../atl/understanding-window-traits.md) fournit une méthode simple pour standardiser les styles utilisés pour la création d’un objet de fenêtre ATL. Utilisez une spécialisation de cette classe comme paramètre de modèle pour [CWindowImpl](../../atl/reference/cwindowimpl-class.md) ou un autre des classes de fenêtre d’ATL pour spécifier la norme par défaut et les styles étendus utilisés pour les instances de cette classe de fenêtre.

Utilisez ce modèle lorsque vous souhaitez fournir des styles de fenêtre par défaut qui ne seront utilisés que lorsqu’aucun autre style n’est spécifié dans l’appel à [CWindowImpl::Créer](../../atl/reference/cwindowimpl-class.md#create).

ATL fournit trois spécialisations prédéfinies de ce modèle pour les combinaisons couramment utilisées de styles de fenêtre:

- `CControlWinTraits`

   Conçu pour une fenêtre de contrôle standard. Les styles standard suivants sont utilisés : WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN et WS_CLIPSIBLINGS. Il n’y a pas de styles étendus.

- `CFrameWinTraits`

   Conçu pour une fenêtre de cadre standard. Les styles standard utilisés sont les suivants : WS_OVERLAPPEDWINDOW, WS_CLIPCHILDREN et WS_CLIPSIBLINGS. Les styles étendus utilisés comprennent: WS_EX_APPWINDOW et WS_EX_WINDOWEDGE.

- `CMDIChildWinTraits`

   Conçu pour une fenêtre mÉDI standard pour enfants. Les styles standard utilisés sont les suivants : WS_OVERLAPPEDWINDOW, WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN et WS_CLIPSIBLINGS. Les styles étendus utilisés comprennent: WS_EX_MDICHILD.

Si vous voulez vous assurer que certains styles sont définis pour tous les cas de la classe de fenêtre tout en permettant d’autres styles d’être définis sur une base par instance, utilisez [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) à la place.

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="cwintraitsgetwndstyle"></a><a name="getwndstyle"></a>CWinTraits::GetWndStyle

Appelez cette fonction pour récupérer `CWinTraits` les styles standard de l’objet.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Styles standard utilisés pour la création d’une fenêtre. Si *dwStyle* est 0, les`t_dwStyle`valeurs de style de modèle ( ) sont retournées. Si *dwStyle* n’est paszero, *dwStyle* est retourné.

### <a name="return-value"></a>Valeur de retour

Les styles de fenêtre standard de l’objet.

## <a name="cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraits::GetWndExStyle

Appelez cette fonction pour récupérer `CWinTraits` les styles étendus de l’objet.

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Paramètres

*dwExStyle (en anglais)*<br/>
Styles étendus utilisés pour la création d’une fenêtre. Si *dwExStyle* est 0, les`t_dwExStyle`valeurs de style de modèle ( ) sont retournées. Si *dwExStyle* n’est paszero, *dwExStyle* est retourné.

### <a name="return-value"></a>Valeur de retour

Les styles de fenêtre étendue de l’objet.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Comprendre les traits de fenêtre](../../atl/understanding-window-traits.md)

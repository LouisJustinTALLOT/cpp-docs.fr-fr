---
title: Macros de classe de fenêtre
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 18c0912c506bc52421b18d36346204b557c0fc5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325731"
---
# <a name="window-class-macros"></a>Macros de classe de fenêtre

Ces macros définissent les utilitaires de classe de fenêtre.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Vous permet de spécifier le nom d’une nouvelle classe de fenêtre.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Studio visuel 2017) Vous permet de spécifier le nom d’une nouvelle classe de fenêtre et la classe d’enceinte dont la procédure de fenêtre de la nouvelle classe utilisera.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Vous permet de spécifier le nom d’une classe de fenêtre existante sur laquelle une nouvelle classe de fenêtre sera basée.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Vous permet de spécifier les paramètres d’une classe.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a>DECLARE_WND_CLASS

Vous permet de spécifier le nom d’une nouvelle classe de fenêtre. Placez cette macro dans la classe de contrôle d’un contrôle ATL ActiveX.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Paramètres

*WndClassName (WndClassName)*<br/>
[dans] Le nom de la nouvelle classe de fenêtre. Si NULL, ATL va générer un nom de classe de fenêtre.

### <a name="remarks"></a>Notes

Si vous utilisez l’option /permissive- compilateur, alors DECLARE_WND_CLASS provoquera une erreur de compilateur; utiliser DECLARE_WND_CLASS2 à la place.

DECLARE_WND_CLASS vous permet de spécifier le nom d’une nouvelle classe de fenêtre dont les informations seront gérées par [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS définit la nouvelle classe de fenêtre en mettant en œuvre la fonction statique suivante :

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS spécifie les styles suivants pour la nouvelle fenêtre :

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS spécifie également la couleur de fond de la fenêtre par défaut. Utilisez la [macro DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) pour fournir vos propres styles et couleur de fond.

[CWindowImpl](cwindowimpl-class.md) utilise la macro DECLARE_WND_CLASS pour créer une fenêtre basée sur une nouvelle classe de fenêtre. Pour remplacer ce comportement, utilisez la [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) macro, ou fournissez votre propre implémentation de la fonction [GetWndClassInfo.](cwindowimpl-class.md#getwndclassinfo)

Pour plus d’informations sur l’utilisation des fenêtres dans ATL, voir l’article [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

(Studio visuel 2017) Semblable à DECLARE_WND_CLASS, mais avec un paramètre supplémentaire qui évite une erreur de nom dépendante lors de la compilation avec l’option /permissive.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Paramètres

*WndClassName (WndClassName)*<br/>
[dans] Le nom de la nouvelle classe de fenêtre. Si NULL, ATL va générer un nom de classe de fenêtre.

*Enclosclass*<br/>
[dans] Le nom de la classe de fenêtre qui entoure la nouvelle classe de fenêtre. Ne peut pas avoir la valeur NULL.

### <a name="remarks"></a>Notes

Si vous utilisez l’option /permissive, alors DECLARE_WND_CLASS provoquera une erreur de compilation parce qu’elle contient un nom dépendant. DECLARE_WND_CLASS2 vous oblige à nommer explicitement la classe dans laquelle cette macro est utilisée et ne provoque pas l’erreur sous le drapeau /permissif.
Sinon, cette macro est identique à [DECLARE_WND_CLASS](#declare_wnd_class).

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

Vous permet de spécifier les paramètres d’une classe. Placez cette macro dans la classe de contrôle d’un contrôle ATL ActiveX.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Paramètres

*WndClassName (WndClassName)*<br/>
[dans] Le nom de la classe de fenêtre qui superclassera *OrigWndClassName*. Si NULL, ATL va générer un nom de classe de fenêtre.

*OrigWndClassName*<br/>
[dans] Le nom d’une classe de fenêtre existante.

### <a name="remarks"></a>Notes

Cette macro vous permet de spécifier le nom d’une classe de fenêtre qui superclassera une classe de fenêtre existante. [CWndClassInfo](cwndclassinfo-class.md) gère les informations de la superclasse.

DECLARE_WND_SUPERCLASS met en œuvre la fonction statique suivante :

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Par défaut, [CWindowImpl](cwindowimpl-class.md) utilise la [macro DECLARE_WND_CLASS](#declare_wnd_class) pour créer une fenêtre basée sur une nouvelle classe de fenêtre. En spécifiant la DECLARE_WND_SUPERCLASS `CWindowImpl`macro dans une classe dérivée, la classe de fenêtre sera basée sur une classe existante, mais utilisera votre procédure de fenêtre. Cette technique est appelée superclassement.

En plus d’utiliser les macros DECLARE_WND_CLASS et DECLARE_WND_SUPERCLASS, vous pouvez remplacer la fonction [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) avec votre propre implémentation.

Pour plus d’informations sur l’utilisation des fenêtres dans ATL, voir l’article [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

Vous permet de spécifier le nom d’une classe de fenêtre existante sur laquelle une nouvelle classe de fenêtre sera basée. Placez cette macro dans la classe de contrôle d’un contrôle ATL ActiveX.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Paramètres

*WndClassName (WndClassName)*<br/>
[dans] Le nom de la nouvelle classe de fenêtre. Si NULL, ATL va générer un nom de classe de fenêtre.

*style*<br/>
[dans] Le style de la fenêtre.

*bkgnd bkgnd*<br/>
[dans] La couleur de fond de la fenêtre.

### <a name="remarks"></a>Notes

Cette macro vous permet de spécifier les paramètres de classe d’une nouvelle classe de fenêtre, dont les informations seront gérées par [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX définit la nouvelle classe de fenêtre en mettant en œuvre la fonction statique suivante :

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Si vous souhaitez utiliser les styles par défaut et la couleur de fond, utilisez la [macro DECLARE_WND_CLASS.](#declare_wnd_class) Pour plus d’informations sur l’utilisation des fenêtres dans ATL, voir l’article [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Voir aussi

[Macros](atl-macros.md)

---
title: Macros de classe de fenêtre
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: ca19eba1632ef3754b704c82ad5a872160ae0c91
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834464"
---
# <a name="window-class-macros"></a>Macros de classe de fenêtre

Ces macros définissent les utilitaires de classe de fenêtre.

|Nom|Description|
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Vous permet de spécifier le nom d’une nouvelle classe de fenêtre.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Vous permet de spécifier le nom d’une nouvelle classe de fenêtre et la classe englobante dont la procédure de fenêtre doit être utilisée par la nouvelle classe.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Vous permet de spécifier le nom d’une classe de fenêtre existante sur laquelle sera basée une nouvelle classe de fenêtre.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Vous permet de spécifier les paramètres d’une classe.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin. h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a> DECLARE_WND_CLASS

Vous permet de spécifier le nom d’une nouvelle classe de fenêtre. Placez cette macro dans la classe de contrôle d’un contrôle ActiveX ATL.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Paramètres

*WndClassName*<br/>
dans Nom de la nouvelle classe de fenêtre. Si la valeur est NULL, ATL génère un nom de classe de fenêtre.

### <a name="remarks"></a>Notes

Si vous utilisez l’option du compilateur/permissive-, DECLARE_WND_CLASS provoque une erreur du compilateur. Utilisez à la place DECLARE_WND_CLASS2.

DECLARE_WND_CLASS vous permet de spécifier le nom d’une nouvelle classe de fenêtre dont les informations seront gérées par [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS définit la nouvelle classe de fenêtre en implémentant la fonction statique suivante :

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS spécifie les styles suivants pour la nouvelle fenêtre :

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS spécifie également la couleur d’arrière-plan par défaut de la fenêtre. Utilisez la macro [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) pour fournir vos propres styles et couleur d’arrière-plan.

[CWindowImpl](cwindowimpl-class.md) utilise la macro DECLARE_WND_CLASS pour créer une fenêtre basée sur une nouvelle classe de fenêtre. Pour remplacer ce comportement, utilisez la macro [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) ou fournissez votre propre implémentation de la fonction [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) .

Pour plus d’informations sur l’utilisation de Windows dans ATL, consultez l’article [classes de fenêtre ATL](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a> DECLARE_WND_CLASS2

(Visual Studio 2017) Semblable à DECLARE_WND_CLASS, mais avec un paramètre supplémentaire qui évite une erreur de nom dépendant lors de la compilation avec l’option/permissive-.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Paramètres

*WndClassName*<br/>
dans Nom de la nouvelle classe de fenêtre. Si la valeur est NULL, ATL génère un nom de classe de fenêtre.

*EnclosingClass*<br/>
dans Nom de la classe de fenêtre qui englobe la nouvelle classe de fenêtre. Ne peut pas avoir la valeur NULL.

### <a name="remarks"></a>Notes

Si vous utilisez l’option/permissive-, DECLARE_WND_CLASS entraîne une erreur de compilation, car elle contient un nom dépendant. DECLARE_WND_CLASS2 vous oblige à nommer explicitement la classe dans laquelle cette macro est utilisée et qui ne provoque pas l’erreur sous l’indicateur/permissive-.
Dans le cas contraire, cette macro est identique à [DECLARE_WND_CLASS](#declare_wnd_class).

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a> DECLARE_WND_SUPERCLASS

Vous permet de spécifier les paramètres d’une classe. Placez cette macro dans la classe de contrôle d’un contrôle ActiveX ATL.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Paramètres

*WndClassName*<br/>
dans Nom de la classe de fenêtre qui va superclasser *OrigWndClassName*. Si la valeur est NULL, ATL génère un nom de classe de fenêtre.

*OrigWndClassName*<br/>
dans Nom d’une classe de fenêtre existante.

### <a name="remarks"></a>Notes

Cette macro vous permet de spécifier le nom d’une classe de fenêtre qui va superclasser une classe de fenêtre existante. [CWndClassInfo](cwndclassinfo-class.md) gère les informations de la superclasse.

DECLARE_WND_SUPERCLASS implémente la fonction statique suivante :

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Par défaut, [CWindowImpl](cwindowimpl-class.md) utilise la macro [DECLARE_WND_CLASS](#declare_wnd_class) pour créer une fenêtre basée sur une nouvelle classe de fenêtre. En spécifiant la macro DECLARE_WND_SUPERCLASS dans une `CWindowImpl` classe dérivée de, la classe de fenêtre sera basée sur une classe existante, mais utilisera votre procédure de fenêtre. Cette technique est appelée superclassement.

Outre l’utilisation des macros DECLARE_WND_CLASS et DECLARE_WND_SUPERCLASS, vous pouvez remplacer la fonction [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) par votre propre implémentation.

Pour plus d’informations sur l’utilisation de Windows dans ATL, consultez l’article [classes de fenêtre ATL](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a> DECLARE_WND_CLASS_EX

Vous permet de spécifier le nom d’une classe de fenêtre existante sur laquelle sera basée une nouvelle classe de fenêtre. Placez cette macro dans la classe de contrôle d’un contrôle ActiveX ATL.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Paramètres

*WndClassName*<br/>
dans Nom de la nouvelle classe de fenêtre. Si la valeur est NULL, ATL génère un nom de classe de fenêtre.

*style*<br/>
dans Style de la fenêtre.

*pinceau*<br/>
dans Couleur d’arrière-plan de la fenêtre.

### <a name="remarks"></a>Notes

Cette macro vous permet de spécifier les paramètres de classe d’une nouvelle classe de fenêtre, dont les informations seront gérées par [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX définit la nouvelle classe de fenêtre en implémentant la fonction statique suivante :

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Si vous souhaitez utiliser les styles et la couleur d’arrière-plan par défaut, utilisez la macro [DECLARE_WND_CLASS](#declare_wnd_class) . Pour plus d’informations sur l’utilisation de Windows dans ATL, consultez l’article [classes de fenêtre ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Voir aussi

[Macros](atl-macros.md)

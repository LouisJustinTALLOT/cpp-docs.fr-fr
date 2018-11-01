---
title: Macros de classe de fenêtre
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 75a6a769770c9de8b26c08fae852197cdb99248e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503152"
---
# <a name="window-class-macros"></a>Macros de classe de fenêtre

Ces macros définissent des utilitaires de classe de fenêtre.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Vous permet de spécifier le nom d’une nouvelle classe de fenêtre.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Vous permet de spécifier le nom d’une nouvelle classe de fenêtre et de la classe englobante dont la nouvelle classe utilisera la procédure de fenêtre.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Vous permet de spécifier le nom d’une classe de fenêtre existante sur laquelle une nouvelle classe de fenêtre doit être basée.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Vous permet de spécifier les paramètres d’une classe.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

##  <a name="declare_wnd_class"></a>  DECLARE_WND_CLASS

Vous permet de spécifier le nom d’une nouvelle classe de fenêtre. Placez cette macro dans la classe de contrôle d’un contrôle ActiveX ATL.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Paramètres

*WndClassName*<br/>
[in] Le nom de la nouvelle classe de fenêtre. Si NULL, ATL générera un nom de classe de fenêtre.

### <a name="remarks"></a>Notes

Si vous utilisez l’option /permissive-compiler, DECLARE_WND_CLASS provoquera une erreur du compilateur ; Utilisez DECLARE_WND_CLASS2 à la place.

DECLARE_WND_CLASS vous permet de spécifier le nom d’une nouvelle classe de fenêtre dont les informations seront gérées par [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS définit la nouvelle classe de fenêtre en implémentant la fonction statique suivante :

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS spécifie les styles suivants pour la nouvelle fenêtre :

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS spécifie également la couleur d’arrière-plan de la fenêtre par défaut. Utilisez le [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) macro pour fournir vos propres styles et de couleur d’arrière-plan.

[CWindowImpl](cwindowimpl-class.md) utilise la macro DECLARE_WND_CLASS pour créer une fenêtre basée sur une nouvelle classe de fenêtre. Pour remplacer ce comportement, utilisez le [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) (macro), ou fournir votre propre implémentation de la [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) (fonction).

Pour plus d’informations sur l’utilisation des fenêtres dans ATL, consultez l’article [Classes de fenêtre ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2

(Visual Studio 2017) Similaire à DECLARE_WND_CLASS, mais avec un paramètre supplémentaire qui permet d’éviter une erreur de nom dépendant lors de la compilation avec la /permissive-option.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Paramètres

*WndClassName*<br/>
[in] Le nom de la nouvelle classe de fenêtre. Si NULL, ATL générera un nom de classe de fenêtre.

*EnclosingClass*<br/>
[in] Le nom de la classe de fenêtre qui englobe la nouvelle classe de fenêtre. Ne peut pas être Null.

### <a name="remarks"></a>Notes

Si vous utilisez la /permissive-option, DECLARE_WND_CLASS entraîne une erreur de compilation, car elle contient un nom dépendant. DECLARE_WND_CLASS2 vous oblige à nommer explicitement la classe que cette macro est utilisée dans et n’entraîne pas l’erreur sous la /permissive-flag.
Sinon, cette macro est identique à [DECLARE_WND_CLASS](#declare_wnd_class).

##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS

Vous permet de spécifier les paramètres d’une classe. Placez cette macro dans la classe de contrôle d’un contrôle ActiveX ATL.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Paramètres

*WndClassName*<br/>
[in] Le nom de la fenêtre classe celle-ci sera *OrigWndClassName*. Si NULL, ATL générera un nom de classe de fenêtre.

*OrigWndClassName*<br/>
[in] Le nom d’une classe de fenêtre existante.

### <a name="remarks"></a>Notes

Cette macro vous permet de spécifier le nom d’une classe de fenêtre qui sera superclasse une classe de fenêtre existante. [CWndClassInfo](cwndclassinfo-class.md) gère les informations de la superclasse.

DECLARE_WND_SUPERCLASS implémente la fonction statique suivante :

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Par défaut, [CWindowImpl](cwindowimpl-class.md) utilise le [DECLARE_WND_CLASS](#declare_wnd_class) macro pour créer une fenêtre basée sur une nouvelle classe de fenêtre. En spécifiant la macro DECLARE_WND_SUPERCLASS dans un `CWindowImpl`-classe dérivée, la classe de fenêtre est basée sur une classe existante mais utilisera votre procédure de fenêtre. Cette technique est appelée surclasser.

Outre l’utilisation des macros DECLARE_WND_CLASS et DECLARE_WND_SUPERCLASS, vous pouvez remplacer le [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) fonction avec votre propre implémentation.

Pour plus d’informations sur l’utilisation des fenêtres dans ATL, consultez l’article [Classes de fenêtre ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX

Vous permet de spécifier le nom d’une classe de fenêtre existante sur laquelle une nouvelle classe de fenêtre doit être basée. Placez cette macro dans la classe de contrôle d’un contrôle ActiveX ATL.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Paramètres

*WndClassName*<br/>
[in] Le nom de la nouvelle classe de fenêtre. Si NULL, ATL générera un nom de classe de fenêtre.

*style*<br/>
[in] Le style de la fenêtre.

*arrière-plan*<br/>
[in] La couleur d’arrière-plan de la fenêtre.

### <a name="remarks"></a>Notes

Cette macro vous permet de spécifier les paramètres de la classe d’une nouvelle classe de fenêtre, dont les informations seront gérées par [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX définit la nouvelle classe de fenêtre en implémentant la fonction statique suivante :

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Si vous souhaitez utiliser les styles par défaut et la couleur d’arrière-plan, utilisez la [DECLARE_WND_CLASS](#declare_wnd_class) macro. Pour plus d’informations sur l’utilisation des fenêtres dans ATL, consultez l’article [Classes de fenêtre ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Voir aussi

[Macros](atl-macros.md)


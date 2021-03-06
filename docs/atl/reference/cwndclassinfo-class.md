---
description: 'En savoir plus sur : classe CWndClassInfo'
title: CWndClassInfo, classe
ms.date: 11/04/2016
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: 7a857812fa35743fbab0968fb94095bf8fdcabcf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140021"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo, classe

Cette classe fournit des méthodes pour inscrire des informations pour une classe de fenêtre.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWndClassInfo
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|[S’inscrire](#register)|Inscrit la classe de fenêtre.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|-|-|
|[m_atom](#m_atom)|Identifie de façon unique la classe de fenêtre inscrite.|
|[m_bSystemCursor](#m_bsystemcursor)|Spécifie si la ressource de curseur fait référence à un curseur système ou à un curseur contenu dans une ressource de module.|
|[m_lpszCursorID](#m_lpszcursorid)|Spécifie le nom de la ressource curseur.|
|[m_lpszOrigName](#m_lpszorigname)|Contient le nom d’une classe de fenêtre existante.|
|[m_szAutoName](#m_szautoname)|Contient un nom généré par ATL de la classe de fenêtre.|
|[m_wc](#m_wc)|Gère les informations de classe de fenêtre dans une `WNDCLASSEX` structure.|
|[pWndProc](#pwndproc)|Pointe vers la procédure de fenêtre d’une classe de fenêtre existante.|

## <a name="remarks"></a>Notes

`CWndClassInfo` gère les informations d’une classe de fenêtre. En général, vous utilisez `CWndClassInfo` l’une des trois macros, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX ou DECLARE_WND_SUPERCLASS, comme décrit dans le tableau suivant :

|Macro|Description|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` inscrit des informations pour une nouvelle classe de fenêtre.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` inscrit des informations pour une nouvelle classe de fenêtre, y compris les paramètres de classe.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` inscrit des informations pour une classe de fenêtre qui est basée sur une classe existante, mais qui utilise une procédure de fenêtre différente. Cette technique est appelée superclassement.|

Par défaut, [CWindowImpl](../../atl/reference/cwindowimpl-class.md) comprend la `DECLARE_WND_CLASS` macro pour créer une fenêtre basée sur une nouvelle classe de fenêtre. DECLARE_WND_CLASS fournit les styles et la couleur d’arrière-plan par défaut pour le contrôle. Si vous souhaitez spécifier vous-même le style et la couleur d’arrière-plan, dérivez votre classe de `CWindowImpl` et incluez la macro DECLARE_WND_CLASS_EX dans la définition de votre classe.

Si vous souhaitez créer une fenêtre basée sur une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et incluez la macro DECLARE_WND_SUPERCLASS dans la définition de votre classe. Par exemple :

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Pour plus d’informations sur les classes de fenêtre, consultez [classes de fenêtre](/windows/win32/winmsg/window-classes) dans le SDK Windows.

Pour plus d’informations sur l’utilisation de Windows dans ATL, consultez l’article [classes de fenêtre ATL](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a> CWndClassInfo :: m_atom

Contient l’identificateur unique de la classe de fenêtre inscrite.

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a> CWndClassInfo :: m_bSystemCursor

Si la valeur est TRUE, la ressource de curseur système est chargée lors de l’inscription de la classe de fenêtre.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Notes

Dans le cas contraire, la ressource de curseur contenue dans votre module sera chargée.

`CWndClassInfo` utilise `m_bSystemCursor` uniquement lorsque le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) est spécifié. Dans ce cas, `m_bSystemCursor` est initialisé à true. Pour plus d’informations, consultez la vue d’ensemble de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a> CWndClassInfo :: m_lpszCursorID

Spécifie soit le nom de la ressource de curseur, soit l’identificateur de ressource dans le mot de poids faible et zéro dans le mot de poids fort.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Notes

Lorsque la classe de fenêtre est inscrite, le handle du curseur identifié par `m_lpszCursorID` est récupéré et stocké par [m_wc](#m_wc).

`CWndClassInfo` utilise `m_lpszCursorID` uniquement lorsque le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) est spécifié. Dans ce cas, `m_lpszCursorID` est initialisé à IDC_ARROW. Pour plus d’informations, consultez la vue d’ensemble de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a> CWndClassInfo :: m_lpszOrigName

Contient le nom d’une classe de fenêtre existante.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Notes

`CWndClassInfo` utilise `m_lpszOrigName` uniquement lorsque vous incluez la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) dans la définition de votre classe. Dans ce cas, `CWndClassInfo` enregistre une classe de fenêtre basée sur la classe nommée par `m_lpszOrigName` . Pour plus d’informations, consultez la vue d’ensemble de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a> CWndClassInfo :: m_szAutoName

Contient le nom de la classe de fenêtre.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Notes

`CWndClassInfo` utilise `m_szAutoName` uniquement si la valeur null est transmise pour le `WndClassName` paramètre à [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) ou [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL crée un nom lorsque la classe de fenêtre est inscrite.

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a> CWndClassInfo :: m_wc

Gère les informations de classe de fenêtre dans une structure [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw) .

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Notes

Si vous avez spécifié le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) , `m_wc` contient des informations sur une nouvelle classe de fenêtre.

Si vous avez spécifié la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) , `m_wc` contient des informations sur une superclasse, c’est-à-dire une classe de fenêtre qui est basée sur une classe existante, mais qui utilise une procédure de fenêtre différente. [m_lpszOrigName](#m_lpszorigname) et [pWndProc](#pwndproc) enregistrent la procédure de fenêtre et le nom de la classe de fenêtre existante, respectivement.

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a> CWndClassInfo ::p WndProc

Pointe vers la procédure de fenêtre d’une classe de fenêtre existante.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Notes

`CWndClassInfo` utilise `pWndProc` uniquement lorsque vous incluez la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) dans la définition de votre classe. Dans ce cas, `CWndClassInfo` enregistre une classe de fenêtre qui est basée sur une classe existante, mais utilise une procédure de fenêtre différente. La procédure de fenêtre de la classe de fenêtre existante est enregistrée dans `pWndProc` . Pour plus d’informations, consultez la vue d’ensemble de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) .

## <a name="cwndclassinforegister"></a><a name="register"></a> CWndClassInfo :: Register

Appelé par [CWindowImpl :: Create](../../atl/reference/cwindowimpl-class.md#create) pour inscrire la classe de fenêtre si elle n’a pas encore été inscrite.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Paramètres

*pProc*<br/>
à Spécifie la procédure de fenêtre d’origine d’une classe de fenêtre existante.

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, un atome qui identifie de façon unique la classe de fenêtre en cours d’inscription. Sinon, il prend la valeur 0.

### <a name="remarks"></a>Notes

Si vous avez spécifié le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) , `Register` inscrit une nouvelle classe de fenêtre. Dans ce cas, le paramètre *pProc* n’est pas utilisé.

Si vous avez spécifié la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) , `Register` inscrit une superclasse, c’est-à-dire une classe de fenêtre basée sur une classe existante, mais utilisant une procédure de fenêtre différente. La procédure de fenêtre de la classe de fenêtre existante est retournée dans *pProc*.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

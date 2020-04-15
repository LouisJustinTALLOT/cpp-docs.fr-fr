---
title: Classe CWndClassInfo
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
ms.openlocfilehash: 01706bf61c3b977c28998325ece68724cfbc7452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330339"
---
# <a name="cwndclassinfo-class"></a>Classe CWndClassInfo

Cette classe fournit des méthodes pour l’enregistrement des informations pour une classe de fenêtre.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWndClassInfo
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|[S'inscrire](#register)|Enregistre la classe de fenêtre.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_atom](#m_atom)|Identifie uniquement la classe de fenêtre enregistrée.|
|[m_bSystemCursor](#m_bsystemcursor)|Précise si la ressource de curseur se réfère à un curseur du système ou à un curseur contenu dans une ressource de module.|
|[m_lpszCursorID](#m_lpszcursorid)|Spécifie le nom de la ressource curseur.|
|[m_lpszOrigName](#m_lpszorigname)|Contient le nom d’une classe de fenêtre existante.|
|[m_szAutoName](#m_szautoname)|Tient un nom généré par ATL de la classe de fenêtre.|
|[m_wc](#m_wc)|Conserve les informations de `WNDCLASSEX` classe de fenêtre dans une structure.|
|[pWndProc](#pwndproc)|Indique la procédure de fenêtre d’une classe de fenêtre existante.|

## <a name="remarks"></a>Notes

`CWndClassInfo`gère l’information d’une classe de fenêtre. Vous utilisez `CWndClassInfo` généralement l’une des trois macros, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX ou DECLARE_WND_SUPERCLASS, comme décrit dans le tableau suivant :

|Macro|Description|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`enregistre des informations pour une nouvelle classe de fenêtre.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`enregistre des informations pour une nouvelle classe de fenêtre, y compris les paramètres de classe.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`enregistre des informations pour une classe de fenêtre qui est basée sur une classe existante, mais utilise une procédure de fenêtre différente. Cette technique est appelée superclassement.|

Par défaut, [CWindowImpl](../../atl/reference/cwindowimpl-class.md) inclut la `DECLARE_WND_CLASS` macro pour créer une fenêtre basée sur une nouvelle classe de fenêtre. DECLARE_WND_CLASS fournit des styles par défaut et la couleur de fond pour le contrôle. Si vous voulez spécifier le style et `CWindowImpl` la couleur de fond vous-même, dérivez votre classe et incluez la macro DECLARE_WND_CLASS_EX dans votre définition de classe.

Si vous souhaitez créer une fenêtre basée sur une `CWindowImpl` classe de fenêtre existante, dérivez votre classe et incluez la macro DECLARE_WND_SUPERCLASS dans votre définition de classe. Par exemple :

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Pour plus d’informations sur les cours de fenêtre, voir [Classes de fenêtre](/windows/win32/winmsg/window-classes) dans le SDK Windows.

Pour plus d’informations sur l’utilisation des fenêtres dans ATL, voir l’article [ATL Window Classes](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a>CWndClassInfo:m_atom

Contient l’identifiant unique pour la classe de fenêtre enregistrée.

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a>CWndClassInfo:m_bSystemCursor

Si VRAI, la ressource de curseur système sera chargée lorsque la classe de fenêtre est enregistrée.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Notes

Dans le cas contraire, la ressource de curseur contenue dans votre module sera chargée.

`CWndClassInfo`utilise `m_bSystemCursor` uniquement lorsque le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) est spécifiée. Dans ce `m_bSystemCursor` cas, est parasécé à TRUE. Pour plus d’informations, consultez la vue d’ensemble [de CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a>CWndClassInfo:m_lpszCursorID

Spécifie soit le nom de la ressource curseur ou l’identifiant de ressource dans le mot de faible ordre et zéro dans le mot de haute commande.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Notes

Lorsque la classe de fenêtre est enregistrée, la `m_lpszCursorID` poignée du curseur identifié par est récupérée et stockée par [m_wc](#m_wc).

`CWndClassInfo`utilise `m_lpszCursorID` uniquement lorsque le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou la macro [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) est spécifiée. Dans ce `m_lpszCursorID` cas, est paradé pour IDC_ARROW. Pour plus d’informations, consultez la vue d’ensemble [de CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a>CWndClassInfo:m_lpszOrigName

Contient le nom d’une classe de fenêtre existante.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Notes

`CWndClassInfo`utilise `m_lpszOrigName` uniquement lorsque vous incluez la [macro DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) dans votre définition de classe. Dans ce `CWndClassInfo` cas, enregistre une classe de `m_lpszOrigName`fenêtre basée sur la classe nommée par . Pour plus d’informations, consultez la vue d’ensemble [de CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a>CWndClassInfo:m_szAutoName

Tient le nom de la classe de fenêtre.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Notes

`CWndClassInfo`utilise `m_szAutoName` uniquement si NULL `WndClassName` est passé pour le paramètre à [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), le [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) ou [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL construira un nom lorsque la classe de fenêtre est enregistrée.

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a>CWndClassInfo:m_wc

Conserve l’information de classe de fenêtre dans une structure [WNDCLASSEX.](/windows/win32/api/winuser/ns-winuser-wndclassexw)

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Notes

Si vous avez spécifié la [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (la valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou la macro [DECLARE_WND_CLASS_EX,](window-class-macros.md#declare_wnd_class_ex) `m_wc` contient des informations sur une nouvelle classe de fenêtre.

Si vous avez [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) spécifié la DECLARE_WND_SUPERCLASS `m_wc` macro, contient des informations sur une superclasse - une classe de fenêtre qui est basée sur une classe existante, mais utilise une procédure de fenêtre différente. [m_lpszOrigName](#m_lpszorigname) et [pWndProc](#pwndproc) enregistrent respectivement le nom et la procédure de fenêtre de la classe de fenêtre existante.

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a>CWndClassInfo::pWndProc

Indique la procédure de fenêtre d’une classe de fenêtre existante.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Notes

`CWndClassInfo`utilise `pWndProc` uniquement lorsque vous incluez la [macro DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) dans votre définition de classe. Dans ce `CWndClassInfo` cas, enregistre une classe de fenêtre qui est basée sur une classe existante, mais utilise une procédure de fenêtre différente. La procédure de fenêtre de la `pWndProc`classe de fenêtre existante est enregistrée dans . Pour plus d’informations, consultez la vue d’ensemble [de CWndClassInfo.](../../atl/reference/cwndclassinfo-class.md)

## <a name="cwndclassinforegister"></a><a name="register"></a>CWndClassInfo::Enregistrement

Appelé par [CWindowImpl::Créer](../../atl/reference/cwindowimpl-class.md#create) pour enregistrer la classe de fenêtre si elle n’a pas encore été enregistrée.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Paramètres

*pProc (en)*<br/>
[out] Spécifie la procédure de fenêtre originale d’une classe de fenêtre existante.

### <a name="return-value"></a>Valeur de retour

En cas de succès, un atome qui identifie uniquement la classe de fenêtre étant enregistrée. Sinon, il prend la valeur 0.

### <a name="remarks"></a>Notes

Si vous avez spécifié la [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (la valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou la macro [DECLARE_WND_CLASS_EX,](window-class-macros.md#declare_wnd_class_ex) `Register` enregistre une nouvelle classe de fenêtre. Dans ce cas, le paramètre *pProc n’est* pas utilisé.

Si vous avez [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) spécifié la DECLARE_WND_SUPERCLASS `Register` macro, enregistre une superclasse — une classe de fenêtre qui est basée sur une classe existante mais qui utilise une procédure de fenêtre différente. La procédure de fenêtre de la classe de fenêtre existante est retournée en *pProc*.

## <a name="see-also"></a>Voir aussi

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

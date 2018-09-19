---
title: CWndClassInfo, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d674b2e3049d27f0e79eb082a44640f67a395dea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097880"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo, classe

Cette classe fournit des méthodes pour l’inscription des informations pour une classe de fenêtre.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWndClassInfo
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|[S’inscrire](#register)|Inscrit la classe de fenêtre.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_atom](#m_atom)|Identifie la classe de fenêtres inscrites.|
|[m_bSystemCursor](#m_bsystemcursor)|Spécifie si la ressource curseur fait référence à un curseur système ou à un curseur contenues dans une ressource de module.|
|[m_lpszCursorID](#m_lpszcursorid)|Spécifie le nom de la ressource curseur.|
|[m_lpszOrigName](#m_lpszorigname)|Contient le nom d’une classe de fenêtre existante.|
|[m_szAutoName](#m_szautoname)|Contient un nom généré ATL de la classe de fenêtre.|
|[m_wc](#m_wc)|Conserve les informations de classe de fenêtre dans un `WNDCLASSEX` structure.|
|[pWndProc](#pwndproc)|Pointe vers la procédure de fenêtre d’une classe de fenêtre existante.|

## <a name="remarks"></a>Notes

`CWndClassInfo` gère les informations d’une classe de fenêtre. Vous utilisez généralement `CWndClassInfo` via un des trois macros, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX ou DECLARE_WND_SUPERCLASS, comme décrit dans le tableau suivant :

|Macro|Description|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` enregistre les informations pour une nouvelle classe de fenêtre.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` enregistre les informations pour une nouvelle classe de fenêtre, y compris les paramètres de la classe.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` enregistre les informations pour une classe de fenêtre qui est basée sur une classe existante mais utilise une autre procédure de fenêtre. Cette technique est appelée surclasser.|

Par défaut, [CWindowImpl](../../atl/reference/cwindowimpl-class.md) inclut le `DECLARE_WND_CLASS` macro pour créer une fenêtre basée sur une nouvelle classe de fenêtre. DECLARE_WND_CLASS fournit les styles par défaut et la couleur d’arrière-plan pour le contrôle. Si vous souhaitez spécifier le style et la couleur d’arrière-plan vous-même, dérivez votre classe de `CWindowImpl` et incluez la macro DECLARE_WND_CLASS_EX dans votre définition de classe.

Si vous souhaitez créer une fenêtre basée sur une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et incluez la macro DECLARE_WND_SUPERCLASS dans votre définition de classe. Exemple :

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Pour plus d’informations sur les classes de fenêtre, consultez [Classes de fenêtre](https://msdn.microsoft.com/library/windows/desktop/ms632596) dans le SDK Windows.

Pour plus d’informations sur l’utilisation des fenêtres dans ATL, consultez l’article [Classes de fenêtre ATL](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

##  <a name="m_atom"></a>  CWndClassInfo::m_atom

Contient l’identificateur unique pour la classe de fenêtres inscrites.

```
ATOM m_atom;
```

##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor

Si la valeur est TRUE, la ressource du curseur système soit chargée lorsque la classe de fenêtre est inscrit.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Notes

Sinon, la ressource curseur contenue dans votre module sera chargée.

`CWndClassInfo` utilise `m_bSystemCursor` uniquement lorsque le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (la valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou le [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro est spécifiée. Dans ce cas, `m_bSystemCursor` est initialisé à la valeur TRUE. Pour plus d’informations, consultez le [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) vue d’ensemble.

##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID

Spécifie le nom de la ressource curseur ou l’identificateur de ressource dans le mot de poids faible et zéro dans le mot de poids fort.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Notes

Lorsque la classe de fenêtre est inscrit, le handle du curseur identifié par `m_lpszCursorID` est récupéré et stocké par [m_wc](#m_wc).

`CWndClassInfo` utilise `m_lpszCursorID` uniquement lorsque le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (la valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou le [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro est spécifiée. Dans ce cas, `m_lpszCursorID` est initialisé à IDC_ARROW. Pour plus d’informations, consultez le [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) vue d’ensemble.

##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName

Contient le nom d’une classe de fenêtre existante.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Notes

`CWndClassInfo` utilise `m_lpszOrigName` uniquement lorsque vous incluez le [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro dans votre définition de classe. Dans ce cas, `CWndClassInfo` enregistre une classe de fenêtre en fonction de la classe appelée par `m_lpszOrigName`. Pour plus d’informations, consultez le [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) vue d’ensemble.

##  <a name="m_szautoname"></a>  CWndClassInfo::m_szAutoName

Contient le nom de la classe de fenêtre.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Notes

`CWndClassInfo` utilise `m_szAutoName` uniquement si la valeur NULL est passée le `WndClassName` paramètre [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), le [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) ou [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . ATL construira un nom lors de la classe de fenêtre est inscrit.

##  <a name="m_wc"></a>  CWndClassInfo::m_wc

Conserve les informations de classe de fenêtre dans un [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577) structure.

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Notes

Si vous avez spécifié le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (la valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou le [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro, `m_wc` contient des informations sur un nouvelle classe de fenêtre.

Si vous avez spécifié le [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro, `m_wc` contient des informations sur une superclasse : une classe de fenêtre qui est basée sur une classe existante mais utilise une autre procédure de fenêtre. [m_lpszOrigName](#m_lpszorigname) et [pWndProc](#pwndproc) enregistrer les nom de la classe de fenêtre existante et la procédure de fenêtre, respectivement.

##  <a name="pwndproc"></a>  CWndClassInfo::pWndProc

Pointe vers la procédure de fenêtre d’une classe de fenêtre existante.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Notes

`CWndClassInfo` utilise `pWndProc` uniquement lorsque vous incluez le [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro dans votre définition de classe. Dans ce cas, `CWndClassInfo` enregistre une classe de fenêtre qui est basée sur une classe existante mais utilise une autre procédure de fenêtre. Procédure de fenêtre de la classe de fenêtre existante est enregistrée dans `pWndProc`. Pour plus d’informations, consultez le [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) vue d’ensemble.

##  <a name="register"></a>  CWndClassInfo::Register

Appelé par [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create) pour inscrire la classe de fenêtre si elle n’a pas encore été enregistré.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Paramètres

*pProc*<br/>
[out] Spécifie la procédure de fenêtre d’origine d’une classe de fenêtre existante.

### <a name="return-value"></a>Valeur de retour

Si l’opération réussit, un atome qui identifie la classe de fenêtre en cours d’inscription. Sinon, 0.

### <a name="remarks"></a>Notes

Si vous avez spécifié le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (la valeur par défaut dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) ou le [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro, `Register` inscrit une nouvelle classe de fenêtre. Dans ce cas, le *pProc* paramètre n’est pas utilisé.

Si vous avez spécifié le [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro, `Register` enregistre une superclasse : une classe de fenêtre qui est basée sur une classe existante mais utilise une autre procédure de fenêtre. Procédure de fenêtre de la classe de fenêtre existante est retournée dans *pProc*.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
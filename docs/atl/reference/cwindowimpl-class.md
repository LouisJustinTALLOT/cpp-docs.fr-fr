---
title: CWindowImpl (classe)
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::CWindowImpl::DefWindowProc
- ATLWIN/ATL::CWindowImpl::GetCurrentMessage
- ATLWIN/ATL::CWindowImpl::GetWindowProc
- ATLWIN/ATL::CWindowImpl::OnFinalMessage
- ATLWIN/ATL::CWindowImpl::SubclassWindow
- ATLWIN/ATL::CWindowImpl::UnsubclassWindow
- ATLWIN/ATL::CWindowImpl::GetWndClassInfo
- ATLWIN/ATL::CWindowImpl::WindowProc
- ATLWIN/ATL::CWindowImpl::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: b8b633dcf4ea14e899ee00552b553476cf697689
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862964"
---
# <a name="cwindowimpl-class"></a>CWindowImpl (classe)

Fournit des méthodes pour créer ou sous-classer une fenêtre.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre nouvelle classe, dérivée de `CWindowImpl`.

*TBase*<br/>
Classe de base de votre classe. Par défaut, la classe de base est [CWindow](../../atl/reference/cwindow-class.md).

*TWinTraits*<br/>
[Classe de traits](../../atl/understanding-window-traits.md) qui définit des styles pour votre fenêtre. Par défaut, il s’agit de `CControlWinTraits`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CWindowImpl :: Create](#create)|Crée une fenêtre.|

### <a name="cwindowimplbaset-methods"></a>Méthodes CWindowImplBaseT

|||
|-|-|
|[DefWindowProc](#defwindowproc)|Fournit le traitement du message par défaut.|
|[GetCurrentMessage](#getcurrentmessage)|Retourne le message actuel.|
|[GetWindowProc](#getwindowproc)|Retourne la procédure de fenêtre active.|
|[OnFinalMessage](#onfinalmessage)|Appelé après la réception du dernier message (généralement WM_NCDESTROY).|
|[SubclassWindow](#subclasswindow)|Sous-classe une fenêtre.|
|[UnsubclassWindow](#unsubclasswindow)|Restaure une fenêtre précédemment sous-classée.|

### <a name="static-methods"></a>Méthodes statiques

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|Retourne une instance statique de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), qui gère les informations de classe de fenêtre.|
|[WindowProc](#windowproc)|Traite les messages envoyés à la fenêtre.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Pointe vers la procédure de fenêtre d'origine de la classe de fenêtre.|

## <a name="remarks"></a>Notes

Vous pouvez utiliser `CWindowImpl` pour créer une fenêtre ou une sous-classe dans une fenêtre existante. la procédure de fenêtre `CWindowImpl` utilise une table des messages pour diriger les messages vers les gestionnaires appropriés.

`CWindowImpl::Create` crée une fenêtre basée sur les informations de classe de fenêtre gérées par [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` contient la macro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) , ce qui signifie `CWndClassInfo` inscrit une nouvelle classe de fenêtre. Si vous souhaitez superclasser une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et incluez la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . Dans ce cas, `CWndClassInfo` enregistre une classe de fenêtre basée sur une classe existante mais utilise `CWindowImpl::WindowProc`. Par exemple :

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  Étant donné que `CWndClassInfo` gère les informations d'une seule classe de fenêtre, chaque fenêtre créée via une instance de `CWindowImpl` est basée sur la même classe de fenêtre.

`CWindowImpl` prend également en charge le sous-classement de fenêtre. La méthode `SubclassWindow` attache une fenêtre existante à l'objet `CWindowImpl` et remplace la procédure de fenêtre par `CWindowImpl::WindowProc`. Chaque instance de `CWindowImpl` peut sous-classer une fenêtre différente.

> [!NOTE]
>  Pour tout objet `CWindowImpl` donné, appelez `Create` ou `SubclassWindow`. N'appelez pas les deux méthodes sur le même objet.

En plus de `CWindowImpl`, ATL fournit [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) pour créer une fenêtre contenue dans un autre objet.

Le destructeur de classe de base (~ `CWindowImplRoot`) garantit que la fenêtre est supprimée avant la destruction de l’objet.

`CWindowImpl` dérive de `CWindowImplBaseT`, qui dérive de `CWindowImplRoot`, qui dérive de `TBase` et [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Pour plus d’informations sur l’un des sujets suivants :|Consultez|
|--------------------------------|---------|
|Création de contrôles|[Tutoriel ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilisation de fenêtres dans ATL|[ATL, classes de fenêtre](../../atl/atl-window-classes.md)|
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="create"></a>CWindowImpl :: Create

Crée une fenêtre basée sur une nouvelle classe de fenêtre.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
dans Handle de la fenêtre parente ou propriétaire.

*rectangulaire*<br/>
dans Structure [Rect](/previous-versions/dd162897\(v=vs.85\)) spécifiant la position de la fenêtre. Le `RECT` peut être passé par pointeur ou par référence.

*szWindowName*<br/>
dans Spécifie le nom de la fenêtre. La valeur par défaut est NULL.

*dwStyle*<br/>
dans Style de la fenêtre. Cette valeur est combinée avec le style fourni par la classe de traits pour la fenêtre. La valeur par défaut donne un contrôle total à la classe de traits sur le style. Pour obtenir la liste des valeurs possibles, consultez [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le SDK Windows.

*dwExStyle*<br/>
dans Style de fenêtre étendu. Cette valeur est combinée avec le style fourni par la classe de traits pour la fenêtre. La valeur par défaut donne un contrôle total à la classe de traits sur le style. Pour obtenir la liste des valeurs possibles, consultez [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*MenuOrID*<br/>
dans Pour une fenêtre enfant, identificateur de fenêtre. Pour une fenêtre de niveau supérieur, un handle de menu pour la fenêtre. La valeur par défaut est **0U**.

*lpCreateParam*<br/>
dans Pointeur vers des données de création de fenêtre. Pour obtenir une description complète, consultez la description du paramètre final de [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Valeur de retour

En cas de réussite, handle vers la fenêtre nouvellement créée. Sinon, NULL.

### <a name="remarks"></a>Notes

`Create` inscrit d’abord la classe de fenêtre si elle n’a pas encore été inscrite. La fenêtre nouvellement créée est automatiquement attachée à l’objet `CWindowImpl`.

> [!NOTE]
>  N’appelez pas `Create` si vous avez déjà appelé [SubclassWindow](#subclasswindow).

Pour utiliser une classe de fenêtre qui est basée sur une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et incluez la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . La procédure de fenêtre de la classe de fenêtre existante est enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Pour plus d’informations, consultez la vue d’ensemble de [CWindowImpl](../../atl/reference/cwindowimpl-class.md) .

> [!NOTE]
>  Si 0 est utilisé comme valeur pour le paramètre *MenuOrID* , il doit être spécifié sous la forme de 0U (valeur par défaut) pour éviter une erreur du compilateur.

##  <a name="defwindowproc"></a>CWindowImpl ::D efWindowProc

Appelée par [WindowProc](#windowproc) pour traiter les messages non gérés par la table des messages.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Paramètres

*uMsg*<br/>
dans Message envoyé à la fenêtre.

*wParam*<br/>
dans Informations supplémentaires spécifiques au message.

*lParam*<br/>
dans Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur de retour

Résultat du traitement du message.

### <a name="remarks"></a>Notes

Par défaut, `DefWindowProc` appelle la fonction Win32 [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) pour envoyer les informations de message à la procédure de fenêtre spécifiée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

La fonction sans paramètres récupère automatiquement les paramètres nécessaires à partir du message actuel.

##  <a name="getcurrentmessage"></a>CWindowImpl :: GetCurrentMessage

Retourne le message en cours, empaqueté dans la structure `MSG`.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valeur de retour

Le message en cours.

##  <a name="getwindowproc"></a>CWindowImpl :: GetWindowProc

Retourne `WindowProc`, la procédure de fenêtre active.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Valeur de retour

Procédure de fenêtre active.

### <a name="remarks"></a>Notes

Substituez cette méthode pour remplacer la procédure de fenêtre par les vôtres.

##  <a name="getwndclassinfo"></a>CWindowImpl :: GetWndClassInfo

Appelée par [Create](#create) pour accéder aux informations de classe de fenêtre.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Valeur de retour

Instance statique de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Notes

Par défaut, `CWindowImpl` obtient cette méthode via la macro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) , qui spécifie une nouvelle classe de fenêtre.

Pour superclasser une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et incluez la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) pour remplacer `GetWndClassInfo`. Pour plus d’informations, consultez la vue d’ensemble de [CWindowImpl](../../atl/reference/cwindowimpl-class.md) .

Outre l’utilisation des macros DECLARE_WND_CLASS et DECLARE_WND_SUPERCLASS, vous pouvez remplacer `GetWndClassInfo` par votre propre implémentation.

##  <a name="m_pfnsuperwindowproc"></a>CWindowImpl :: m_pfnSuperWindowProc

En fonction de la fenêtre, pointe vers l’une des procédures de fenêtre suivantes.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Notes

|Type de fenêtre|Procédure de fenêtre|
|--------------------|----------------------|
|Fenêtre basée sur une nouvelle classe de fenêtre, spécifiée par le biais de la macro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) .|Fonction Win32 [DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) .|
|Fenêtre basée sur une classe de fenêtre qui modifie une classe existante, spécifiée à l’aide de la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) .|Procédure de fenêtre de la classe de fenêtre existante.|
|Fenêtre sous-classée.|Procédure de fenêtre d’origine de la fenêtre sous-classée.|

[CWindowImpl ::D efwindowproc](#defwindowproc) envoie les informations sur le message à la procédure de fenêtre enregistrée dans `m_pfnSuperWindowProc`.

##  <a name="onfinalmessage"></a>CWindowImpl :: OnFinalMessage

Appelé après la réception du dernier message (généralement WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
dans Handle de la fenêtre en cours de destruction.

### <a name="remarks"></a>Notes

L’implémentation par défaut de `OnFinalMessage` ne fait rien, mais vous pouvez remplacer cette fonction pour gérer le nettoyage avant de détruire une fenêtre. Si vous souhaitez supprimer automatiquement votre objet lors de la destruction de la fenêtre, vous pouvez appeler **Delete this ;** dans cette fonction.

##  <a name="subclasswindow"></a>CWindowImpl :: SubclassWindow

Sous-classe la fenêtre identifiée par *HWND* et l’attache à l’objet `CWindowImpl`.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
dans Handle de la fenêtre en cours de sous-classe.

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre est sous-classée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

La fenêtre sous-classée utilise désormais [CWindowImpl :: WindowProc](#windowproc). La procédure de fenêtre d’origine est enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  N’appelez pas `SubclassWindow` si vous avez déjà appelé [créer](#create).

##  <a name="unsubclasswindow"></a>CWindowImpl :: UnsubclassWindow

Détache la fenêtre sous-classée de l’objet `CWindowImpl` et restaure la procédure de fenêtre d’origine, enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Valeur de retour

Handle de la fenêtre sous-classé précédemment.

##  <a name="windowproc"></a>CWindowImpl :: WindowProc

Cette fonction statique implémente la procédure de fenêtre.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
dans Handle de la fenêtre.

*uMsg*<br/>
dans Message envoyé à la fenêtre.

*wParam*<br/>
dans Informations supplémentaires spécifiques au message.

*lParam*<br/>
dans Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur de retour

Résultat du traitement du message.

### <a name="remarks"></a>Notes

`WindowProc` utilise la table des messages par défaut (déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) pour diriger les messages vers les gestionnaires appropriés. Si nécessaire, `WindowProc` appelle [DefWindowProc](#defwindowproc) pour le traitement des messages supplémentaires. Si le dernier message n’est pas géré, `WindowProc` effectue les opérations suivantes :

- Exécute unsubclassing si la fenêtre a été unsubclassed.

- Efface `m_hWnd`.

- Appelle [OnFinalMessage](#onfinalmessage) avant la destruction de la fenêtre.

Vous pouvez substituer `WindowProc` pour fournir un mécanisme différent pour la gestion des messages.

## <a name="see-also"></a>Voir aussi

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

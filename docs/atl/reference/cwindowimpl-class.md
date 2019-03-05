---
title: CWindowImpl, classe
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::DefWindowProc
- ATLWIN/ATL::GetCurrentMessage
- ATLWIN/ATL::GetWindowProc
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::SubclassWindow
- ATLWIN/ATL::UnsubclassWindow
- ATLWIN/ATL::GetWndClassInfo
- ATLWIN/ATL::WindowProc
- ATLWIN/ATL::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: 2e4a9b585ed653927c87eaf82dfae8ce8f982dfc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290701"
---
# <a name="cwindowimpl-class"></a>CWindowImpl, classe

Fournit des méthodes pour créer ou sous-classer une fenêtre.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
Un [classe de traits](../../atl/understanding-window-traits.md) qui définit les styles de votre fenêtre. La valeur par défaut est `CControlWinTraits`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWindowImpl::Create](#create)|Crée une fenêtre.|

### <a name="cwindowimplbaset-methods"></a>Méthodes CWindowImplBaseT

|||
|-|-|
|[DefWindowProc](#defwindowproc)|Fournit le traitement du message par défaut.|
|[GetCurrentMessage](#getcurrentmessage)|Retourne le message actuel.|
|[GetWindowProc](#getwindowproc)|Retourne la procédure de fenêtre active.|
|[OnFinalMessage](#onfinalmessage)|Appelé après la dernière réception du message (généralement WM_NCDESTROY).|
|[SubclassWindow](#subclasswindow)|Sous-classe une fenêtre.|
|[UnsubclassWindow](#unsubclasswindow)|Restaure une fenêtre précédemment sous-classée.|

### <a name="static-methods"></a>Méthodes statiques

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|Retourne une instance statique de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), qui gère les informations de classe de fenêtre.|
|[WindowProc](#windowproc)|Traite les messages envoyés à la fenêtre.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Pointe vers la procédure de fenêtre d'origine de la classe de fenêtre.|

## <a name="remarks"></a>Notes

Vous pouvez utiliser `CWindowImpl` pour créer une fenêtre ou sous-classer une fenêtre existante. le `CWindowImpl` procédure de fenêtre utilise une table des messages pour diriger les messages vers les gestionnaires appropriés.

`CWindowImpl::Create` Crée une fenêtre basée sur les informations de classe de fenêtre qui sont gérées par [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` contient le [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) macro, ce qui signifie que `CWndClassInfo` inscrit une nouvelle classe de fenêtre. Si vous souhaitez surclasser une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et incluent la [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) (macro). Dans ce cas, `CWndClassInfo` enregistre une classe de fenêtre basée sur une classe existante mais utilise `CWindowImpl::WindowProc`. Exemple :

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  Étant donné que `CWndClassInfo` gère les informations d'une seule classe de fenêtre, chaque fenêtre créée via une instance de `CWindowImpl` est basée sur la même classe de fenêtre.

`CWindowImpl` prend également en charge le sous-classement de fenêtre. La méthode `SubclassWindow` attache une fenêtre existante à l'objet `CWindowImpl` et remplace la procédure de fenêtre par `CWindowImpl::WindowProc`. Chaque instance de `CWindowImpl` peut sous-classer une fenêtre différente.

> [!NOTE]
>  Pour tout `CWindowImpl` d’objet, appelez `Create` ou `SubclassWindow`. N'appelez pas les deux méthodes sur le même objet.

En plus de `CWindowImpl`, ATL fournit [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) pour créer une fenêtre qui est contenue dans un autre objet.

Le destructeur de classe de base (~ `CWindowImplRoot`) permet de s’assurer que la fenêtre a disparu avant la destruction de l’objet.

`CWindowImpl` dérive de `CWindowImplBaseT`, qui dérive à son `CWindowImplRoot`, qui dérive à son `TBase` et [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Pour plus d'informations sur|Voir|
|--------------------------------|---------|
|Création de contrôles|[Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilisation de fenêtres dans ATL|[ATL, classes de fenêtre](../../atl/atl-window-classes.md)|
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin.h

##  <a name="create"></a>  CWindowImpl::Create

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
[in] Le handle vers la fenêtre parente ou propriétaire.

*rect*<br/>
[in] Un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure spécifiant la position de la fenêtre. Le `RECT` peuvent être passés par pointeur ou par référence.

*szWindowName*<br/>
[in] Spécifie le nom de la fenêtre. La valeur par défaut est NULL.

*dwStyle*<br/>
[in] Le style de la fenêtre. Cette valeur est combinée avec le style fourni par la classe de traits pour la fenêtre. La valeur par défaut donne les caractéristiques de classe un contrôle total sur le style. Pour obtenir la liste des valeurs possibles, consultez [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) dans le SDK Windows.

*dwExStyle*<br/>
[in] Le style de fenêtre étendus. Cette valeur est combinée avec le style fourni par la classe de traits pour la fenêtre. La valeur par défaut donne les caractéristiques de classe un contrôle total sur le style. Pour obtenir la liste des valeurs possibles, consultez [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) dans le SDK Windows.

*MenuOrID*<br/>
[in] Pour une fenêtre enfant, l’identificateur de la fenêtre. Pour une fenêtre de niveau supérieur, un handle de menu de la fenêtre. La valeur par défaut est **0 u**.

*lpCreateParam*<br/>
[in] Pointeur vers les données de création de la fenêtre. Pour une description complète, consultez la description pour le paramètre final [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa).

### <a name="return-value"></a>Valeur de retour

En cas de réussite, le handle vers la fenêtre qui vient d’être créée. Sinon, NULL.

### <a name="remarks"></a>Notes

`Create` enregistre tout d’abord la classe de fenêtre si elle n’a pas encore été enregistré. La fenêtre qui vient d’être créée est automatiquement joint à la `CWindowImpl` objet.

> [!NOTE]
>  N’appelez pas `Create` si vous avez déjà appelé [SubclassWindow](#subclasswindow).

Pour utiliser une classe de fenêtre qui est basée sur une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et incluent la [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) (macro). Procédure de fenêtre de la classe de fenêtre existante est enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Pour plus d’informations, consultez le [CWindowImpl](../../atl/reference/cwindowimpl-class.md) vue d’ensemble.

> [!NOTE]
>  Si 0 est utilisé comme valeur pour le *MenuOrID* paramètre, il doit être spécifié en tant que 0 u (valeur par défaut) pour éviter une erreur du compilateur.

##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc

Appelé par [WindowProc](#windowproc) pour traiter les messages non gérées par la table des messages.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Paramètres

*uMsg*<br/>
[in] Le message est envoyé à la fenêtre.

*wParam*<br/>
[in] Informations supplémentaires spécifiques au message.

*lParam*<br/>
[in] Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur de retour

Le résultat du traitement du message.

### <a name="remarks"></a>Notes

Par défaut, `DefWindowProc` appelle le [CallWindowProc](/windows/desktop/api/winuser/nf-winuser-callwindowproca) Win32/fonction pour envoyer les informations de message à la procédure de fenêtre spécifiée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

La fonction sans aucun paramètre récupère automatiquement les paramètres nécessaires à partir du message actuel.

##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage

Retourne le message en cours, empaqueté dans le `MSG` structure.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valeur de retour

Le message en cours.

##  <a name="getwindowproc"></a>  CWindowImpl::GetWindowProc

Retourne `WindowProc`, la procédure de fenêtre actuelle.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Valeur de retour

La procédure de fenêtre actuelle.

### <a name="remarks"></a>Notes

Substituez cette méthode pour remplacer la procédure de fenêtre par les vôtres.

##  <a name="getwndclassinfo"></a>  CWindowImpl::GetWndClassInfo

Appelé par [créer](#create) pour accéder aux informations de classe de fenêtre.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Valeur de retour

Une instance statique de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Notes

Par défaut, `CWindowImpl` obtient cette méthode via la [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) macro, qui spécifie une nouvelle classe de fenêtre.

Pour surclasser une classe de fenêtre existante, dérivez votre classe de `CWindowImpl` et incluent la [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro pour remplacer `GetWndClassInfo`. Pour plus d’informations, consultez le [CWindowImpl](../../atl/reference/cwindowimpl-class.md) vue d’ensemble.

Outre l’utilisation des macros DECLARE_WND_CLASS et DECLARE_WND_SUPERCLASS, vous pouvez remplacer `GetWndClassInfo` par votre propre implémentation.

##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc

En fonction de la fenêtre, pointe vers une des procédures de fenêtre suivant.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Notes

|Type de fenêtre|Procédure de fenêtre|
|--------------------|----------------------|
|Une fenêtre basée sur une nouvelle classe de fenêtre spécifiée par le biais du [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) macro.|Le [DefWindowProc](/windows/desktop/api/winuser/nf-winuser-defwindowproca) fonction Win32.|
|Une fenêtre basée sur une classe de fenêtre qui modifie une classe existante, spécifiée par le biais du [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) (macro).|Procédure de fenêtre de la classe de fenêtre existante.|
|Une fenêtre sous-classé.|Procédure de fenêtre d’origine de la fenêtre sous-classé.|

[CWindowImpl::DefWindowProc](#defwindowproc) envoie message d’informations à la procédure de fenêtre enregistrée dans `m_pfnSuperWindowProc`.

##  <a name="onfinalmessage"></a>  CWindowImpl::OnFinalMessage

Appelé après réception du dernier message (généralement WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[in] Handle vers la fenêtre en cours de destruction.

### <a name="remarks"></a>Notes

L’implémentation par défaut de `OnFinalMessage` ne fait rien, mais vous pouvez remplacer cette fonction pour gérer le nettoyage avant de détruire une fenêtre. Si vous souhaitez supprimer automatiquement votre objet lors de la destruction de la fenêtre, vous pouvez appeler **supprimer cela ;** dans cette fonction.

##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow

Les sous-classes de la fenêtre est identifiée par *hWnd* et l’attache à la `CWindowImpl` objet.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[in] Le handle vers la fenêtre sous-classée.

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre est une sous-classe avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

La fenêtre sous-classé utilise désormais [CWindowImpl::WindowProc](#windowproc). La procédure de fenêtre d’origine est enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  N’appelez pas `SubclassWindow` si vous avez déjà appelé [créer](#create).

##  <a name="unsubclasswindow"></a>  CWindowImpl::UnsubclassWindow

Détache la fenêtre sous-classé à partir de la `CWindowImpl` de l’objet et restaure la procédure de fenêtre d’origine, enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Valeur de retour

Le handle vers la fenêtre précédemment sous-classée.

##  <a name="windowproc"></a>  CWindowImpl::WindowProc

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
[in] Handle vers la fenêtre.

*uMsg*<br/>
[in] Le message est envoyé à la fenêtre.

*wParam*<br/>
[in] Informations supplémentaires spécifiques au message.

*lParam*<br/>
[in] Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur de retour

Le résultat du traitement du message.

### <a name="remarks"></a>Notes

`WindowProc` utilise la table des messages par défaut (déclaré avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) pour diriger les messages vers les gestionnaires appropriés. Si nécessaire, `WindowProc` appels [DefWindowProc](#defwindowproc) pour le traitement des messages supplémentaires. Si le message final n’est pas géré, `WindowProc` effectue les opérations suivantes :

- Effectue unsubclassing si la fenêtre a été unsubclassed.

- Efface `m_hWnd`.

- Appels [OnFinalMessage](#onfinalmessage) avant la destruction de la fenêtre.

Vous pouvez remplacer `WindowProc` pour fournir un mécanisme différent pour la gestion des messages.

## <a name="see-also"></a>Voir aussi

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

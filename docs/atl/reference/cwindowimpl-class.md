---
title: Classe CWindowImpl
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
ms.openlocfilehash: ea150195f06d12cd6549b9026714d9e1bbf392df
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745995"
---
# <a name="cwindowimpl-class"></a>Classe CWindowImpl

Fournit des méthodes pour créer ou sous-classer une fenêtre.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre nouvelle classe, dérivée de `CWindowImpl`.

*TBase (TBase)*<br/>
Classe de base de votre classe. Par défaut, la classe de base est [CWindow](../../atl/reference/cwindow-class.md).

*TWinTraits*<br/>
Une [classe de traits](../../atl/understanding-window-traits.md) qui définit les styles pour votre fenêtre. Par défaut, il s’agit de `CControlWinTraits`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWindowImpl::Créer](#create)|Crée une fenêtre.|

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

Vous pouvez `CWindowImpl` utiliser pour créer une fenêtre ou sous-classer une fenêtre existante. la `CWindowImpl` procédure de fenêtre utilise une carte de message pour diriger les messages vers les gestionnaires appropriés.

`CWindowImpl::Create`crée une fenêtre basée sur les informations de classe de fenêtre qui est gérée par [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl`contient la [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) macro, ce `CWndClassInfo` qui signifie enregistre une nouvelle classe de fenêtre. Si vous voulez superclasser une classe de `CWindowImpl` fenêtre existante, dérivez votre classe et incluez la [macro DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass) Dans ce cas, `CWndClassInfo` enregistre une classe de fenêtre basée sur une classe existante mais utilise `CWindowImpl::WindowProc`. Par exemple :

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> Étant donné que `CWndClassInfo` gère les informations d'une seule classe de fenêtre, chaque fenêtre créée via une instance de `CWindowImpl` est basée sur la même classe de fenêtre.

`CWindowImpl` prend également en charge le sous-classement de fenêtre. La méthode `SubclassWindow` attache une fenêtre existante à l'objet `CWindowImpl` et remplace la procédure de fenêtre par `CWindowImpl::WindowProc`. Chaque instance de `CWindowImpl` peut sous-classer une fenêtre différente.

> [!NOTE]
> Pour tout `CWindowImpl` objet donné, appelez l’un ou l’autre `Create` ou `SubclassWindow`. N'appelez pas les deux méthodes sur le même objet.

En plus `CWindowImpl`de , ATL fournit [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) pour créer une fenêtre qui est contenue dans un autre objet.

Le destructeur de `CWindowImplRoot`classe de base (md) garantit que la fenêtre est partie avant que l’objet ne soit détruit.

`CWindowImpl`dérive de `CWindowImplBaseT`, qui `CWindowImplRoot`dérive de , `TBase` qui dérive de et [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Pour plus d’informations sur l’un des sujets suivants :|Consultez|
|--------------------------------|---------|
|Création de contrôles|[Tutoriel ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilisation de fenêtres dans ATL|[Cours de fenêtre ATL](../../atl/atl-window-classes.md)|
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="cwindowimplcreate"></a><a name="create"></a>CWindowImpl::Créer

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
[dans] La poignée à la fenêtre du parent ou du propriétaire.

*Rect*<br/>
[dans] Une structure [RECT](/windows/win32/api/windef/ns-windef-rect) spécifiant la position de la fenêtre. Le `RECT` peut être passé par pointeur ou par référence.

*szWindowName*<br/>
[dans] Précise le nom de la fenêtre. La valeur par défaut est NULL.

*dwStyle (en)*<br/>
[dans] Le style de la fenêtre. Cette valeur est combinée avec le style fourni par la classe de traits pour la fenêtre. La valeur par défaut donne aux traits classe plein contrôle sur le style. Pour une liste de valeurs possibles, voir [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le SDK Windows.

*dwExStyle (en anglais)*<br/>
[dans] Le style de fenêtre étendue. Cette valeur est combinée avec le style fourni par la classe de traits pour la fenêtre. La valeur par défaut donne aux traits classe plein contrôle sur le style. Pour une liste de valeurs possibles, voir [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*MenuOrID*<br/>
[dans] Pour une fenêtre pour enfant, l’identifiant de fenêtre. Pour une fenêtre de haut niveau, une poignée de menu pour la fenêtre. La valeur par défaut est **0U**.

*lpCreateParam*<br/>
[dans] Un pointeur aux données de création de fenêtres. Pour une description complète, voir la description du paramètre final de [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Valeur de retour

En cas de succès, le manche à la fenêtre nouvellement créée. Sinon, NULL.

### <a name="remarks"></a>Notes

`Create`enregistre d’abord la classe de fenêtre si elle n’a pas encore été enregistrée. La fenêtre nouvellement créée `CWindowImpl` est automatiquement fixée à l’objet.

> [!NOTE]
> N’appelez `Create` pas si vous avez déjà appelé [SubclassWindow](#subclasswindow).

Pour utiliser une classe de fenêtre qui est basée `CWindowImpl` sur une classe de fenêtre existante, dérivez votre classe et incluez la [macro DECLARE_WND_SUPERCLASS.](window-class-macros.md#declare_wnd_superclass) La procédure de fenêtre de la classe de fenêtre existante est enregistrée en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Pour plus d’informations, consultez la vue d’ensemble [de CWindowImpl.](../../atl/reference/cwindowimpl-class.md)

> [!NOTE]
> Si 0 est utilisé comme valeur pour le paramètre *MenuOrID,* il doit être spécifié comme 0U (la valeur par défaut) pour éviter une erreur de compilateur.

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a>CWindowImpl::DefWindowProc

Appelé par [WindowProc](#windowproc) pour traiter les messages non traités par la carte de message.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Paramètres

*uMsg*<br/>
[dans] Le message envoyé à la fenêtre.

*wParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

*lParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur de retour

Le résultat du traitement du message.

### <a name="remarks"></a>Notes

Par défaut, `DefWindowProc` appelez la fonction [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 pour envoyer les informations de message à la procédure de fenêtre spécifiée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

La fonction sans paramètres récupère automatiquement les paramètres nécessaires du message actuel.

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a>CWindowImpl::GetCurrentMessage

Retourne le message actuel, `MSG` emballé dans la structure.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valeur de retour

Le message en cours.

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a>CWindowImpl::GetWindowProc

Retours `WindowProc`, la procédure de fenêtre actuelle.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Valeur de retour

La procédure de fenêtre actuelle.

### <a name="remarks"></a>Notes

Remplacez cette méthode pour remplacer la procédure de fenêtre par la vôtre.

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a>CWindowImpl::GetWndClassInfo

Appelé par [Create](#create) pour accéder à l’information de classe de fenêtre.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Valeur de retour

Une instance statique de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Notes

Par défaut, `CWindowImpl` obtient cette méthode à travers la [macro DECLARE_WND_CLASS,](window-class-macros.md#declare_wnd_class) qui spécifie une nouvelle classe de fenêtre.

Pour superclasser une classe de `CWindowImpl` fenêtre existante, dérivez votre classe et incluez la macro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) pour l’emporter. `GetWndClassInfo` Pour plus d’informations, consultez la vue d’ensemble [de CWindowImpl.](../../atl/reference/cwindowimpl-class.md)

En plus d’utiliser les macros DECLARE_WND_CLASS et `GetWndClassInfo` DECLARE_WND_SUPERCLASS, vous pouvez passer outre à votre propre implémentation.

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CWindowImpl::m_pfnSuperWindowProc

Selon la fenêtre, indique l’une des procédures de fenêtre suivantes.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Notes

|Type de fenêtre|Procédure de fenêtre|
|--------------------|----------------------|
|Une fenêtre basée sur une nouvelle classe de fenêtre, spécifiée à travers la macro [DECLARE_WND_CLASS.](window-class-macros.md#declare_wnd_class)|La fonction [DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32.|
|Une fenêtre basée sur une classe de fenêtre qui modifie une classe existante, spécifiée par le [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro.|Procédure de fenêtre de la classe de fenêtre existante.|
|Une fenêtre sous-classée.|Procédure de fenêtre originale de la fenêtre sous-classée.|

[CWindowImpl::DefWindowProc](#defwindowproc) envoie des informations de message `m_pfnSuperWindowProc`à la procédure de fenêtre enregistrée dans .

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a>CWindowImpl::OnFinalMessage

Appelé après avoir reçu le dernier message (généralement WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[dans] Une poignée à la fenêtre détruite.

### <a name="remarks"></a>Notes

La mise `OnFinalMessage` en œuvre par défaut de ne fait rien, mais vous pouvez remplacer cette fonction pour gérer le nettoyage avant de détruire une fenêtre. Si vous souhaitez supprimer automatiquement votre objet lors de la destruction de la fenêtre, vous pouvez appeler **supprimer ceci;** dans cette fonction.

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a>CWindowImpl::SubclassWindow

Sous-classe la fenêtre identifiée par *hWnd* `CWindowImpl` et la fixe à l’objet.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[dans] La poignée à la fenêtre étant sous-classée.

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre est sous-classée avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

La fenêtre sous-classée utilise maintenant [CWindowImpl::WindowProc](#windowproc). La procédure de fenêtre d’origine est enregistrée en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> N’appelez `SubclassWindow` pas si vous avez déjà appelé [Create](#create).

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a>CWindowImpl::UnsubclassWindow

Détache la fenêtre sous-classée `CWindowImpl` de l’objet et restaure la procédure de fenêtre d’origine, enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Valeur de retour

La poignée à la fenêtre précédemment sous-classée.

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a>CWindowImpl::WindowProc

Cette fonction statique met en œuvre la procédure de fenêtre.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[dans] La poignée à la fenêtre.

*uMsg*<br/>
[dans] Le message envoyé à la fenêtre.

*wParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

*lParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur de retour

Le résultat du traitement du message.

### <a name="remarks"></a>Notes

`WindowProc`utilise la carte des messages par défaut (déclarée avec [BEGIN_MSG_MAP)](message-map-macros-atl.md#begin_msg_map)pour adresser des messages aux gestionnaires appropriés. Si nécessaire, `WindowProc` appelle [DefWindowProc](#defwindowproc) pour un traitement de messages supplémentaires. Si le message final n’est pas traité, `WindowProc` fait ce qui suit :

- Effectue un désabonnement si la fenêtre n’était pas sous-classée.

- Efface `m_hWnd`.

- Appels [SurFinalMessage](#onfinalmessage) avant que la fenêtre soit détruite.

Vous pouvez `WindowProc` remplacer pour fournir un mécanisme différent pour le traitement des messages.

## <a name="see-also"></a>Voir aussi

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

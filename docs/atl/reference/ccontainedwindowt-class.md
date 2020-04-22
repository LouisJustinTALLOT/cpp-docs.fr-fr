---
title: Classe CContainedWindowT
ms.date: 11/04/2016
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
ms.openlocfilehash: 7b89346bbc62cdda808b193a199fdf121f052ebb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747748"
---
# <a name="ccontainedwindowt-class"></a>Classe CContainedWindowT

Cette classe implémente une fenêtre contenue dans un autre objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Paramètres

*TBase (TBase)*<br/>
La classe de base de votre nouvelle classe. La classe de `CWindow`base par défaut est .

*TWinTraits*<br/>
Classe de traits qui définit des styles pour votre fenêtre. Par défaut, il s’agit de `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) est une `CContainedWindowT`spécialisation de . Si vous voulez changer la classe de `CContainedWindowT` base ou les traits, utilisez directement.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CContainedWindowt::CContainedWindowt](#ccontainedwindowt)|Constructeur. Initialise les membres des données pour spécifier quelle carte de message traitera les messages contenus de la fenêtre.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CContainedWindowT::Créer](#create)|Crée une fenêtre.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Fournit le traitement du message par défaut.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Retourne le message actuel.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Enregistre la classe de fenêtre de la fenêtre contenue.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Sous-classe une fenêtre.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Modifie la carte des messages utilisée pour traiter les messages contenus de la fenêtre.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Restaure une fenêtre précédemment sous-classée.|
|[CContainedWindowT::WindowProc](#windowproc)|(Statique) Traite les messages envoyés à la fenêtre contenue.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Identifie la carte de message qui traitera les messages de la fenêtre contenue.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Précise le nom d’une classe de fenêtre existante sur laquelle une nouvelle classe de fenêtre sera basée.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Pointe vers la procédure de fenêtre d'origine de la classe de fenêtre.|
|[CContainedWindowT::m_pObject](#m_pobject)|Points à l’objet contenant.|

## <a name="remarks"></a>Notes

`CContainedWindowT`implémente une fenêtre contenue dans un autre objet. `CContainedWindowT`la procédure de fenêtre utilise une carte de message dans l’objet contenant pour diriger les messages vers les gestionnaires appropriés. Lors de `CContainedWindowT` la construction d’un objet, vous spécifiez quelle carte de message doit être utilisée.

`CContainedWindowT`vous permet de créer une nouvelle fenêtre en superclassant une classe de fenêtre existante. La `Create` méthode enregistre d’abord une classe de fenêtre `CContainedWindowT::WindowProc`qui est basée sur une classe existante, mais utilise . `Create`crée alors une fenêtre basée sur cette nouvelle classe de fenêtre. Chaque instance `CContainedWindowT` de peut superclasser une classe de fenêtre différente.

`CContainedWindowT` prend également en charge le sous-classement de fenêtre. La méthode `SubclassWindow` attache une fenêtre existante à l'objet `CContainedWindowT` et remplace la procédure de fenêtre par `CContainedWindowT::WindowProc`. Chaque instance de `CContainedWindowT` peut sous-classer une fenêtre différente.

> [!NOTE]
> Pour tout `CContainedWindowT` objet donné, appelez l’un ou l’autre `Create` ou `SubclassWindow`. Vous ne devez pas invoquer les deux méthodes sur le même objet.

Lorsque vous utilisez le **contrôle Add basé sur l’option** dans `CContainedWindowT` l’assistant de projet ATL, l’assistant ajoutera automatiquement un membre de données à la classe implémentant le contrôle. L’exemple suivant montre comment la fenêtre contenue est déclarée :

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Pour plus d’informations sur l’un des sujets suivants :|Consultez|
|--------------------------------|---------|
|Création de contrôles|[Tutoriel ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilisation de fenêtres dans ATL|[Cours de fenêtre ATL](../../atl/atl-window-classes.md)|
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/win32/winmsg/windows) et les sujets suivants dans le Windows SDK|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a>CContainedWindowt::CContainedWindowt

Le constructeur initialise les membres des données.

```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```

### <a name="parameters"></a>Paramètres

*lpszClassName (en)*<br/>
[dans] Le nom d’une classe de fenêtre existante sur laquelle la fenêtre contenue sera basée.

*pObject*<br/>
[dans] Un pointeur vers l’objet contenant qui déclare la carte de message. La classe de cet objet doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[dans] Identifie la carte de message qui traitera les messages de la fenêtre contenue. La valeur par défaut, 0, spécifie la carte de message par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Pour utiliser une carte de message alternative déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), passez `msgMapID`.

### <a name="remarks"></a>Notes

Si vous souhaitez créer une nouvelle fenêtre par [l’intermédiaire de Create](#create), vous devez passer le nom d’une classe de fenêtre existante pour le paramètre *lpszClassName.* Par exemple, voir la vue [d’ensemble CContainedWindow.](../../atl/reference/ccontainedwindowt-class.md)

Il y a trois constructeurs :

- Le constructeur avec trois arguments est celui généralement appelé.

- Le constructeur avec deux arguments utilise `TBase::GetWndClassName`le nom de classe de .

- Le constructeur sans arguments est utilisé si vous voulez fournir les arguments plus tard. Vous devez fournir le nom de la classe de fenêtre, `Create`l’objet de carte de message, et l’ID de carte de message lorsque vous appelez plus tard .

Si vous sous-classez une fenêtre existante par [SubclassWindow](#subclasswindow), la valeur *lpszClassName* ne sera pas utilisée; par conséquent, vous pouvez passer NULL pour ce paramètre.

## <a name="ccontainedwindowtcreate"></a><a name="create"></a>CContainedWindowT::Créer

Appels [RegisterWndSuperclass](#registerwndsuperclass) pour enregistrer une classe de fenêtre qui est basée sur une classe existante, mais utilise [CContainedWindowT::WindowProc](#windowproc).

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszClassName (en)*<br/>
[dans] Le nom d’une classe de fenêtre existante sur laquelle la fenêtre contenue sera basée.

*pObject*<br/>
[dans] Un pointeur vers l’objet contenant qui déclare la carte de message. La classe de cet objet doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[dans] Identifie la carte de message qui traitera les messages de la fenêtre contenue. La valeur par défaut, 0, spécifie la carte de message par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Pour utiliser une carte de message alternative déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), passez `msgMapID`.

*hWndParent*<br/>
[dans] La poignée à la fenêtre du parent ou du propriétaire.

*Rect*<br/>
[dans] Une structure [RECT](/windows/win32/api/windef/ns-windef-rect) spécifiant la position de la fenêtre. Le `RECT` peut être passé par pointeur ou par référence.

*szWindowName*<br/>
[dans] Précise le nom de la fenêtre. La valeur par défaut est NULL.

*dwStyle (en)*<br/>
[dans] Le style de la fenêtre. La valeur par défaut est WS_CHILD WS_VISIBLE &#124;. Pour une liste de valeurs possibles, voir [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le SDK Windows.

*dwExStyle (en anglais)*<br/>
[dans] Le style de fenêtre étendue. La valeur par défaut est de 0, ce qui signifie qu’aucun style étendu. Pour une liste de valeurs possibles, voir [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*MenuOrID*<br/>
[dans] Pour une fenêtre pour enfant, l’identifiant de fenêtre. Pour une fenêtre de haut niveau, une poignée de menu pour la fenêtre. La valeur par défaut est **0U**.

*lpCreateParam*<br/>
[dans] Un pointeur aux données de création de fenêtres. Pour une description complète, voir la description du paramètre final de [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Valeur de retour

En cas de succès, la poignée de la fenêtre nouvellement créée; autrement, NULL.

### <a name="remarks"></a>Notes

Le nom de classe de fenêtre existant est enregistré dans [m_lpszClassName](#m_lpszclassname). `Create`crée alors une fenêtre basée sur cette nouvelle classe. La fenêtre nouvellement créée `CContainedWindowT` est automatiquement fixée à l’objet.

> [!NOTE]
> N’appelez `Create` pas si vous avez déjà appelé [SubclassWindow](#subclasswindow).

> [!NOTE]
> Si 0 est utilisé comme valeur pour le paramètre *MenuOrID,* il doit être spécifié comme 0U (la valeur par défaut) pour éviter une erreur de compilateur.

## <a name="ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a>CContainedWindowT::DefWindowProc

Appelé par [WindowProc](#windowproc) pour traiter les messages non traités par la carte de message.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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

## <a name="ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage

Retourne le message`m_pCurrentMsg`actuel ( ).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valeur de retour

Le message actuel, emballé `MSG` dans la structure.

## <a name="ccontainedwindowtm_dwmsgmapid"></a><a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID

Tient l’identifiant de la carte de message actuellement utilisée pour la fenêtre contenue.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Notes

Cette carte de message doit être déclarée dans l’objet contenant.

La carte de message par défaut, déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), est toujours identifiée par zéro. Une carte de message alternative, déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), est identifiée par `msgMapID`.

`m_dwMsgMapID`est d’abord parascé par le constructeur et peut être changé en appelant [SwitchMessageMap](#switchmessagemap). Par exemple, voir le [aperçu CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md).

## <a name="ccontainedwindowtm_lpszclassname"></a><a name="m_lpszclassname"></a>CContainedWindowT::m_lpszClassName

Spécifie le nom d’une classe de fenêtre existante.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Notes

Lorsque vous créez une fenêtre, [Create](#create) enregistre une nouvelle classe de fenêtre qui est basée sur cette classe existante, mais utilise [CContainedWindowT::WindowProc](#windowproc).

`m_lpszClassName`est parascé par le constructeur. Par exemple, voir la vue [d’ensemble CContainedWindowT.](../../atl/reference/ccontainedwindowt-class.md)

## <a name="ccontainedwindowtm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CContainedWindowT::m_pfnSuperWindowProc

Si la fenêtre contenue est `m_pfnSuperWindowProc` sous-classée, indique la procédure de fenêtre originale de la classe de fenêtre.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Notes

Si la fenêtre contenue est surclassée, ce qui signifie qu’elle `m_pfnSuperWindowProc` est basée sur une classe de fenêtre qui modifie une classe existante, indique la procédure de fenêtre de la classe de fenêtre existante.

La méthode [DefWindowProc](#defwindowproc) envoie des informations `m_pfnSuperWindowProc`de message à la procédure de fenêtre enregistrée dans .

## <a name="ccontainedwindowtm_pobject"></a><a name="m_pobject"></a>CContainedWindowT::m_pObject

Points à l’objet contenant l’objet. `CContainedWindowT`

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Notes

Ce conteneur, dont la classe doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md), déclare la carte de message utilisée par la fenêtre contenue.

`m_pObject`est parascé par le constructeur. Par exemple, voir la vue [d’ensemble CContainedWindowT.](../../atl/reference/ccontainedwindowt-class.md)

## <a name="ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass

Appelé par [Create](#create) pour enregistrer la classe de fenêtre de la fenêtre contenue.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, un atome qui identifie uniquement la classe de fenêtre étant enregistrée; autrement, zéro.

### <a name="remarks"></a>Notes

Cette classe de fenêtre est basée sur une classe existante, mais utilise [CContainedWindowT::WindowProc](#windowproc). Le nom et la procédure de fenêtre de la classe de fenêtre existante sont enregistrés dans [m_lpszClassName](#m_lpszclassname) et [m_pfnSuperWindowProc,](#m_pfnsuperwindowproc)respectivement.

## <a name="ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a>CContainedWindowT::SubclassWindow

Sous-classe la fenêtre identifiée par *hWnd* `CContainedWindowT` et la fixe à l’objet.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[dans] La poignée à la fenêtre étant sous-classée.

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre est sous-classée avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

La fenêtre sous-classée utilise maintenant [CContainedWindowT::WindowProc](#windowproc). La procédure de fenêtre d’origine est enregistrée en [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> N’appelez `SubclassWindow` pas si vous avez déjà appelé [Create](#create).

## <a name="ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap

Modifie la carte des messages pour traiter les messages contenus de la fenêtre.

```cpp
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Paramètres

*dwMsgMapID*<br/>
[dans] L’identifiant de carte de message. Pour utiliser la carte de message par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), passez zéro. Pour utiliser une carte de message alternative déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), passez `msgMapID`.

### <a name="remarks"></a>Notes

La carte de message doit être définie dans l’objet contenant.

Vous spécifiez d’abord l’identifiant de carte de message dans le constructeur.

## <a name="ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow

Détache la fenêtre sous-classée `CContainedWindowT` de l’objet et restaure la procédure de fenêtre d’origine, enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Paramètres

*bForce (en)*<br/>
[dans] Définissez à TRUE pour forcer la procédure de fenêtre `CContainedWindowT` originale à être restaurée même si la procédure de fenêtre de cet objet n’est pas actuellement active. Si *bForce* est réglé sur FALSE `CContainedWindowT` et que la procédure de fenêtre de cet objet n’est pas actuellement active, la procédure de fenêtre d’origine ne sera pas restaurée.

### <a name="return-value"></a>Valeur de retour

La poignée à la fenêtre précédemment sous-classée. Si *bForce* est réglé sur FALSE `CContainedWindowT` et que la procédure de fenêtre de cet objet n’est pas actuellement active, retourne NULL.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement si vous souhaitez restaurer la procédure de fenêtre d’origine avant que la fenêtre ne soit détruite. Sinon, [WindowProc](#windowproc) le fera automatiquement lorsque la fenêtre sera détruite.

## <a name="ccontainedwindowtwindowproc"></a><a name="windowproc"></a>CContainedWindowT::WindowProc

Cette méthode statique met en œuvre la procédure de fenêtre.

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

`WindowProc`dirige les messages vers la carte de message identifiée par [m_dwMsgMapID](#m_dwmsgmapid). Si nécessaire, `WindowProc` appelle [DefWindowProc](#defwindowproc) pour un traitement de messages supplémentaires.

## <a name="see-also"></a>Voir aussi

[Classe CWindow](../../atl/reference/cwindow-class.md)<br/>
[Classe CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Classe CMessageMap](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

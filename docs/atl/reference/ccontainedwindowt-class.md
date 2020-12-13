---
description: 'En savoir plus sur : classe CContainedWindowT'
title: CContainedWindowT, classe
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
ms.openlocfilehash: 68135ec6d8dc43623ec2a827bbe075e24eef8d42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142075"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT, classe

Cette classe implémente une fenêtre contenue dans un autre objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Paramètres

*TBase*<br/>
Classe de base de votre nouvelle classe. La classe de base par défaut est `CWindow` .

*TWinTraits*<br/>
Classe de traits qui définit des styles pour votre fenêtre. Par défaut, il s’agit de `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) est une spécialisation de `CContainedWindowT` . Si vous souhaitez modifier la classe de base ou les traits, utilisez `CContainedWindowT` directement.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Constructeur. Initialise des membres de données pour spécifier la table des messages qui traitera les messages de la fenêtre contenue.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CContainedWindowT :: Create](#create)|Crée une fenêtre.|
|[CContainedWindowT ::D efWindowProc](#defwindowproc)|Fournit le traitement du message par défaut.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Retourne le message actuel.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Inscrit la classe de fenêtre de la fenêtre contenue.|
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Sous-classe une fenêtre.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Modifie la table des messages utilisée pour traiter les messages de la fenêtre contenue.|
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Restaure une fenêtre précédemment sous-classée.|
|[CContainedWindowT :: WindowProc](#windowproc)|Statique Traite les messages envoyés à la fenêtre contenue.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CContainedWindowT :: m_dwMsgMapID](#m_dwmsgmapid)|Identifie la table des messages qui traitera les messages de la fenêtre contenue.|
|[CContainedWindowT :: m_lpszClassName](#m_lpszclassname)|Spécifie le nom d’une classe de fenêtre existante sur laquelle sera basée une nouvelle classe de fenêtre.|
|[CContainedWindowT :: m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Pointe vers la procédure de fenêtre d'origine de la classe de fenêtre.|
|[CContainedWindowT :: m_pObject](#m_pobject)|Pointe vers l’objet conteneur.|

## <a name="remarks"></a>Notes

`CContainedWindowT` implémente une fenêtre contenue dans un autre objet. `CContainedWindowT`la procédure de fenêtre de utilise une table des messages dans l’objet conteneur pour diriger les messages vers les gestionnaires appropriés. Lors de la construction d’un `CContainedWindowT` objet, vous spécifiez la table des messages à utiliser.

`CContainedWindowT` vous permet de créer une nouvelle fenêtre en superclassant une classe de fenêtre existante. La `Create` méthode enregistre tout d’abord une classe de fenêtre qui est basée sur une classe existante, mais utilise `CContainedWindowT::WindowProc` . `Create` crée ensuite une fenêtre basée sur cette nouvelle classe de fenêtre. Chaque instance de `CContainedWindowT` peut superclasser une classe de fenêtre différente.

`CContainedWindowT` prend également en charge le sous-classement de fenêtre. La méthode `SubclassWindow` attache une fenêtre existante à l'objet `CContainedWindowT` et remplace la procédure de fenêtre par `CContainedWindowT::WindowProc`. Chaque instance de `CContainedWindowT` peut sous-classer une fenêtre différente.

> [!NOTE]
> Pour tout `CContainedWindowT` objet donné, appelez `Create` ou `SubclassWindow` . Vous ne devez pas appeler les deux méthodes sur le même objet.

Lorsque vous utilisez l’option **Ajouter un contrôle basé sur** dans l’Assistant Projet ATL, l’Assistant ajoute automatiquement un `CContainedWindowT` membre de données à la classe qui implémente le contrôle. L’exemple suivant montre comment la fenêtre contenue est déclarée :

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Pour plus d’informations sur l’un des sujets suivants :|Consultez|
|--------------------------------|---------|
|Création de contrôles|[Tutoriel ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilisation de fenêtres dans ATL|[Classes de fenêtre ATL](../../atl/atl-window-classes.md)|
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/win32/winmsg/windows) et les rubriques suivantes de la SDK Windows|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a> CContainedWindowT::CContainedWindowT

Le constructeur initialise les membres de données.

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

*lpszClassName*<br/>
dans Nom d’une classe de fenêtre existante sur laquelle la fenêtre contenue sera basée.

*pObject*<br/>
dans Pointeur vers l’objet conteneur qui déclare la table des messages. La classe de cet objet doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
dans Identifie la table des messages qui traitera les messages de la fenêtre contenue. La valeur par défaut, 0, spécifie la table des messages par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Pour utiliser une autre table des messages déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), transmettez `msgMapID` .

### <a name="remarks"></a>Notes

Si vous souhaitez créer une nouvelle fenêtre par le biais de [Create](#create), vous devez passer le nom d’une classe de fenêtre existante pour le paramètre *lpszClassName* . Pour obtenir un exemple, consultez la vue d’ensemble de [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) .

Il existe trois constructeurs :

- Le constructeur avec trois arguments est celui généralement appelé.

- Le constructeur avec deux arguments utilise le nom de la classe à partir de `TBase::GetWndClassName` .

- Le constructeur sans argument est utilisé si vous souhaitez fournir les arguments ultérieurement. Vous devez fournir le nom de la classe de fenêtre, l’objet de la table des messages et l’ID de la table des messages lorsque vous appelez ultérieurement `Create` .

Si vous sous-classez une fenêtre existante par le biais de [SubclassWindow](#subclasswindow), la valeur *lpszClassName* ne sera pas utilisée. par conséquent, vous pouvez passer la valeur NULL pour ce paramètre.

## <a name="ccontainedwindowtcreate"></a><a name="create"></a> CContainedWindowT :: Create

Appelle [RegisterWndSuperclass](#registerwndsuperclass) pour inscrire une classe de fenêtre qui est basée sur une classe existante, mais utilise [CContainedWindowT :: WindowProc](#windowproc).

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

*lpszClassName*<br/>
dans Nom d’une classe de fenêtre existante sur laquelle la fenêtre contenue sera basée.

*pObject*<br/>
dans Pointeur vers l’objet conteneur qui déclare la table des messages. La classe de cet objet doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
dans Identifie la table des messages qui traitera les messages de la fenêtre contenue. La valeur par défaut, 0, spécifie la table des messages par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Pour utiliser une autre table des messages déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), transmettez `msgMapID` .

*hWndParent*<br/>
dans Handle de la fenêtre parente ou propriétaire.

*rectangulaire*<br/>
dans Structure [Rect](/windows/win32/api/windef/ns-windef-rect) spécifiant la position de la fenêtre. `RECT`Peut être passé par pointeur ou par référence.

*szWindowName*<br/>
dans Spécifie le nom de la fenêtre. La valeur par défaut est NULL.

*dwStyle*<br/>
dans Style de la fenêtre. La valeur par défaut est WS_CHILD &#124; WS_VISIBLE. Pour obtenir la liste des valeurs possibles, consultez [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le SDK Windows.

*dwExStyle*<br/>
dans Style de fenêtre étendu. La valeur par défaut est 0, ce qui signifie qu’il n’y a pas de style étendu. Pour obtenir la liste des valeurs possibles, consultez [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*MenuOrID*<br/>
dans Pour une fenêtre enfant, identificateur de fenêtre. Pour une fenêtre de niveau supérieur, un handle de menu pour la fenêtre. La valeur par défaut est **0U**.

*lpCreateParam*<br/>
dans Pointeur vers des données de création de fenêtre. Pour obtenir une description complète, consultez la description du paramètre final de [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, handle vers la fenêtre nouvellement créée ; Sinon, NULL.

### <a name="remarks"></a>Notes

Le nom de la classe de fenêtre existante est enregistré dans [m_lpszClassName](#m_lpszclassname). `Create` crée ensuite une fenêtre basée sur cette nouvelle classe. La fenêtre nouvellement créée est automatiquement attachée à l' `CContainedWindowT` objet.

> [!NOTE]
> N’appelez pas `Create` si vous avez déjà appelé [SubclassWindow](#subclasswindow).

> [!NOTE]
> Si 0 est utilisé comme valeur pour le paramètre *MenuOrID* , il doit être spécifié sous la forme de 0U (valeur par défaut) pour éviter une erreur du compilateur.

## <a name="ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a> CContainedWindowT ::D efWindowProc

Appelée par [WindowProc](#windowproc) pour traiter les messages non gérés par la table des messages.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*uMsg*<br/>
dans Message envoyé à la fenêtre.

*wParam*<br/>
dans Informations supplémentaires spécifiques au message.

*lParam*<br/>
dans Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur renvoyée

Résultat du traitement du message.

### <a name="remarks"></a>Notes

Par défaut, `DefWindowProc` appelle la fonction Win32 [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) pour envoyer les informations de message à la procédure de fenêtre spécifiée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

## <a name="ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a> CContainedWindowT::GetCurrentMessage

Retourne le message en cours ( `m_pCurrentMsg` ).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Valeur renvoyée

Message en cours, empaqueté dans la `MSG` structure.

## <a name="ccontainedwindowtm_dwmsgmapid"></a><a name="m_dwmsgmapid"></a> CContainedWindowT :: m_dwMsgMapID

Contient l’identificateur de la table des messages actuellement utilisée pour la fenêtre contenue.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Notes

Cette table des messages doit être déclarée dans l’objet conteneur.

La table des messages par défaut, déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), est toujours identifiée par zéro. Une autre table des messages, déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), est identifiée par `msgMapID` .

`m_dwMsgMapID` est d’abord initialisé par le constructeur et peut être modifié en appelant [SwitchMessageMap](#switchmessagemap). Pour obtenir un exemple, consultez la [vue d’ensemble de CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md).

## <a name="ccontainedwindowtm_lpszclassname"></a><a name="m_lpszclassname"></a> CContainedWindowT :: m_lpszClassName

Spécifie le nom d’une classe de fenêtre existante.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Notes

Quand vous créez une fenêtre, [créer](#create) inscrit une nouvelle classe de fenêtre qui est basée sur cette classe existante, mais utilise [CContainedWindowT :: WindowProc](#windowproc).

`m_lpszClassName` est initialisé par le constructeur. Pour obtenir un exemple, consultez la vue d’ensemble de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) .

## <a name="ccontainedwindowtm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a> CContainedWindowT :: m_pfnSuperWindowProc

Si la fenêtre contenue est sous-classée, `m_pfnSuperWindowProc` pointe vers la procédure de fenêtre d’origine de la classe de fenêtre.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Notes

Si la fenêtre contenue est superclassée, ce qui signifie qu’elle est basée sur une classe de fenêtre qui modifie une classe existante, `m_pfnSuperWindowProc` pointe vers la procédure de fenêtre de la classe de fenêtre existante.

La méthode [DefWindowProc](#defwindowproc) envoie les informations sur le message à la procédure de fenêtre enregistrée dans `m_pfnSuperWindowProc` .

## <a name="ccontainedwindowtm_pobject"></a><a name="m_pobject"></a> CContainedWindowT :: m_pObject

Pointe vers l’objet qui contient l' `CContainedWindowT` objet.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Notes

Ce conteneur, dont la classe doit dériver de [CMessageMap](../../atl/reference/cmessagemap-class.md), déclare la table des messages utilisée par la fenêtre contenue.

`m_pObject` est initialisé par le constructeur. Pour obtenir un exemple, consultez la vue d’ensemble de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) .

## <a name="ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a> CContainedWindowT::RegisterWndSuperclass

Appelée par [Create](#create) pour inscrire la classe de fenêtre de la fenêtre contenue.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, un atome qui identifie de façon unique la classe de fenêtre en cours d’inscription ; Sinon, zéro.

### <a name="remarks"></a>Notes

Cette classe de fenêtre est basée sur une classe existante, mais utilise [CContainedWindowT :: WindowProc](#windowproc). Le nom et la procédure de fenêtre de la classe de fenêtre existante sont enregistrés dans [m_lpszClassName](#m_lpszclassname) et [m_pfnSuperWindowProc](#m_pfnsuperwindowproc), respectivement.

## <a name="ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a> CContainedWindowT::SubclassWindow

Sous-classe la fenêtre identifiée par *HWND* et l’attache à l' `CContainedWindowT` objet.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
dans Handle de la fenêtre en cours de sous-classe.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fenêtre est sous-classée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

La fenêtre sous-classée utilise désormais [CContainedWindowT :: WindowProc](#windowproc). La procédure de fenêtre d’origine est enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> N’appelez pas `SubclassWindow` si vous avez déjà appelé [Create](#create).

## <a name="ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a> CContainedWindowT::SwitchMessageMap

Modifie la table des messages qui sera utilisée pour traiter les messages de la fenêtre contenue.

```cpp
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Paramètres

*dwMsgMapID*<br/>
dans Identificateur de la table des messages. Pour utiliser la table des messages par défaut déclarée avec [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), transmettez zéro. Pour utiliser une autre table des messages déclarée avec [ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map), transmettez `msgMapID` .

### <a name="remarks"></a>Notes

La table des messages doit être définie dans l’objet conteneur.

Vous spécifiez initialement l’identificateur de la table des messages dans le constructeur.

## <a name="ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a> CContainedWindowT::UnsubclassWindow

Détache la fenêtre sous-classée de l' `CContainedWindowT` objet et restaure la procédure de fenêtre d’origine, enregistrée dans [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Paramètres

*bForce*<br/>
dans Affectez la valeur TRUE pour forcer la restauration de la procédure de fenêtre d’origine, même si la procédure de fenêtre pour cet `CContainedWindowT` objet n’est pas actuellement active. Si *bForce* a la valeur false et que la procédure de fenêtre pour cet `CContainedWindowT` objet n’est pas actuellement active, la procédure de fenêtre d’origine ne sera pas restaurée.

### <a name="return-value"></a>Valeur renvoyée

Handle de la fenêtre sous-classé précédemment. Si *bForce* a la valeur false et que la procédure de fenêtre pour cet `CContainedWindowT` objet n’est pas actuellement active, retourne la valeur null.

### <a name="remarks"></a>Notes

Utilisez cette méthode uniquement si vous souhaitez restaurer la procédure de fenêtre d’origine avant la destruction de la fenêtre. Dans le cas contraire, [WindowProc](#windowproc) le fera automatiquement lorsque la fenêtre sera détruite.

## <a name="ccontainedwindowtwindowproc"></a><a name="windowproc"></a> CContainedWindowT :: WindowProc

Cette méthode statique implémente la procédure de fenêtre.

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

### <a name="return-value"></a>Valeur renvoyée

Résultat du traitement du message.

### <a name="remarks"></a>Notes

`WindowProc` dirige les messages vers la table des messages identifiée par [m_dwMsgMapID](#m_dwmsgmapid). Si nécessaire, `WindowProc` appelle [DefWindowProc](#defwindowproc) pour le traitement des messages supplémentaires.

## <a name="see-also"></a>Voir aussi

[CWindow (classe)](../../atl/reference/cwindow-class.md)<br/>
[CWindowImpl (classe)](../../atl/reference/cwindowimpl-class.md)<br/>
[CMessageMap, classe](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP (msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

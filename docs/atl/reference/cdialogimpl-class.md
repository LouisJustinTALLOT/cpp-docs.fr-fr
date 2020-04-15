---
title: Classe CDialogImpl
ms.date: 11/04/2016
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
ms.openlocfilehash: 900a312c97d7b83eac93a372be39a006b3c4344d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327062"
---
# <a name="cdialogimpl-class"></a>Classe CDialogImpl

Cette classe fournit des méthodes pour créer une boîte de dialogue modale ou sans mode.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `CDialogImpl`dérivée de .

*TBase (TBase)*<br/>
La classe de base de votre nouvelle classe. La classe de base par défaut est [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Créer](#create)|Crée une boîte de dialogue sans mode.|
|[DétruireWindow](#destroywindow)|Détruit une boîte de dialogue sans mode.|
|[DoModal (En)](#domodal)|Crée une boîte de dialogue modal.|
|[EndDialog (en)](#enddialog)|Détruit une boîte de dialogue modal.|

### <a name="cdialogimplbaset-methods"></a>Méthodes CDialogImplBaseT

|||
|-|-|
|[GetDialogProc (en)](#getdialogproc)|Retourne la procédure actuelle de boîte de dialogue.|
|[MapDialogRect (en)](#mapdialogrect)|Cartographier les unités de la boîte de dialogue du rectangle spécifié pour filtrer les unités (pixels).|
|[OnFinalMessage](#onfinalmessage)|Appelé après avoir reçu le dernier message, généralement WM_NCDESTROY.|

### <a name="static-functions"></a>Fonctions statiques

|||
|-|-|
|[DialogProc](#dialogproc)|Traite les messages envoyés à la boîte de dialogue.|
|[StartDialogProc](#startdialogproc)|Appelé lorsque le premier message est reçu pour traiter les messages envoyés à la boîte de dialogue.|

## <a name="remarks"></a>Notes

Avec `CDialogImpl` vous pouvez créer une boîte de dialogue modale ou sans mode. `CDialogImpl`fournit la procédure de boîte de dialogue, qui utilise la carte de message par défaut pour diriger les messages vers les gestionnaires appropriés.

Le destructeur de `~CWindowImplRoot` classe de base assure que la fenêtre a disparu avant de détruire l’objet.

`CDialogImpl`dérive de `CDialogImplBaseT`, qui à `CWindowImplRoot`son tour dérive de .

> [!NOTE]
> Votre classe doit `IDD` définir un membre qui spécifie l’ID de ressources du modèle de dialogue. Par exemple, l’assistant de projet ATL ajoute automatiquement la ligne suivante à votre classe :

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

où `MyDlg` le **nom court** est inscrit dans la page **Noms** de l’assistant.

|Pour plus d’informations sur l’un des sujets suivants :|Consultez|
|--------------------------------|---------|
|Création de contrôles|[Tutoriel ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilisation de boîtes de dialogue dans ATL|[Cours de fenêtre ATL](../../atl/atl-window-classes.md)|
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|
|Boîtes de dialogue|[Dialog Boxes](/windows/win32/dlgbox/dialog-boxes) et sujets ultérieurs dans le Windows SDK|

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="cdialogimplcreate"></a><a name="create"></a>CDialogImpl::Créer

Crée une boîte de dialogue sans mode.

```
HWND Create(
    HWND hWndParent,
    LPARAM dwInitParam = NULL );

HWND Create(
    HWND hWndParent,
    RECT&,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
[dans] La poignée à la fenêtre du propriétaire.

**RECT&** *rect* [dans] une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) précisant la taille et la position du dialogue.

*dwInitParam*<br/>
[dans] Spécifie la valeur de passer à la boîte de dialogue dans le paramètre *lParam* du message WM_INITDIALOG.

### <a name="return-value"></a>Valeur de retour

Le manche de la boîte de dialogue nouvellement créée.

### <a name="remarks"></a>Notes

Cette boîte de dialogue est `CDialogImpl` automatiquement fixée à l’objet. Pour créer une boîte de dialogue modal, appelez [DoModal](#domodal). Le deuxième remplacement ci-dessus n’est utilisé qu’avec [CComControl](../../atl/reference/ccomcontrol-class.md).

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a>CDialogImpl::DestroyWindow

Détruit une boîte de dialogue sans mode.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Valeur de retour

VRAI si la boîte de dialogue a été détruite avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

Retourne VRAI si la boîte de dialogue a été détruite avec succès; autrement FALSE.

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a>CDialogImpl::DialogProc

Cette fonction statique met en œuvre la procédure de boîte de dialogue.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[dans] La poignée de la boîte de dialogue.

*uMsg*<br/>
[dans] Le message envoyé à la boîte de dialogue.

*wParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

*lParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur de retour

VRAI si le message est traité; autrement, FALSE.

### <a name="remarks"></a>Notes

`DialogProc`utilise la carte des messages par défaut pour diriger les messages vers les gestionnaires appropriés.

Vous pouvez `DialogProc` remplacer pour fournir un mécanisme différent pour le traitement des messages.

## <a name="cdialogimpldomodal"></a><a name="domodal"></a>CDialogImpl::DoModal

Crée une boîte de dialogue modal.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
[dans] La poignée à la fenêtre du propriétaire. La valeur par défaut est la valeur de retour de la fonction [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32.

*dwInitParam*<br/>
[dans] Spécifie la valeur de passer à la boîte de dialogue dans le paramètre *lParam* du message WM_INITDIALOG.

### <a name="return-value"></a>Valeur de retour

En cas de succès, la valeur du paramètre *nRetCode* spécifié dans l’appel à [EndDialog](#enddialog). Sinon, -1.

### <a name="remarks"></a>Notes

Cette boîte de dialogue est `CDialogImpl` automatiquement fixée à l’objet.

Pour créer une boîte de dialogue sans mode, appelez [Create](#create).

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a>CDialogImpl::EndDialog

Détruit une boîte de dialogue modal.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Paramètres

*nRetCode (nRetCode)*<br/>
[dans] La valeur à retourner par [CDialogImpl::DoModal](#domodal).

### <a name="return-value"></a>Valeur de retour

VRAI si la boîte de dialogue est détruite; autrement, FALSE.

### <a name="remarks"></a>Notes

`EndDialog`doit être appelé par la procédure de dialogue. Après la boîte de dialogue est détruite, Windows utilise la `DoModal`valeur de *nRetCode* comme la valeur de retour pour , qui a créé la boîte de dialogue.

> [!NOTE]
> N’appelez `EndDialog` pas pour détruire une boîte de dialogue sans mode. Appelez [CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) à la place.

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CDialogImpl::GetDialogProc

Retours `DialogProc`, la procédure actuelle boîte de dialogue.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Valeur de retour

La procédure actuelle de boîte de dialogue.

### <a name="remarks"></a>Notes

Remplacez cette méthode pour remplacer la procédure de dialogue par la vôtre.

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a>CDialogImpl::MapDialogRect

Convertit (cartes) les unités de boîte de dialogue du rectangle spécifié en unités d’écran (pixels).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Indique une `CRect` structure d’objet ou [de RECT](/windows/win32/api/windef/ns-windef-rect) qui doit recevoir les coordonnées client de la mise à jour qui entoure la région de mise à jour.

### <a name="return-value"></a>Valeur de retour

Nonzero si la mise à jour réussit; 0 si la mise à jour échoue. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

### <a name="remarks"></a>Notes

La fonction remplace les coordonnées `RECT` de la structure spécifiée par les coordonnées converties, ce qui permet d’utiliser la structure pour créer une boîte de dialogue ou positionner un contrôle dans une boîte de dialogue.

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a>CDialogImpl::OnFinalMessage

Appelé après avoir reçu `WM_NCDESTROY`le dernier message (généralement ).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[dans] Une poignée à la fenêtre détruite.

### <a name="remarks"></a>Notes

Notez que si vous souhaitez supprimer automatiquement votre objet sur la destruction de la fenêtre, vous pouvez appeler **supprimer ceci;** ici.

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a>CDialogImpl::StartDialogProc

Appelé qu’une seule fois, lorsque le premier message est reçu, pour traiter les messages envoyés à la boîte de dialogue.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[dans] La poignée de la boîte de dialogue.

*uMsg*<br/>
[dans] Le message envoyé à la boîte de dialogue.

*wParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

*lParam*<br/>
[dans] Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur de retour

La procédure de fenêtre.

### <a name="remarks"></a>Notes

Après l’appel `StartDialogProc` `DialogProc` initial à , est fixé comme une procédure de dialogue, et d’autres appels y aller.

## <a name="see-also"></a>Voir aussi

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

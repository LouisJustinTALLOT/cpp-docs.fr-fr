---
description: 'En savoir plus sur : classe CDialogImpl'
title: CDialogImpl (classe)
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
ms.openlocfilehash: 228a63edde7eb66960a0acad5d60088d909946a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141854"
---
# <a name="cdialogimpl-class"></a>CDialogImpl (classe)

Cette classe fournit des méthodes pour créer une boîte de dialogue modale ou non modale.

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
Votre classe, dérivée de `CDialogImpl` .

*TBase*<br/>
Classe de base de votre nouvelle classe. La classe de base par défaut est [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Fonction|Description|
|-|-|
|[Créer](#create)|Crée une boîte de dialogue non modale.|
|[DestroyWindow](#destroywindow)|Détruit une boîte de dialogue non modale.|
|[DoModal](#domodal)|Crée une boîte de dialogue modale.|
|[EndDialog](#enddialog)|Détruit une boîte de dialogue modale.|

### <a name="cdialogimplbaset-methods"></a>Méthodes CDialogImplBaseT

|Fonction|Description|
|-|-|
|[GetDialogProc](#getdialogproc)|Retourne la procédure de la boîte de dialogue active.|
|[MapDialogRect](#mapdialogrect)|Mappe les unités de boîte de dialogue du rectangle spécifié aux unités d’écran (pixels).|
|[OnFinalMessage](#onfinalmessage)|Appelé après la réception du dernier message, généralement WM_NCDESTROY.|

### <a name="static-functions"></a>Fonctions statiques

|Fonction|Description|
|-|-|
|[DialogProc](#dialogproc)|Traite les messages envoyés à la boîte de dialogue.|
|[StartDialogProc](#startdialogproc)|Appelé lorsque le premier message est reçu pour traiter les messages envoyés à la boîte de dialogue.|

## <a name="remarks"></a>Notes

Avec `CDialogImpl` , vous pouvez créer une boîte de dialogue modale ou non modale. `CDialogImpl` fournit la procédure de boîte de dialogue, qui utilise la table des messages par défaut pour diriger les messages vers les gestionnaires appropriés.

Le destructeur de classe de base `~CWindowImplRoot` garantit que la fenêtre a disparu avant de détruire l’objet.

`CDialogImpl` dérive de `CDialogImplBaseT` , qui dérive à son tour de `CWindowImplRoot` .

> [!NOTE]
> Votre classe doit définir un `IDD` membre qui spécifie l’ID de ressource du modèle de boîte de dialogue. Par exemple, l’Assistant Projet ATL ajoute automatiquement la ligne suivante à votre classe :

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

où `MyDlg` est le **nom abrégé** entré dans la page **noms** de l’Assistant.

|Pour plus d’informations sur l’un des sujets suivants :|Consultez|
|--------------------------------|---------|
|Création de contrôles|[Tutoriel ATL](../../atl/active-template-library-atl-tutorial.md)|
|Utilisation des boîtes de dialogue dans ATL|[Classes de fenêtre ATL](../../atl/atl-window-classes.md)|
|Assistant Projet ATL|[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)|
|Boîtes de dialogue|[Boîtes de dialogue](/windows/win32/dlgbox/dialog-boxes) et rubriques suivantes de la SDK Windows|

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="cdialogimplcreate"></a><a name="create"></a> CDialogImpl :: Create

Crée une boîte de dialogue non modale.

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
dans Handle de la fenêtre propriétaire.

**Rect&** *Rect* [in] structure [Rect](/windows/win32/api/windef/ns-windef-rect) spécifiant la taille et la position de la boîte de dialogue.

*dwInitParam*<br/>
dans Spécifie la valeur à passer à la boîte de dialogue dans le paramètre *lParam* du message de WM_INITDIALOG.

### <a name="return-value"></a>Valeur renvoyée

Handle de la boîte de dialogue nouvellement créée.

### <a name="remarks"></a>Notes

Cette boîte de dialogue est automatiquement jointe à l' `CDialogImpl` objet. Pour créer une boîte de dialogue modale [, appelez DoModal](#domodal). Le deuxième remplacement ci-dessus est utilisé uniquement avec [CComControl](../../atl/reference/ccomcontrol-class.md).

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a> CDialogImpl ::D estroyWindow

Détruit une boîte de dialogue non modale.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la boîte de dialogue a été détruite avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Retourne la valeur TRUE si la boîte de dialogue a été détruite avec succès ; Sinon, FALSe.

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a> CDialogImpl ::D ialogProc

Cette fonction statique implémente la procédure de boîte de dialogue.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
dans Handle de la boîte de dialogue.

*uMsg*<br/>
dans Message envoyé à la boîte de dialogue.

*wParam*<br/>
dans Informations supplémentaires spécifiques au message.

*lParam*<br/>
dans Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le message est traité ; Sinon, FALSe.

### <a name="remarks"></a>Notes

`DialogProc` utilise la table des messages par défaut pour diriger les messages vers les gestionnaires appropriés.

Vous pouvez remplacer `DialogProc` pour fournir un mécanisme différent pour la gestion des messages.

## <a name="cdialogimpldomodal"></a><a name="domodal"></a> CDialogImpl ::D oModal

Crée une boîte de dialogue modale.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
dans Handle de la fenêtre propriétaire. La valeur par défaut est la valeur de retour de la fonction Win32 [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) .

*dwInitParam*<br/>
dans Spécifie la valeur à passer à la boîte de dialogue dans le paramètre *lParam* du message de WM_INITDIALOG.

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, la valeur du paramètre *nRetCode* spécifiée dans l’appel à [EndDialog](#enddialog). Sinon, -1.

### <a name="remarks"></a>Notes

Cette boîte de dialogue est automatiquement jointe à l' `CDialogImpl` objet.

Pour créer une boîte de dialogue non modale, appelez [Create](#create).

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a> CDialogImpl :: EndDialog

Détruit une boîte de dialogue modale.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Paramètres

*nRetCode*<br/>
dans Valeur à retourner par [CDialogImpl ::D omodal](#domodal).

### <a name="return-value"></a>Valeur renvoyée

TRUE si la boîte de dialogue est détruite ; Sinon, FALSe.

### <a name="remarks"></a>Notes

`EndDialog` doit être appelé par le biais de la procédure de dialogue. Une fois la boîte de dialogue détruite, Windows utilise la valeur de *nRetCode* comme valeur de retour pour `DoModal` , qui a créé la boîte de dialogue.

> [!NOTE]
> N’appelez pas `EndDialog` pour détruire une boîte de dialogue non modale. Appelez [CWindow ::D estroywindow](../../atl/reference/cwindow-class.md#destroywindow) à la place.

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a> CDialogImpl :: GetDialogProc

Retourne `DialogProc` , la procédure de la boîte de dialogue active.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Valeur renvoyée

Procédure de la boîte de dialogue active.

### <a name="remarks"></a>Notes

Substituez cette méthode pour remplacer la procédure de dialogue par la vôtre.

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a> CDialogImpl :: MapDialogRect

Convertit (mappe) les unités de boîte de dialogue du rectangle spécifié en unités d’écran (pixels).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Paramètres

*lpRect*<br/>
Pointe vers un `CRect` objet ou une structure [Rect](/windows/win32/api/windef/ns-windef-rect) qui doit recevoir les coordonnées clientes de la mise à jour qui englobe la région de mise à jour.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la mise à jour est réussie ; 0 si la mise à jour échoue. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

### <a name="remarks"></a>Notes

La fonction remplace les coordonnées de la `RECT` structure spécifiée par les coordonnées converties, ce qui permet à la structure d’être utilisée pour créer une boîte de dialogue ou positionner un contrôle dans une boîte de dialogue.

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a> CDialogImpl :: OnFinalMessage

Appelé après la réception du dernier message (en général `WM_NCDESTROY` ).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
dans Handle de la fenêtre en cours de destruction.

### <a name="remarks"></a>Notes

Notez que, si vous souhaitez supprimer automatiquement votre objet lors de la destruction de la fenêtre, vous pouvez appeler **Delete this ;** ici.

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a> CDialogImpl :: StartDialogProc

Appelée une seule fois, lorsque le premier message est reçu, pour traiter les messages envoyés à la boîte de dialogue.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
dans Handle de la boîte de dialogue.

*uMsg*<br/>
dans Message envoyé à la boîte de dialogue.

*wParam*<br/>
dans Informations supplémentaires spécifiques au message.

*lParam*<br/>
dans Informations supplémentaires spécifiques au message.

### <a name="return-value"></a>Valeur renvoyée

La procédure de fenêtre.

### <a name="remarks"></a>Notes

Après l’appel initial à `StartDialogProc` , `DialogProc` est défini comme une procédure de dialogue et d’autres appels y sont effectués.

## <a name="see-also"></a>Voir aussi

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

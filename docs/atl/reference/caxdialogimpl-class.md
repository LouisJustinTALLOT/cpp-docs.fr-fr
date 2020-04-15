---
title: Classe CAxDialogImpl
ms.date: 11/04/2016
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
ms.openlocfilehash: d8e60a817d197f67c14318a7d50ddf796e570142
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318739"
---
# <a name="caxdialogimpl-class"></a>Classe CAxDialogImpl

Cette classe met en œuvre une boîte de dialogue (modale ou sans mode) qui héberge les commandes ActiveX.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `CAxDialogImpl`dérivée de .

*TBase (TBase)*<br/>
La classe de `CDialogImplBaseT`fenêtre de base pour .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Appelez cette méthode pour conseiller ou déconseiller toutes les entrées de la carte de l’évier de l’objet.|
|[CAxDialogImpl::Créer](#create)|Appelez cette méthode pour créer une boîte de dialogue sans mode.|
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Appelez cette méthode pour détruire une boîte de dialogue sans mode.|
|[CAxDialogImpl::DoModal](#domodal)|Appelez cette méthode pour créer une boîte de dialogue modal.|
|[CAxDialogImpl::EndDialog](#enddialog)|Appelez cette méthode pour détruire une boîte de dialogue modal.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Appelez cette méthode pour obtenir `DialogProc` un pointeur à la fonction de rappel.|
|[CAxDialogImpl::GetIDD](#getidd)|Appelez cette méthode pour obtenir l’ID de ressources de modèle de dialogue|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Appelez cette méthode pour déterminer si un message est destiné à cette boîte de dialogue et, si elle est, traiter le message.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CAxDialogImpl::m_bModal](#m_bmodal)|Une variable qui n’existe que dans les constructions de débogs et est définie à vrai si la boîte de dialogue est modal.|

## <a name="remarks"></a>Notes

`CAxDialogImpl`vous permet de créer une boîte de dialogue modale ou sans mode. `CAxDialogImpl`fournit la procédure de boîte de dialogue, qui utilise la carte de message par défaut pour diriger les messages vers les gestionnaires appropriés.

`CAxDialogImpl`dérive de `CDialogImplBaseT`, qui à son tour dérive `CWindow`de `CMessageMap` *TBase* (par défaut, ) et .

Votre classe doit définir un membre IDD qui spécifie l’ID de ressources du modèle de dialogue. Par exemple, l’ajout d’un objet ATL Dialog à l’aide de la boîte de dialogue **Add Class** ajoute automatiquement la ligne suivante à votre classe :

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

où `MyDialog` est le **nom court** inscrit dans le assistant de dialogue ATL.

Voir [la mise en œuvre d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md) pour plus d’informations.

Notez qu’un contrôle ActiveX sur une `CAxDialogImpl` boîte de dialogue modal créée avec ne prendra pas en charge les touches d’accélérateur. Pour prendre en charge les touches `CAxDialogImpl`d’accélérateur sur une boîte de dialogue créée avec , créer une boîte de dialogue sans mode et, en utilisant votre propre boucle de message, utilisez [CAxDialogImpl::IsDialogMessage](#isdialogmessage) après avoir reçu un message de la file d’attente pour gérer une clé d’accélérateur.

Pour plus `CAxDialogImpl`d’informations sur , voir [ATL Control Containment FAQ](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="caxdialogimpladvisesinkmap"></a><a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap

Appelez cette méthode pour conseiller ou déconseiller toutes les entrées de la carte de l’évier de l’objet.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Paramètres

*bAdvise (en)*<br/>
Définir pour être vrai si toutes les entrées d’évier doivent être conseillées; faux si toutes les entrées d’évier doivent être déconseillées.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="caxdialogimplcreate"></a><a name="create"></a>CAxDialogImpl::Créer

Appelez cette méthode pour créer une boîte de dialogue sans mode.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
[dans] La poignée à la fenêtre du propriétaire.

*dwInitParam*<br/>
[dans] Spécifie la valeur de passer à la boîte de dialogue dans le paramètre *lParam* du message WM_INITDIALOG.

*&RECT*<br/>
Ce paramètre n'est pas utilisé. Ce paramètre est `CComControl`transmis par .

### <a name="return-value"></a>Valeur de retour

Le manche de la boîte de dialogue nouvellement créée.

### <a name="remarks"></a>Notes

Cette boîte de dialogue est `CAxDialogImpl` automatiquement fixée à l’objet. Pour créer une boîte de dialogue modal, appelez [DoModal](#domodal).

Le deuxième remplacement est fourni uniquement afin que les boîtes de dialogue peuvent être utilisées avec [CComControl](../../atl/reference/ccomcontrol-class.md).

## <a name="caxdialogimpldestroywindow"></a><a name="destroywindow"></a>CAxDialogImpl::DestroyWindow

Appelez cette méthode pour détruire une boîte de dialogue sans mode.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre est détruite avec succès; autrement FALSE.

### <a name="remarks"></a>Notes

N’appelez `DestroyWindow` pas pour détruire une boîte de dialogue modal. Appelez [EndDialog](#enddialog) à la place.

## <a name="caxdialogimpldomodal"></a><a name="domodal"></a>CAxDialogImpl::DoModal

Appelez cette méthode pour créer une boîte de dialogue modal.

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

En cas de succès, la valeur du paramètre *nRetCode* spécifié dans l’appel à [EndDialog](#enddialog); sinon, -1.

### <a name="remarks"></a>Notes

Cette boîte de dialogue est `CAxDialogImpl` automatiquement fixée à l’objet.

Pour créer une boîte de dialogue sans mode, appelez [Create](#create).

## <a name="caxdialogimplenddialog"></a><a name="enddialog"></a>CAxDialogImpl::EndDialog

Appelez cette méthode pour détruire une boîte de dialogue modal.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Paramètres

*nRetCode (nRetCode)*<br/>
[dans] La valeur à retourner par [DoModal](#domodal).

### <a name="return-value"></a>Valeur de retour

VRAI si la boîte de dialogue est détruite; autrement, FALSE.

### <a name="remarks"></a>Notes

`EndDialog`doit être appelé par la procédure de boîte de dialogue. Après la boîte de dialogue est détruite, Windows utilise la `DoModal`valeur de *nRetCode* comme la valeur de retour pour , qui a créé la boîte de dialogue.

> [!NOTE]
> N’appelez `EndDialog` pas pour détruire une boîte de dialogue sans mode. Appelez [DestroyWindow](#destroywindow) à la place.

## <a name="caxdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc

Appelez cette méthode pour obtenir `DialogProc` un pointeur à la fonction de rappel.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la `DialogProc` fonction de rappel.

### <a name="remarks"></a>Notes

La `DialogProc` fonction est une fonction de rappel définie par l’application.

## <a name="caxdialogimplgetidd"></a><a name="getidd"></a>CAxDialogImpl::GetIDD

Appelez cette méthode pour obtenir l’ID de ressources de modèle de dialogue.

```
int GetIDD();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’ID de ressources du modèle de dialogue.

## <a name="caxdialogimplisdialogmessage"></a><a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage

Appelez cette méthode pour déterminer si un message est destiné à cette boîte de dialogue et, si elle est, traiter le message.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Pointeur vers une structure [MSG](/windows/win32/api/winuser/ns-winuser-msg) qui contient le message à vérifier.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le message a été traité, FALSE autrement.

### <a name="remarks"></a>Notes

Cette méthode est destinée à être appelée à partir d’une boucle de message.

## <a name="caxdialogimplm_bmodal"></a><a name="m_bmodal"></a>CAxDialogImpl::m_bModal

Une variable qui n’existe que dans les constructions de débogs et est définie à vrai si la boîte de dialogue est modal.

```
bool m_bModal;
```

## <a name="see-also"></a>Voir aussi

[Classe CDialogImpl](../../atl/reference/cdialogimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

---
title: CAxDialogImpl, classe
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
ms.openlocfilehash: 548d2aed0644187b4b8dee1e472b581f1f92d6a1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865054"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl, classe

Cette classe implémente une boîte de dialogue (modale ou non modale) qui héberge des contrôles ActiveX.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `CAxDialogImpl`.

*TBase*<br/>
Classe de fenêtre de base pour `CDialogImplBaseT`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CAxDialogImpl :: AdviseSinkMap](#advisesinkmap)|Appelez cette méthode pour informer ou déconseiller toutes les entrées dans la table des événements de la table de récepteurs de l’objet.|
|[CAxDialogImpl :: Create](#create)|Appelez cette méthode pour créer une boîte de dialogue non modale.|
|[CAxDialogImpl ::D estroyWindow](#destroywindow)|Appelez cette méthode pour détruire une boîte de dialogue non modale.|
|[CAxDialogImpl ::D oModal](#domodal)|Appelez cette méthode pour créer une boîte de dialogue modale.|
|[CAxDialogImpl :: EndDialog](#enddialog)|Appelez cette méthode pour détruire une boîte de dialogue modale.|
|[CAxDialogImpl :: GetDialogProc](#getdialogproc)|Appelez cette méthode pour obtenir un pointeur vers la fonction de rappel `DialogProc`.|
|[CAxDialogImpl :: GetIDD](#getidd)|Appelez cette méthode pour accéder à l’ID de ressource du modèle de boîte de dialogue|
|[CAxDialogImpl :: IsDialogMessage](#isdialogmessage)|Appelez cette méthode pour déterminer si un message est destiné à cette boîte de dialogue et, si c’est le cas, traiter le message.|

### <a name="protected-data-members"></a>Membres de données protégées

|Name|Description|
|----------|-----------------|
|[CAxDialogImpl :: m_bModal](#m_bmodal)|Variable qui existe uniquement dans les versions Debug et qui a la valeur true si la boîte de dialogue est modale.|

## <a name="remarks"></a>Notes

`CAxDialogImpl` vous permet de créer une boîte de dialogue modale ou non modale. `CAxDialogImpl` fournit la procédure de boîte de dialogue, qui utilise la table des messages par défaut pour diriger les messages vers les gestionnaires appropriés.

`CAxDialogImpl` dérive de `CDialogImplBaseT`, qui dérive à son tour de *TBase* (par défaut, `CWindow`) et `CMessageMap`.

Votre classe doit définir un membre IDD qui spécifie l’ID de ressource du modèle de boîte de dialogue. Par exemple, l’ajout d’un objet de boîte de dialogue ATL à l’aide de la boîte de dialogue **Ajouter une classe** ajoute automatiquement la ligne suivante à votre classe :

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

où `MyDialog` est le **nom abrégé** entré dans l’Assistant boîte de dialogue ATL.

Pour plus d’informations, consultez [implémentation d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md) .

Notez qu’un contrôle ActiveX dans une boîte de dialogue modale créée avec `CAxDialogImpl` ne prend pas en charge les touches d’accès rapide. Pour prendre en charge les touches accélérateur sur une boîte de dialogue créée avec `CAxDialogImpl`, créez une boîte de dialogue non modale et, à l’aide de votre propre boucle de message, utilisez [CAxDialogImpl :: IsDialogMessage](#isdialogmessage) après avoir obtenu un message de la file d’attente pour gérer une touche accélérateur.

Pour plus d’informations sur les `CAxDialogImpl`, consultez [Forum aux questions sur la relation contenant-contenu de contrôle ATL](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="advisesinkmap"></a>CAxDialogImpl :: AdviseSinkMap

Appelez cette méthode pour informer ou déconseiller toutes les entrées dans la table des événements de la table de récepteurs de l’objet.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Paramètres

*bAdvise*<br/>
A la valeur true si toutes les entrées de récepteur doivent être notifiées ; false si toutes les entrées de récepteur ne doivent pas être avisées.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="create"></a>CAxDialogImpl :: Create

Appelez cette méthode pour créer une boîte de dialogue non modale.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
dans Handle de la fenêtre propriétaire.

*dwInitParam*<br/>
dans Spécifie la valeur à passer à la boîte de dialogue dans le paramètre *lParam* du message de WM_INITDIALOG.

*RECT &*<br/>
Ce paramètre n'est pas utilisé. Ce paramètre est passé par `CComControl`.

### <a name="return-value"></a>Valeur de retour

Handle de la boîte de dialogue nouvellement créée.

### <a name="remarks"></a>Notes

Cette boîte de dialogue est automatiquement jointe à l’objet `CAxDialogImpl`. Pour créer une boîte de dialogue modale [, appelez DoModal](#domodal).

La deuxième substitution est fournie uniquement si les boîtes de dialogue peuvent être utilisées avec [CComControl](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>CAxDialogImpl ::D estroyWindow

Appelez cette méthode pour détruire une boîte de dialogue non modale.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre est détruite avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

N’appelez pas `DestroyWindow` pour détruire une boîte de dialogue modale. Appelez à la place [EndDialog](#enddialog) .

##  <a name="domodal"></a>CAxDialogImpl ::D oModal

Appelez cette méthode pour créer une boîte de dialogue modale.

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

### <a name="return-value"></a>Valeur de retour

En cas de réussite, la valeur du paramètre *nRetCode* spécifié dans l’appel à [EndDialog](#enddialog); Sinon,-1.

### <a name="remarks"></a>Notes

Cette boîte de dialogue est automatiquement jointe à l’objet `CAxDialogImpl`.

Pour créer une boîte de dialogue non modale, appelez [Create](#create).

##  <a name="enddialog"></a>CAxDialogImpl :: EndDialog

Appelez cette méthode pour détruire une boîte de dialogue modale.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Paramètres

*nRetCode*<br/>
dans Valeur à retourner par [DoModal](#domodal).

### <a name="return-value"></a>Valeur de retour

TRUE si la boîte de dialogue est détruite ; Sinon, FALSe.

### <a name="remarks"></a>Notes

`EndDialog` doit être appelée à l’aide de la procédure de la boîte de dialogue. Une fois la boîte de dialogue détruite, Windows utilise la valeur de *nRetCode* comme valeur de retour pour `DoModal`, qui a créé la boîte de dialogue.

> [!NOTE]
>  N’appelez pas `EndDialog` pour détruire une boîte de dialogue non modale. Appelez [DestroyWindow](#destroywindow) à la place.

##  <a name="getdialogproc"></a>CAxDialogImpl :: GetDialogProc

Appelez cette méthode pour obtenir un pointeur vers la fonction de rappel `DialogProc`.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la fonction de rappel `DialogProc`.

### <a name="remarks"></a>Notes

La fonction `DialogProc` est une fonction de rappel définie par l’application.

##  <a name="getidd"></a>CAxDialogImpl :: GetIDD

Appelez cette méthode pour accéder à l’ID de ressource du modèle de boîte de dialogue.

```
int GetIDD();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’ID de ressource du modèle de boîte de dialogue.

##  <a name="isdialogmessage"></a>CAxDialogImpl :: IsDialogMessage

Appelez cette méthode pour déterminer si un message est destiné à cette boîte de dialogue et, si c’est le cas, traiter le message.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Paramètres

*pMsg*<br/>
Pointeur vers une structure [MSG](/windows/win32/api/winuser/ns-winuser-msg) qui contient le message à vérifier.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le message a été traité ; sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode est destinée à être appelée à partir d’une boucle de message.

##  <a name="m_bmodal"></a>CAxDialogImpl :: m_bModal

Variable qui existe uniquement dans les versions Debug et qui a la valeur true si la boîte de dialogue est modale.

```
bool m_bModal;
```

## <a name="see-also"></a>Voir aussi

[CDialogImpl, classe](../../atl/reference/cdialogimpl-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

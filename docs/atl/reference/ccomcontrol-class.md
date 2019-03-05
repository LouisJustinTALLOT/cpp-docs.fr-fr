---
title: CComControl, classe
ms.date: 11/04/2016
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
ms.openlocfilehash: 29eeb31c0823a0614fa1404cf7efc1c281bab3a4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261581"
---
# <a name="ccomcontrol-class"></a>CComControl, classe

Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
La classe qui implémente le contrôle.

*WinBase*<br/>
La classe de base qui implémente les fonctions de fenêtrage. Valeur par défaut est [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Récupère un pointeur vers l'interface demandée.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Crée une fenêtre pour le contrôle.|
|[CComControl::FireOnChanged](#fireonchanged)|Notifie le récepteur du conteneur qu’une propriété de contrôle a changé.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Avertit les récepteurs du conteneur qu’une propriété de contrôle est va être modifiée et que l’objet demandant le récepteur comment procéder.|
|[CComControl::MessageBox](#messagebox)|Appelez cette méthode pour créer, afficher et utiliser une boîte de message.|

## <a name="remarks"></a>Notes

`CComControl` est un ensemble de fonctions d’assistance de contrôle pratique et des membres de données essentielles pour les contrôles ATL. Lorsque vous créez un contrôle standard ou un contrôle DHTML Edit à l’aide de l’Assistant contrôle ATL, l’Assistant dérivera automatiquement votre classe à partir de `CComControl`. `CComControl` dérive la plupart de ses méthodes à partir de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Pour plus d’informations sur la création d’un contrôle, consultez le [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md). Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

Pour une démonstration de `CComControl` méthodes et les membres de données, consultez le [CERC](../../visual-cpp-samples.md) exemple.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl.h

##  <a name="ccomcontrol"></a>  CComControl::CComControl

Constructeur.

```
CComControl();
```

### <a name="remarks"></a>Notes

Appelle le [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) constructeur, en passant le `m_hWnd` membre de données héritées par le biais [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface

Récupère un pointeur vers l'interface demandée.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Paramètres

*iid*<br/>
[in] Le GUID de l’interface demandée.

*ppv*<br/>
[out] Un pointeur vers le pointeur d’interface identifié par *iid*, ou NULL si l’interface est introuvable.

### <a name="remarks"></a>Notes

gère seulement des interfaces dans la table de mappage COM.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>  CComControl::CreateControlWindow

Par défaut, crée une fenêtre pour le contrôle en appelant `CWindowImpl::Create`.

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
[in] Handle de la fenêtre parente ou propriétaire. Un handle de fenêtre valide doit être fourni. La fenêtre de contrôle se limite à la zone de sa fenêtre parente.

*rcPos*<br/>
[in] La taille initiale et la position de la fenêtre doit être créé.

### <a name="remarks"></a>Notes

Substituez cette méthode si vous voulez faire quelque chose autre que créer une fenêtre unique, par exemple, pour créer deux fenêtres, un d'entre eux devienne une barre d’outils pour votre contrôle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>  CComControl::FireOnChanged

Notifie le récepteur du conteneur qu’une propriété de contrôle a changé.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*dispID*<br/>
[in] Identificateur de la propriété qui a changé.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Si votre classe de contrôle dérive [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink), cette méthode appelle [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) pour notifier tous connectés `IPropertyNotifySink` les interfaces que le contrôle spécifié propriété a été modifiée. Si votre classe de contrôle ne dérive pas de `IPropertyNotifySink`, cette méthode retourne S_OK.

Cette méthode est sécurisée pour appeler, même si votre contrôle ne prend pas en charge les points de connexion.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit

Avertit les récepteurs du conteneur qu’une propriété de contrôle est va être modifiée et que l’objet demandant le récepteur comment procéder.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*dispID*<br/>
[in] Identificateur de la propriété va être modifiée.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Si votre classe de contrôle dérive [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink), cette méthode appelle [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) pour notifier tous connectés `IPropertyNotifySink` les interfaces que le texte spécifié propriété du contrôle est va être modifiée. Si votre classe de contrôle ne dérive pas de `IPropertyNotifySink`, cette méthode retourne S_OK.

Cette méthode est sécurisée pour appeler, même si votre contrôle ne prend pas en charge les points de connexion.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>  CComControl::MessageBox

Appelez cette méthode pour créer, afficher et utiliser une boîte de message.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Le texte à afficher dans la boîte de message.

*lpszCaption*<br/>
Le titre de la boîte de dialogue. Si NULL (la valeur par défaut), le titre « Erreur » est utilisé.

*nType*<br/>
Spécifie le contenu et le comportement de la boîte de dialogue. Consultez le [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) entrée dans la documentation du Kit de développement logiciel Windows pour obtenir la liste des boîtes de message différents sont accessibles. La valeur par défaut fournit un simple **OK** bouton.

### <a name="return-value"></a>Valeur de retour

Retourne une valeur entière spécifiant l’une des valeurs d’élément de menu répertoriés sous [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) dans la documentation du SDK Windows.

### <a name="remarks"></a>Notes

`MessageBox` est utile lors du développement et comme un moyen simple pour afficher un message d’erreur ou avertissement à l’utilisateur.

## <a name="see-also"></a>Voir aussi

[CWindowImpl, classe](../../atl/reference/cwindowimpl-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComControlBase, classe](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl, classe](../../atl/reference/ccomcompositecontrol-class.md)

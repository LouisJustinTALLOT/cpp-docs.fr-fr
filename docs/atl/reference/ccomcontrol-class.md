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
ms.openlocfilehash: bf0f64d8c7b8e8a3347e4c0fcad902b9e8a0ecb4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497531"
---
# <a name="ccomcontrol-class"></a>CComControl, classe

Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Classe qui implémente le contrôle.

*WinBase*<br/>
Classe de base qui implémente les fonctions de fenêtrage. La valeur par défaut est [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

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
|[CComControl::FireOnChanged](#fireonchanged)|Notifie le récepteur du conteneur qu’une propriété de contrôle a été modifiée.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Notifie le récepteur du conteneur qu’une propriété de contrôle est sur le lieu de changer et que l’objet demande au récepteur comment continuer.|
|[CComControl::MessageBox](#messagebox)|Appelez cette méthode pour créer, afficher et faire fonctionner une boîte de message.|

## <a name="remarks"></a>Notes

`CComControl`est un ensemble de fonctions d’assistance de contrôle utiles et de membres de données essentiels pour les contrôles ATL. Lorsque vous créez un contrôle standard ou DHTML à l’aide de l’Assistant contrôle ATL, l’Assistant dérivera automatiquement votre `CComControl`classe de. `CComControl`dérive la plupart de ses méthodes de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Pour plus d’informations sur la création d’un contrôle, consultez le [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md). Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

Pour une démonstration des `CComControl` méthodes et des membres de données, consultez l’exemple [CIRC](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlctl. h

##  <a name="ccomcontrol"></a>  CComControl::CComControl

Constructeur.

```
CComControl();
```

### <a name="remarks"></a>Notes

Appelle le constructeur [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) , en passant `m_hWnd` le membre de données hérité par le biais de [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface

Récupère un pointeur vers l'interface demandée.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Paramètres

*iid*<br/>
dans GUID de l’interface demandée.

*ppv*<br/>
à Pointeur vers le pointeur d’interface identifié par *IID*, ou null si l’interface est introuvable.

### <a name="remarks"></a>Notes

Gère uniquement les interfaces dans la table de mappage COM.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>  CComControl::CreateControlWindow

Par défaut, crée une fenêtre pour le contrôle en appelant `CWindowImpl::Create`.

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
dans Handle vers la fenêtre parente ou propriétaire. Un handle de fenêtre valide doit être fourni. La fenêtre de contrôle est limitée à la zone de sa fenêtre parente.

*rcPos*<br/>
dans Taille initiale et position de la fenêtre à créer.

### <a name="remarks"></a>Notes

Substituez cette méthode si vous souhaitez faire autre chose que créer une seule fenêtre, par exemple pour créer deux fenêtres, l’une d’elles devient une barre d’outils pour votre contrôle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>  CComControl::FireOnChanged

Notifie le récepteur du conteneur qu’une propriété de contrôle a été modifiée.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*dispID*<br/>
dans Identificateur de la propriété qui a changé.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si votre classe de contrôle dérive de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), cette méthode appelle [CFirePropNotifyEvent:: FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) pour notifier `IPropertyNotifySink` toutes les interfaces connectées que la propriété de contrôle spécifiée a changé. Si votre classe de contrôle ne dérive `IPropertyNotifySink`pas de, cette méthode retourne S_OK.

Cette méthode peut être appelée en toute sécurité même si votre contrôle ne prend pas en charge les points de connexion.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit

Notifie le récepteur du conteneur qu’une propriété de contrôle est sur le lieu de changer et que l’objet demande au récepteur comment continuer.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*dispID*<br/>
dans Identificateur de la propriété à modifier.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si votre classe de contrôle dérive de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), cette méthode appelle [CFirePropNotifyEvent:: FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) pour notifier `IPropertyNotifySink` toutes les interfaces connectées que la propriété de contrôle spécifiée va changer. Si votre classe de contrôle ne dérive `IPropertyNotifySink`pas de, cette méthode retourne S_OK.

Cette méthode peut être appelée en toute sécurité même si votre contrôle ne prend pas en charge les points de connexion.

### <a name="example"></a>Exemples

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>  CComControl::MessageBox

Appelez cette méthode pour créer, afficher et faire fonctionner une boîte de message.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Texte à afficher dans la boîte de message.

*lpszCaption*<br/>
Titre de la boîte de dialogue. Si la valeur est NULL (valeur par défaut), le titre «erreur» est utilisé.

*nType*<br/>
Spécifie le contenu et le comportement de la boîte de dialogue. Consultez l’entrée [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) dans la documentation de SDK Windows pour obtenir la liste des différentes boîtes de message disponibles. La valeur par défaut fournit un bouton **OK** simple.

### <a name="return-value"></a>Valeur de retour

Retourne une valeur entière spécifiant l’une des valeurs d’élément de menu listées sous [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) dans la documentation de SDK Windows.

### <a name="remarks"></a>Notes

`MessageBox`est utile pendant le développement et comme un moyen simple d’afficher un message d’erreur ou d’avertissement à l’utilisateur.

## <a name="see-also"></a>Voir aussi

[CWindowImpl, classe](../../atl/reference/cwindowimpl-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComControlBase, classe](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl, classe](../../atl/reference/ccomcompositecontrol-class.md)

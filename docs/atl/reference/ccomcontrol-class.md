---
title: Classe CComControl
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
ms.openlocfilehash: 3518de3596748fa284c1f898b69d1576903e9510
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320766"
---
# <a name="ccomcontrol-class"></a>Classe CComControl

Cette classe fournit des méthodes pour créer et gérer les contrôles ATL.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
La classe implémentant le contrôle.

*WinBase (en)*<br/>
La classe de base qui met en œuvre des fonctions de fenêtre. Défauts à [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

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
|[CComControl::FireOnChanged](#fireonchanged)|Informe l’évier du conteneur qu’une propriété de contrôle a changé.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Informe l’évier du conteneur qu’une propriété de contrôle est sur le point de changer et que l’objet demande à l’évier comment procéder.|
|[CComControl::MessageBox](#messagebox)|Appelez cette méthode pour créer, afficher et utiliser une boîte de message.|

## <a name="remarks"></a>Notes

`CComControl`est un ensemble de fonctions utiles d’aide de contrôle et de membres essentiels de données pour les contrôles ATL. Lorsque vous créez un contrôle standard ou un contrôle DHTML à l’aide `CComControl`de l’assistant de contrôle ATL, l’assistant dérive automatiquement votre classe de . `CComControl`tire la plupart de ses méthodes de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Pour plus d’informations sur la création d’un contrôle, voir le [tutoriel ATL](../../atl/active-template-library-atl-tutorial.md). Pour plus d’informations sur le assistant de projet ATL, voir l’article [Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

Pour une `CComControl` démonstration des méthodes et des membres des données, consultez l’échantillon [du CIRC.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WinBase`

[CComControlBase (en)](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="ccomcontrolccomcontrol"></a><a name="ccomcontrol"></a>CComControl::CComControl

Constructeur.

```
CComControl();
```

### <a name="remarks"></a>Notes

Appelle le constructeur [CComControlBase,](ccomcontrolbase-class.md#ccomcontrolbase) en passant le `m_hWnd` membre de données hérité par [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="ccomcontrolcontrolqueryinterface"></a><a name="controlqueryinterface"></a>CComControl::ControlQueryInterface

Récupère un pointeur vers l'interface demandée.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface demandée.

*Ppv*<br/>
[out] Un pointeur au pointeur d’interface identifié par *iid*, ou NULL si l’interface n’est pas trouvée.

### <a name="remarks"></a>Notes

Ne gère que les interfaces dans la table de carte COM.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

## <a name="ccomcontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComControl::CreateControlWindow

Par défaut, crée une fenêtre `CWindowImpl::Create`pour le contrôle en appelant .

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
[dans] Poignée à la fenêtre du parent ou du propriétaire. Une poignée de fenêtre valide doit être fournie. La fenêtre de contrôle est confinée à la zone de sa fenêtre parente.

*rcPos (en)*<br/>
[dans] La taille et la position initiales de la fenêtre à créer.

### <a name="remarks"></a>Notes

Remplacez cette méthode si vous voulez faire autre chose que de créer une seule fenêtre, par exemple, pour créer deux fenêtres, dont l’une devient une barre d’outils pour votre contrôle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

## <a name="ccomcontrolfireonchanged"></a><a name="fireonchanged"></a>CComControl::FireOnChanged

Informe l’évier du conteneur qu’une propriété de contrôle a changé.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*dispID*<br/>
[dans] Identification de la propriété qui a changé.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si votre classe de contrôle dérive [d’IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), cette méthode appelle [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) pour informer toutes les interfaces connectées `IPropertyNotifySink` que la propriété de contrôle spécifiée a changé. Si votre classe de `IPropertyNotifySink`contrôle ne dérive pas, cette méthode renvoie S_OK.

Cette méthode est sûre à appeler même si votre contrôle ne prend pas en charge les points de connexion.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

## <a name="ccomcontrolfireonrequestedit"></a><a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit

Informe l’évier du conteneur qu’une propriété de contrôle est sur le point de changer et que l’objet demande à l’évier comment procéder.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Paramètres

*dispID*<br/>
[dans] Identifiant de la propriété sur le point de changer.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Si votre classe de contrôle dérive [d’IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), cette méthode appelle [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) pour informer toutes les interfaces connectées `IPropertyNotifySink` que la propriété de contrôle spécifiée est sur le point de changer. Si votre classe de `IPropertyNotifySink`contrôle ne dérive pas, cette méthode renvoie S_OK.

Cette méthode est sûre à appeler même si votre contrôle ne prend pas en charge les points de connexion.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

## <a name="ccomcontrolmessagebox"></a><a name="messagebox"></a>CComControl::MessageBox

Appelez cette méthode pour créer, afficher et utiliser une boîte de message.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Le texte à afficher dans la boîte à messages.

*lpszCaption*<br/>
Le titre de la boîte de dialogue. Si NULL (la valeur par défaut), le titre "Erreur" est utilisé.

*nType*<br/>
Spécifie le contenu et le comportement de la boîte de dialogue. Voir l’entrée [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) dans la documentation Windows SDK pour une liste des différentes boîtes de messages disponibles. La valeur par défaut fournit un simple bouton **OK.**

### <a name="return-value"></a>Valeur de retour

Retourne une valeur d’intégrage spécifiant l’une des valeurs de l’élément de menu figurant sous [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) dans la documentation Windows SDK.

### <a name="remarks"></a>Notes

`MessageBox`est utile à la fois pendant le développement et comme un moyen facile d’afficher une erreur ou un message d’avertissement à l’utilisateur.

## <a name="see-also"></a>Voir aussi

[Classe CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe CComControlBase](../../atl/reference/ccomcontrolbase-class.md)<br/>
[Classe CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)

---
title: CComCompositeControl, classe
ms.date: 11/04/2016
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
ms.openlocfilehash: a37386c40f119c855dcb8584a72ce85c48a66381
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834737"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl, classe

Cette classe fournit les méthodes requises pour implémenter un contrôle composite.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toutes les autres interfaces que vous souhaitez prendre en charge pour votre contrôle composite.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Constructeur.|
|[CComCompositeControl :: ~ CComCompositeControl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Appelez cette méthode pour informer ou déconseiller tous les contrôles hébergés par le contrôle composite.|
|[CComCompositeControl::CalcExtent](#calcextent)|Appelez cette méthode pour calculer la taille en unités HIMETRIC de la ressource de boîte de dialogue utilisée pour héberger le contrôle composite.|
|[CComCompositeControl :: Create](#create)|Cette méthode est appelée pour créer la fenêtre de contrôle pour le contrôle composite.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Appelez cette méthode pour créer la fenêtre de contrôle et conseiller tout contrôle hébergé.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Appelez cette méthode pour définir la couleur d’arrière-plan du contrôle composite à l’aide de la couleur d’arrière-plan du conteneur.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCompositeControl :: m_hbrBackground](#m_hbrbackground)|Pinceau d'arrière-plan.|
|[CComCompositeControl :: m_hWndFocus](#m_hwndfocus)|Handle de la fenêtre qui a actuellement le focus.|

## <a name="remarks"></a>Notes

Les classes dérivées de `CComCompositeControl` la classe héritent des fonctionnalités d’un contrôle composite ActiveX. Les contrôles ActiveX dérivés de `CComCompositeControl` sont hébergés par une boîte de dialogue standard. Ces types de contrôles sont appelés contrôles composites, car ils peuvent héberger d’autres contrôles (contrôles Windows natifs et contrôles ActiveX).

`CComCompositeControl` identifie la ressource de boîte de dialogue à utiliser lors de la création du contrôle composite en recherchant un membre de données énuméré dans la classe enfant. L’IDD membre de cette classe enfant a pour valeur l’ID de ressource de la ressource de boîte de dialogue qui sera utilisée comme fenêtre du contrôle. Voici un exemple des données membres que la classe dérivée de `CComCompositeControl` doit contenir pour identifier la ressource de boîte de dialogue à utiliser pour la fenêtre du contrôle :

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> Les contrôles composites sont toujours des contrôles avec fenêtres, bien qu’ils puissent contenir des contrôles sans fenêtre.

Un contrôle implémenté par une `CComCompositeControl` classe dérivée de a un comportement de tabulation par défaut intégré. Lorsque le contrôle reçoit le focus en faisant l’objet d’un onglet dans une application conteneur, le fait d’appuyer successivement sur la touche TAB entraîne le passage du focus à travers tous les contrôles contenus du contrôle composite, puis sur le contrôle composite et sur l’élément suivant dans l’ordre de tabulation du conteneur. L’ordre de tabulation des contrôles hébergés est déterminé par la ressource de boîte de dialogue et détermine l’ordre dans lequel la tabulation aura lieu.

> [!NOTE]
> Pour que les accélérateurs fonctionnent correctement avec un `CComCompositeControl` , il est nécessaire de charger une table d’accélérateurs au fur et à mesure que le contrôle est créé, de passer le handle et le nombre d’accélérateurs dans [IOleControlImpl :: GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), et enfin de détruire la table lorsque le contrôle est libéré.

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl. h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a> CComCompositeControl::AdviseSinkMap

Appelez cette méthode pour informer ou déconseiller tous les contrôles hébergés par le contrôle composite.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Paramètres

*bAdvise*<br/>
True si tous les contrôles doivent être recommandés ; Sinon, false.

### <a name="return-value"></a>Valeur de retour

| Valeur | Description |
|--|--|
| `S_OK` | Tous les contrôles de la table de récepteurs d’événements ont été connectés ou déconnectés de leur source d’événements. |
| `E_FAIL` | Tous les contrôles de la table de récepteurs d’événements n’ont pas pu être connectés ou déconnectés correctement de leur source d’événement. |
| `E_POINTER` | Cette erreur indique généralement un problème avec une entrée dans le mappage de récepteur d’événements du contrôle ou un problème avec un argument de modèle utilisé dans une `IDispEventImpl` `IDispEventSimpleImpl` classe de base ou. |
| `CONNECT_E_ADVISELIMIT` | Le point de connexion a déjà atteint sa limite de connexions et ne peut plus en accepter. |
| `CONNECT_E_CANNOTCONNECT` | Le récepteur ne prend pas en charge l’interface requise par ce point de connexion. |
| `CONNECT_E_NOCONNECTION` | La valeur de cookie ne représente pas une connexion valide. Cette erreur indique généralement un problème avec une entrée dans le mappage de récepteur d’événements du contrôle ou un problème avec un argument de modèle utilisé dans une `IDispEventImpl` `IDispEventSimpleImpl` classe de base ou. |

### <a name="remarks"></a>Notes

L’implémentation de base de cette méthode parcourt les entrées de la table de récepteurs d’événements. Il conseille ensuite ou déconseille les points de connexion aux objets COM décrits par les entrées de récepteur de la carte de récepteurs d’événements. Cette méthode membre repose également sur le fait que la classe dérivée hérite d’une instance de `IDispEventImpl` pour chaque contrôle dans le mappage de récepteur qui doit être avisé ou non.

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a> CComCompositeControl::CalcExtent

Appelez cette méthode pour calculer la taille en unités HIMETRIC de la ressource de boîte de dialogue utilisée pour héberger le contrôle composite.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Référence à une `SIZE` structure à remplir par cette méthode.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le contrôle est hébergé par une boîte de dialogue ; Sinon, FALSe.

### <a name="remarks"></a>Notes

La taille est retournée dans le paramètre *Size* .

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a> CComCompositeControl :: Create

Cette méthode est appelée pour créer la fenêtre de contrôle pour le contrôle composite.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Handle de la fenêtre parente du contrôle.

*rcPos*<br/>
Réservé.

*dwInitParam*<br/>
Données à passer au contrôle pendant la création du contrôle. Les données transmises comme *dwInitParam* apparaissent comme paramètre LParam du message [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) , qui sera envoyé au contrôle composite lorsqu’il est créé.

### <a name="return-value"></a>Valeur renvoyée

Handle de la boîte de dialogue de contrôle composite nouvellement créée.

### <a name="remarks"></a>Notes

Cette méthode est généralement appelée pendant l’activation sur place du contrôle.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a> CComCompositeControl::CComCompositeControl

Constructeur.

```
CComCompositeControl();
```

### <a name="remarks"></a>Notes

Initialise les membres de données [CComCompositeControl :: m_hbrBackground](#m_hbrbackground) et [CComCompositeControl :: m_hWndFocus](#m_hwndfocus) à la valeur null.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a> CComCompositeControl :: ~ CComCompositeControl

Destructeur.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Notes

Supprime l’objet d’arrière-plan, s’il existe.

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a> CComCompositeControl::CreateControlWindow

Appelez cette méthode pour créer la fenêtre de contrôle et conseiller tous les contrôles hébergés.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Handle de la fenêtre parente du contrôle.

*rcPos*<br/>
Rectangle de position du contrôle composite dans les coordonnées clientes par rapport à *hwndParent*.

### <a name="return-value"></a>Valeur renvoyée

Retourne un handle vers la boîte de dialogue de contrôle composite nouvellement créée.

### <a name="remarks"></a>Notes

Cette méthode appelle [CComCompositeControl :: Create](#create) et [CComCompositeControl :: AdviseSinkMap](#advisesinkmap).

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a> CComCompositeControl :: m_hbrBackground

Pinceau d'arrière-plan.

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a> CComCompositeControl :: m_hWndFocus

Handle de la fenêtre qui a actuellement le focus.

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a> CComCompositeControl::SetBackgroundColorFromAmbient

Appelez cette méthode pour définir la couleur d’arrière-plan du contrôle composite à l’aide de la couleur d’arrière-plan du conteneur.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

## <a name="see-also"></a>Voir aussi

[CComControl, classe](../../atl/reference/ccomcontrol-class.md)<br/>
[Notions de base des contrôles composites](../../atl/atl-composite-control-fundamentals.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

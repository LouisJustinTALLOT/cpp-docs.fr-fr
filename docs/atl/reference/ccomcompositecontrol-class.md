---
title: Classe CComCompositeControl
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
ms.openlocfilehash: 700a8047ab1fa9df85c8e6530eb3eed5f29bd3d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320805"
---
# <a name="ccomcompositecontrol-class"></a>Classe CComCompositeControl

Cette classe fournit les méthodes nécessaires pour mettre en œuvre un contrôle composite.

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
|[CComCompositeControl::CComCompositeControl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Appelez cette méthode pour conseiller ou déconseiller tous les contrôles hébergés par le contrôle composite.|
|[CComCompositeControl::CalcExtent](#calcextent)|Appelez cette méthode pour calculer la taille des unités HIMETRIC de la ressource de dialogue utilisée pour héberger le contrôle composite.|
|[CComCompositeControl::Créer](#create)|Cette méthode est appelée pour créer la fenêtre de contrôle pour le contrôle composite.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Appelez cette méthode pour créer la fenêtre de contrôle et conseiller tout contrôle hébergé.|
|[CComCompositeControl::SetBackgroundColorDeAmbient](#setbackgroundcolorfromambient)|Appelez cette méthode pour définir la couleur de fond du contrôle composite en utilisant la couleur de fond du conteneur.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Pinceau d'arrière-plan.|
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|Le manche de la fenêtre qui a actuellement mise au point.|

## <a name="remarks"></a>Notes

Les classes `CComCompositeControl` issues de la classe héritent de la fonctionnalité d’un contrôle composite ActiveX. Les commandes ActiveX dérivées sont `CComCompositeControl` hébergées par une boîte de dialogue standard. Ces types de contrôles sont appelés contrôles composites parce qu’ils sont en mesure d’héberger d’autres contrôles (contrôles Windows natifs et contrôles ActiveX).

`CComCompositeControl`identifie la ressource de dialogue à utiliser dans la création du contrôle composite en recherchant un membre des données énumérés dans la classe des enfants. L’IDD membre de cette classe d’enfant est réglé à la pièce d’identité de ressource de la ressource de dialogue qui sera utilisée comme fenêtre de contrôle. Voici un exemple du membre des données `CComCompositeControl` que la classe dérivée devrait contenir pour identifier la ressource de dialogue à utiliser pour la fenêtre du contrôle :

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> Les commandes composites sont toujours des commandes vitrées, bien qu’elles puissent contenir des commandes sans fenêtre.

Un contrôle mis `CComCompositeControl`en œuvre par une classe dérivée a un comportement de tabbing par défaut intégré. Lorsque le contrôle reçoit la mise au point en étant tabbed à dans une application contenant, successivement en appuyant sur la clé TAB fera cycle la mise au point à travers tous les contrôles contenus du contrôle composite, puis hors du contrôle composite et sur l’élément suivant dans l’ordre d’onglet du conteneur. L’ordre d’onglet des commandes hébergées est déterminé par la ressource de dialogue et détermine l’ordre dans lequel le tabbing se produira.

> [!NOTE]
> Afin que les accélérateurs fonctionnent `CComCompositeControl`correctement avec un , il est nécessaire de charger une table d’accélérateur que le contrôle est créé, passer la poignée et le nombre d’accélérateurs de retour dans [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), et enfin détruire la table lorsque le contrôle est libéré.

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`WinBase`

[CComControlBase (en)](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap

Appelez cette méthode pour conseiller ou déconseiller tous les contrôles hébergés par le contrôle composite.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Paramètres

*bAdvise (en)*<br/>
Vrai si tous les contrôles doivent être conseillés; autrement faux.

### <a name="return-value"></a>Valeur de retour

|||
|-|-|
|S_OK  |Tous les contrôles dans la carte de l’évier de l’événement ont été connectés ou déconnectés de leur source d’événement avec succès.|
|E_FAIL  |Tous les contrôles de la carte de l’évier de l’événement ne peuvent pas être connectés ou déconnectés de leur source d’événement avec succès.|
|E_POINTER  |Cette erreur indique généralement un problème avec une entrée dans la carte de l’évier de l’événement du contrôle ou un problème avec un argument de modèle utilisé dans une classe ou `IDispEventImpl` `IDispEventSimpleImpl` une classe de base.|
|CONNECT_E_ADVISELIMIT  |Le point de connexion a déjà atteint sa limite de connexions et ne peut plus en accepter.|
|CONNECT_E_CANNOTCONNECT  |L’évier ne prend pas en charge l’interface requise par ce point de connexion.|
|CONNECT_E_NOCONNECTION  |La valeur du cookie ne représente pas une connexion valide. Cette erreur indique généralement un problème avec une entrée dans la carte de l’évier de l’événement du contrôle ou un problème avec un argument de modèle utilisé dans une classe ou `IDispEventImpl` `IDispEventSimpleImpl` une classe de base.|

### <a name="remarks"></a>Notes

La mise en œuvre de base de cette méthode recherche à travers les entrées dans la carte de l’évier de l’événement. Il conseille ensuite ou déconseille les points de connexion aux objets COM décrits par les entrées de la carte de l’évier de l’événement. Cette méthode membre repose également sur le fait que `IDispEventImpl` la classe dérivée d’un exemple de pour chaque contrôle dans la carte de l’évier qui doit être conseillé ou non.

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a>CComCompositeControl::CalcExtent

Appelez cette méthode pour calculer la taille des unités HIMETRIC de la ressource de dialogue utilisée pour héberger le contrôle composite.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
Une référence `SIZE` à une structure à remplir par cette méthode.

### <a name="return-value"></a>Valeur de retour

VRAI si le contrôle est hébergé par une boîte de dialogue; autrement FALSE.

### <a name="remarks"></a>Notes

La taille est retournée dans le paramètre *de taille.*

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a>CComCompositeControl::Créer

Cette méthode est appelée pour créer la fenêtre de contrôle pour le contrôle composite.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Une poignée à la fenêtre parente du contrôle.

*rcPos (en)*<br/>
Réservé.

*dwInitParam*<br/>
Données à transmettre au contrôle lors de la création de contrôle. Les données transmises sous forme *de dwInitParam* apparaîtront comme le paramètre LPARAM du message [WM_INITDIALOG,](/windows/win32/dlgbox/wm-initdialog) qui sera envoyé au contrôle composite lors de sa création.

### <a name="return-value"></a>Valeur de retour

Une poignée à la boîte de dialogue composite nouvellement créée.

### <a name="remarks"></a>Notes

Cette méthode est généralement appelée lors de l’activation sur place du contrôle.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl

Constructeur.

```
CComCompositeControl();
```

### <a name="remarks"></a>Notes

Initialise le [CComCompositeControl::m_hbrBackground](#m_hbrbackground) et [CComCompositeControl::m_hWndFocus](#m_hwndfocus) membres de données à NULL.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a>CComCompositeControl::CComCompositeControl

Destructeur.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Notes

Supprime l’objet de fond, s’il existe.

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow

Appelez cette méthode pour créer la fenêtre de contrôle et aviser les commandes hébergées.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Une poignée à la fenêtre parente du contrôle.

*rcPos (en)*<br/>
Le rectangle de position du contrôle composite dans les coordonnées du client par rapport à *hWndParent*.

### <a name="return-value"></a>Valeur de retour

Retourne une poignée à la boîte de dialogue composite nouvellement créée.

### <a name="remarks"></a>Notes

Cette méthode appelle [CComCompositeControl::Créer](#create) et [CComCompositeControl::AdviseSinkMap](#advisesinkmap).

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a>CComCompositeControl::m_hbrBackground

Pinceau d'arrière-plan.

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a>CComCompositeControl::m_hWndFocus

Le manche de la fenêtre qui a actuellement mise au point.

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorDeAmbient

Appelez cette méthode pour définir la couleur de fond du contrôle composite en utilisant la couleur de fond du conteneur.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="see-also"></a>Voir aussi

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Notions de base des contrôles composites](../../atl/atl-composite-control-fundamentals.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

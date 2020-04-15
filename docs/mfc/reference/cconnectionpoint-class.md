---
title: CConnectionPoint, classe
ms.date: 11/04/2016
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
ms.openlocfilehash: ce72c156ab31b742a42d2960923fc56afff656c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369428"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint, classe

Définit un type particulier d'interface utilisé pour communiquer avec d'autres objets OLE, appelé « point de connexion ».

## <a name="syntax"></a>Syntaxe

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|Construit un objet `CConnectionPoint`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CConnectionPoint::GetConnections](#getconnections)|Récupère tous les points de connexion dans une carte de connexion.|
|[CConnectionPoint::GetContainer](#getcontainer)|Récupère le conteneur du contrôle qui possède la carte de connexion.|
|[CConnectionPoint::GetIID](#getiid)|Récupère l’interface ID d’un point de connexion.|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Récupère le nombre maximum de points de connexion pris en charge par un contrôle.|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Récupère un pointeur à l’élément de connexion à *pos*.|
|[CConnectionPoint::GetStartPosition](#getstartposition)|Démarre une itération de carte en retournant une `GetNextConnection` valeur POSITION qui peut être passée à un appel.|
|[CConnectionPoint::OnAdvise](#onadvise)|Appelé par le cadre lors de l’établissement ou la rupture des connexions.|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Récupère un pointeur sur l’interface évier demandée.|

## <a name="remarks"></a>Notes

Contrairement aux interfaces OLE normales, qui sont utilisées pour implémenter et exposer la fonctionnalité d’un contrôle OLE, un point de connexion implémente une interface sortante qui est capable d’initier des actions sur d’autres objets, tels que les événements de tir et les notifications de changement.

Une connexion se compose de deux parties: l’objet appelant l’interface, appelée la «source», et l’objet de mise en œuvre de l’interface, appelé le «sink». En exposant un point de connexion, une source permet aux éviers d’établir des connexions à elle-même. Grâce au mécanisme de point de connexion, un objet source obtient un pointeur sur la mise en œuvre par l’évier d’un ensemble de fonctions membres. Par exemple, pour déclencher un événement implémenté par le récepteur, la source peut appeler la méthode appropriée de l'implémentation du récepteur.

Par défaut, `COleControl`une classe dérivée implémente deux points de connexion : l’un pour les événements et l’autre pour les notifications de changement de propriété. Ces connexions sont utilisées, respectivement, pour le tir d’événement et pour aviser un évier (par exemple, le conteneur du contrôle) lorsqu’une valeur de propriété a changé. Des mesures de soutien sont également fournies pour les contrôles OLE afin de mettre en œuvre des points de connexion supplémentaires. Pour chaque point de connexion supplémentaire implémenté dans votre classe de contrôle, vous devez déclarer une « pièce de connexion » qui implémente le point de connexion. Si vous implémentez un ou plusieurs points de connexion, vous devez également déclarer une seule « carte de connexion » dans votre classe de contrôle.

L’exemple suivant montre une carte de connexion `Sample` simple et un point de connexion pour le contrôle OLE, composé de deux fragments de code : la première partie déclare la carte et le point de connexion ; le second implémente cette carte et ce point. Le premier fragment est inséré dans la déclaration de la classe de contrôle, sous la section **protégée** :

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

Les macros BEGIN_CONNECTION_PART et END_CONNECTION_PART déclarent une `XSampleConnPt` classe intégrée, (dérivée de ) qui implémente ce point de `CConnectionPoint`connexion particulier. Si vous souhaitez remplacer `CConnectionPoint` les fonctions des membres ou ajouter vos propres fonctions de membre, déclarez-les entre ces deux macros. Par exemple, la macro CONNECTION_IID l’emporte sur la `CConnectionPoint::GetIID` fonction du membre lorsqu’elle est placée entre ces deux macros.

Le deuxième fragment de code est inséré dans le fichier d’implémentation (. RPC) de votre classe de contrôle. Ce code implémente la carte de `SampleConnPt`connexion, qui inclut le point de connexion supplémentaire , :

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Une fois que ces fragments de code ont été insérés, `ISampleSink` le contrôle OLE Sample expose un point de connexion pour l’interface.

En règle générale, les points de connexion prennent en charge le « multidiffusion », c’est-à-dire la possibilité de diffuser à plusieurs éviers connectés à la même interface. Le fragment de code suivant montre comment accomplir le multidiffusion en itérant à travers chaque évier sur un point de connexion :

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

Cet exemple récupère l'ensemble actuel de connexions sur le point de connexion `SampleConnPt` par un appel à `CConnectionPoint::GetConnections`. Il itère ensuite à travers `ISampleSink::SinkFunc` les connexions et fait appel à chaque connexion active.

Pour plus d’informations sur l’utilisation `CConnectionPoint`, voir l’article Points de [connexion](../../mfc/connection-points.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint

Construit un objet `CConnectionPoint`.

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint::GetConnections

Appelez cette fonction pour récupérer toutes les connexions actives pour un point de connexion.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un tableau de connexions actives (puits). Certains des pointeurs dans le tableau peut être NULL. Chaque pointeur non-NULL dans ce tableau peut être converti en toute sécurité en un pointeur à l’interface d’évier à l’aide d’un opérateur de fonte.

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint::GetContainer

Appelé par le cadre `IConnectionPointContainer` pour récupérer le point de connexion.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, un pointeur vers le conteneur; autrement NULL.

### <a name="remarks"></a>Notes

Cette fonction est généralement implémentée par la macro BEGIN_CONNECTION_PART.

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint::GetIID

Appelé par le cadre pour récupérer l’interface ID d’un point de connexion.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Valeur de retour

Une référence à l’id d’interface du point de connexion.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour retourner l’interface ID pour ce point de connexion.

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint::GetMaxConnections

Appelé par le cadre pour récupérer le nombre maximum de connexions prises en charge par le point de connexion.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximum de connexions prises en charge par le contrôle, ou -1 si aucune limite.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut renvoie -1, indiquant aucune limite.

Remplacez cette fonction si vous souhaitez limiter le nombre de éviers qui peuvent se connecter à votre contrôle.

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint::GetNextConnection

Récupère un pointeur à l’élément de connexion à *pos*.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Spécifie une référence à une `GetNextConnection` valeur POSITION retournée par un appel précédent ou [GetStartPosition.](#getstartposition)

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’élément de connexion spécifié par *pos*, ou NULL.

### <a name="remarks"></a>Notes

Cette fonction est plus utile pour itérer à travers tous les éléments de la carte de connexion. Lors de l’itération, sautez tous les NULLs retournés de cette fonction.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition

Démarre une itération de carte en retournant une valeur POSITION qui peut être passée à un appel [GetNextConnection.](#getnextconnection)

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui indique une position de départ pour itérer la carte; ou NULL si la carte est vide.

### <a name="remarks"></a>Notes

La séquence d’itération n’est pas prévisible; par conséquent, le «premier élément de la carte» n’a pas d’importance particulière.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CConnectionPoint:GetNextConnection](#getnextconnection).

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint::OnAdvise

Appelé par le cadre lorsqu’une connexion est établie ou rompue.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Paramètres

*bAdvise (en)*<br/>
VRAI, si une connexion est établie; autrement FALSE.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération.

Remplacez cette fonction si vous souhaitez une notification lorsque les éviers se connectent à votre point de connexion ou se déconnectent de votre point de connexion.

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface

Récupère un pointeur sur l’interface évier demandée.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Paramètres

*pUnkSink (en)*<br/>
L’identifiant de l’interface d’évier demandé.

*ppInterface*<br/>
Un pointeur au pointeur d’interface identifié par *pUnkSink*. Si l’objet ne prend \* pas en charge cette interface, *ppInterface* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

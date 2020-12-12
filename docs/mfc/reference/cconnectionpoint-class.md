---
description: 'En savoir plus sur : classe CConnectionPoint'
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
ms.openlocfilehash: 62525428d8f9bf5303f379140837d75e53cbb387
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227843"
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
|[CConnectionPoint :: CConnectionPoint](#cconnectionpoint)|Construit un objet `CConnectionPoint`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CConnectionPoint :: GetConnections](#getconnections)|Récupère tous les points de connexion dans un mappage de connexions.|
|[CConnectionPoint :: GetContainer](#getcontainer)|Récupère le conteneur du contrôle qui possède le mappage de connexions.|
|[CConnectionPoint :: GetIID](#getiid)|Récupère l’ID d’interface d’un point de connexion.|
|[CConnectionPoint :: GetMaxConnections](#getmaxconnections)|Récupère le nombre maximal de points de connexion pris en charge par un contrôle.|
|[CConnectionPoint :: GetNextConnection](#getnextconnection)|Récupère un pointeur vers l’élément de connexion sur *pos*.|
|[CConnectionPoint :: GetStartPosition](#getstartposition)|Démarre une itération de mappage en retournant une valeur de POSITION qui peut être passée à un `GetNextConnection` appel.|
|[CConnectionPoint :: OnAdvise](#onadvise)|Appelé par l’infrastructure lors de l’établissement ou de l’interruption des connexions.|
|[CConnectionPoint :: QuerySinkInterface](#querysinkinterface)|Récupère un pointeur vers l’interface de récepteur demandée.|

## <a name="remarks"></a>Notes

Contrairement aux interfaces OLE normales, qui permettent d’implémenter et d’exposer les fonctionnalités d’un contrôle OLE, un point de connexion implémente une interface sortante capable d’initialiser des actions sur d’autres objets, comme le déclenchement d’événements et de notifications de modifications.

Une connexion se compose de deux parties : l’objet qui appelle l’interface, appelé « source » et l’objet qui implémente l’interface, appelé « récepteur ». En exposant un point de connexion, une source permet aux récepteurs d’établir des connexions à elles-mêmes. Par le biais du mécanisme de point de connexion, un objet source obtient un pointeur vers l’implémentation du récepteur d’un ensemble de fonctions membres. Par exemple, pour déclencher un événement implémenté par le récepteur, la source peut appeler la méthode appropriée de l'implémentation du récepteur.

Par défaut, une `COleControl` classe dérivée de met en œuvre deux points de connexion : un pour les événements et un pour les notifications de modification de propriété. Ces connexions sont utilisées, respectivement, pour le déclenchement d’événements et pour la notification d’un récepteur (par exemple, le conteneur du contrôle) lorsqu’une valeur de propriété a été modifiée. La prise en charge est également fournie pour que les contrôles OLE implémentent des points de connexion supplémentaires. Pour chaque point de connexion supplémentaire implémenté dans votre classe de contrôle, vous devez déclarer une « partie de connexion » qui implémente le point de connexion. Si vous implémentez un ou plusieurs points de connexion, vous devez également déclarer une « carte de connexion » unique dans votre classe de contrôle.

L’exemple suivant illustre une carte de connexion simple et un point de connexion pour le `Sample` contrôle OLE, constitué de deux fragments de code : la première partie déclare le mappage et le point de connexion ; le second implémente ce mappage et ce point. Le premier fragment est inséré dans la déclaration de la classe de contrôle, sous la **`protected`** section :

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

Les macros BEGIN_CONNECTION_PART et END_CONNECTION_PART déclarent une classe incorporée, `XSampleConnPt` (dérivée de `CConnectionPoint` ) qui implémente ce point de connexion particulier. Si vous souhaitez substituer des `CConnectionPoint` fonctions membres, ou ajouter des fonctions membres de votre choix, déclarez-les entre ces deux macros. Par exemple, la macro CONNECTION_IID remplace la `CConnectionPoint::GetIID` fonction membre lorsqu’elle est placée entre ces deux macros.

Le deuxième fragment de code est inséré dans le fichier d’implémentation (. CPP) de votre classe de contrôle. Ce code implémente le mappage de connexions, qui comprend le point de connexion supplémentaire `SampleConnPt` :

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Une fois ces fragments de code insérés, l’exemple de contrôle OLE expose un point de connexion pour l' `ISampleSink` interface.

En règle générale, les points de connexion prennent en charge la « multidiffusion », qui est la possibilité de diffuser vers plusieurs récepteurs connectés à la même interface. Le fragment de code suivant montre comment effectuer la multidiffusion en effectuant une itération au sein de chaque récepteur sur un point de connexion :

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

Cet exemple récupère l'ensemble actuel de connexions sur le point de connexion `SampleConnPt` par un appel à `CConnectionPoint::GetConnections`. Il itère ensuite au sein des connexions et appelle `ISampleSink::SinkFunc` sur chaque connexion active.

Pour plus d’informations sur l’utilisation de `CConnectionPoint` , consultez l’article [points de connexion](../../mfc/connection-points.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a> CConnectionPoint :: CConnectionPoint

Construit un objet `CConnectionPoint`.

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a> CConnectionPoint :: GetConnections

Appelez cette fonction pour récupérer toutes les connexions actives pour un point de connexion.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un tableau de connexions actives (récepteurs). Certains des pointeurs du tableau peuvent être NULL. Chaque pointeur non NULL dans ce tableau peut être converti en toute sécurité en un pointeur vers l’interface du récepteur à l’aide d’un opérateur de cast.

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a> CConnectionPoint :: GetContainer

Appelé par l’infrastructure pour récupérer le `IConnectionPointContainer` pour le point de connexion.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, pointeur vers le conteneur ; Sinon, NULL.

### <a name="remarks"></a>Notes

Cette fonction est généralement implémentée par la macro BEGIN_CONNECTION_PART.

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a> CConnectionPoint :: GetIID

Appelé par l’infrastructure pour récupérer l’ID d’interface d’un point de connexion.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Valeur renvoyée

Référence à l’ID d’interface du point de connexion.

### <a name="remarks"></a>Notes

Substituez cette fonction pour retourner l’ID d’interface pour ce point de connexion.

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a> CConnectionPoint :: GetMaxConnections

Appelée par l’infrastructure pour récupérer le nombre maximal de connexions prises en charge par le point de connexion.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Valeur renvoyée

Le nombre maximal de connexions prises en charge par le contrôle, ou-1 si aucune limite n’est définie.

### <a name="remarks"></a>Notes

L’implémentation par défaut retourne-1, ce qui indique qu’aucune limite n’est définie.

Substituez cette fonction si vous souhaitez limiter le nombre de récepteurs qui peuvent se connecter à votre contrôle.

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a> CConnectionPoint :: GetNextConnection

Récupère un pointeur vers l’élément de connexion sur *pos*.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Spécifie une référence à une valeur de POSITION retournée par un `GetNextConnection` appel précédent ou [GetStartPosition](#getstartposition) .

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’élément de connexion spécifié par *pos*, ou null.

### <a name="remarks"></a>Notes

Cette fonction est particulièrement utile pour itérer au sein de tous les éléments dans le mappage de connexions. Lors de l’itération, ignore les valeurs NULL retournées par cette fonction.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a> CConnectionPoint :: GetStartPosition

Démarre une itération de mappage en retournant une valeur de POSITION qui peut être passée à un appel [GetNextConnection](#getnextconnection) .

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur de POSITION qui indique une position de départ pour itérer la carte ; ou NULL si le mappage est vide.

### <a name="remarks"></a>Notes

La séquence d’itération n’est pas prévisible ; par conséquent, le « premier élément du mappage » n’a pas d’importance particulière.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CConnectionPoint :: GetNextConnection](#getnextconnection).

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a> CConnectionPoint :: OnAdvise

Appelé par le Framework lorsqu’une connexion est en cours d’établissement ou de rupture.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Paramètres

*bAdvise*<br/>
TRUE si une connexion est établie ; Sinon, FALSe.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération.

Remplacez cette fonction si vous souhaitez recevoir une notification lorsque des récepteurs se connectent à votre point de connexion ou s’en déconnectent.

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a> CConnectionPoint :: QuerySinkInterface

Récupère un pointeur vers l’interface de récepteur demandée.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Paramètres

*pUnkSink*<br/>
Identificateur de l’interface du récepteur demandée.

*ppInterface*<br/>
Pointeur vers le pointeur d’interface identifié par *pUnkSink*. Si l’objet ne prend pas en charge cette interface, \* *ppInterface* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

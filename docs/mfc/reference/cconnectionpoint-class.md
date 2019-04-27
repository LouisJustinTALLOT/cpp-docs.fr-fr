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
ms.openlocfilehash: a75ce23cf55f26505c2584c3a021b654602a6a2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182278"
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
|[CConnectionPoint::GetConnections](#getconnections)|Récupère tous les points de connexion dans un mappage de connexions.|
|[CConnectionPoint::GetContainer](#getcontainer)|Récupère le conteneur du contrôle qui possède le mappage de connexions.|
|[CConnectionPoint::GetIID](#getiid)|Récupère l’ID d’interface d’un point de connexion.|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Récupère le nombre maximal de points de connexion pris en charge par un contrôle.|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Récupère un pointeur vers l’élément de la connexion à *pos*.|
|[CConnectionPoint::GetStartPosition](#getstartposition)|Démarre une itération de la carte en retournant une valeur POSITION qui peut être passée à un `GetNextConnection` appeler.|
|[CConnectionPoint::OnAdvise](#onadvise)|Appelé par l’infrastructure lors de l’établissement ou l’arrêt d’une connexion.|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Récupère un pointeur vers l’interface du récepteur demandé.|

## <a name="remarks"></a>Notes

Contrairement aux interfaces OLE normales, qui servent à implémenter et d’exposer les fonctionnalités d’un contrôle OLE, un point de connexion implémente une interface sortante qui est en mesure de lancer des actions sur d’autres objets, tels que le déclenchement d’événements et notifications de modifications.

Une connexion se compose de deux parties : l’objet qui appelle l’interface, appelé la « source » et l’objet implémentant l’interface, appelé « sink ». En exposant un point de connexion, une source permet à des récepteurs d’établir des connexions à elle-même. Via le mécanisme de point de connexion, un objet de source Obtient un pointeur vers l’implémentation du récepteur d’un ensemble de fonctions membres. Par exemple, pour déclencher un événement implémenté par le récepteur, la source peut appeler la méthode appropriée de l'implémentation du récepteur.

Par défaut, un `COleControl`-classe dérivée implémente deux points de connexion : un pour les événements et un pour la propriété des notifications de modifications. Ces connexions sont utilisées, respectivement, pour le déclenchement des événements et pour notifier un récepteur (par exemple, le conteneur du contrôle) quand une valeur de propriété a changé. Prise en charge est également fournie pour contrôles OLE implémenter les points de connexion supplémentaires. Pour chaque point de connexion supplémentaires implémentée dans votre classe de contrôle, vous devez déclarer une partie de connexion « » qui implémente le point de connexion. Si vous implémentez un ou plusieurs points de connexion, vous devez également déclarer un seul « mappage de connexions » dans votre classe de contrôle.

L’exemple suivant montre un mappage de connexions simple et un point de connexion pour le `Sample` contrôle OLE, consistant en deux fragments de code : la première partie déclare le mappage de connexions et le point ; le second implémente ce point et la carte. Le premier fragment est inséré dans la déclaration de la classe de contrôle, sous la **protégé** section :

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

Les macros BEGIN_CONNECTION_PART et END_CONNECTION_PART déclarent une classe incorporée, `XSampleConnPt` (dérivée de `CConnectionPoint`) qui implémente ce point de connexion particulier. Si vous souhaitez remplacer toutes `CConnectionPoint` fonctions membres, ou ajouter vos propres fonctions membres, déclarez-les entre ces deux macros. Par exemple, le CONNECTION_IID (macro) remplace le `CConnectionPoint::GetIID` fonction membre lorsqu’elle est placée entre ces deux macros.

Le deuxième fragment de code est inséré dans le fichier d’implémentation (. (CPP) de votre classe de contrôle. Ce code implémente le mappage de connexions, qui inclut le point de connexion supplémentaires, `SampleConnPt`:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Une fois que ces fragments de code ont été insérées, le contrôle OLE exemple expose un point de connexion pour le `ISampleSink` interface.

En règle générale, les points de connexion prennent en charge la « multidiffusion », qui est la possibilité de diffuser vers plusieurs récepteurs connectés à la même interface. Le fragment de code suivant montre comment accomplir la multidiffusion en parcourant chaque destinataire sur un point de connexion :

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

Cet exemple récupère l'ensemble actuel de connexions sur le point de connexion `SampleConnPt` par un appel à `CConnectionPoint::GetConnections`. Il effectue ensuite une itération via les connexions et appelle `ISampleSink::SinkFunc` sur chaque connexion active.

Pour plus d’informations sur l’utilisation de `CConnectionPoint`, consultez l’article [Points de connexion](../../mfc/connection-points.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="cconnectionpoint"></a>  CConnectionPoint::CConnectionPoint

Construit un objet `CConnectionPoint`.

```
CConnectionPoint();
```

##  <a name="getconnections"></a>  CConnectionPoint::GetConnections

Appelez cette fonction pour récupérer toutes les connexions actives pour un point de connexion.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un tableau de connexions actives (récepteurs). Certaines des pointeurs dans le tableau peuvent être NULL. Chaque pointeur non NULL dans ce tableau peut être converti en toute sécurité à un pointeur vers l’interface du récepteur à l’aide d’un opérateur de conversion.

##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer

Appelé par l’infrastructure pour récupérer le `IConnectionPointContainer` du point de connexion.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Valeur de retour

Si l’opération réussit, un pointeur vers le conteneur ; Sinon, NULL.

### <a name="remarks"></a>Notes

Cette fonction est généralement implémentée par le BEGIN_CONNECTION_PART (macro).

##  <a name="getiid"></a>  CConnectionPoint::GetIID

Appelé par l’infrastructure pour récupérer l’ID d’interface d’un point de connexion.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Valeur de retour

Une référence à l’ID d’interface. du point de connexion

### <a name="remarks"></a>Notes

Remplacez cette fonction pour retourner l’ID de ce point de connexion.

##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections

Appelé par l’infrastructure pour récupérer le nombre maximal de connexions prises en charge par le point de connexion.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximal de connexions prises en charge par le contrôle, ou -1 si aucune limite.

### <a name="remarks"></a>Notes

L’implémentation par défaut retourne -1, n’indiquant aucune limite.

Remplacez cette fonction si vous souhaitez limiter le nombre de récepteurs qui peuvent se connecter à votre contrôle.

##  <a name="getnextconnection"></a>  CConnectionPoint::GetNextConnection

Récupère un pointeur vers l’élément de la connexion à *pos*.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Spécifie une référence à une valeur POSITION retournée par une précédente `GetNextConnection` ou [GetStartPosition](#getstartposition) appeler.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’élément de connexion spécifié par *pos*, ou NULL.

### <a name="remarks"></a>Notes

Cette fonction est particulièrement utile pour l’itération sur tous les éléments dans le mappage de connexion. Lors de l’itération, ignorer toutes les valeurs NULL retournées à partir de cette fonction.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition

Démarre une itération de la carte en retournant une valeur POSITION qui peut être passée à un [GetNextConnection](#getnextconnection) appeler.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui indique une position de départ pour une itération de la carte ; ou NULL si le mappage est vide.

### <a name="remarks"></a>Notes

La séquence d’itération n’est pas prévisible ; Par conséquent, le « premier élément dans le mappage » n’a aucun signification particulière.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CConnectionPoint::GetNextConnection](#getnextconnection).

##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise

Appelé par le framework lorsqu’une connexion est établie ou rompu.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Paramètres

*bAdvise*<br/>
Valeur TRUE, si une connexion est établie ; Sinon, FALSE.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération.

Remplacez cette fonction si vous souhaitez une notification lorsque les récepteurs de connecter ou déconnecter votre point de connexion.

##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface

Récupère un pointeur vers l’interface du récepteur demandé.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Paramètres

*pUnkSink*<br/>
Identificateur de l’interface du récepteur demandé.

*ppInterface*<br/>
Un pointeur vers le pointeur d’interface identifié par *pUnkSink*. Si l’objet ne prend pas en charge cette interface, \* *ppInterface* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

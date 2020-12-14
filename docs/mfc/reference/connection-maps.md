---
description: 'En savoir plus sur : mappages de connexions'
title: Tables de connexions
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 61d2e7023ab97aa00952aee4786b34e60ba57af7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345249"
---
# <a name="connection-maps"></a>Tables de connexions

Les contrôles OLE peuvent exposer des interfaces à d’autres applications. Ces interfaces autorisent uniquement l’accès à partir d’un conteneur dans ce contrôle. Si un contrôle OLE veut accéder à des interfaces externes d’autres objets OLE, un point de connexion doit être établi. Ce point de connexion permet à un contrôle d’accéder en sortie à des tables de dispatch externes, telles que des tables d’événements ou des fonctions de notification.

Le bibliothèque MFC (Microsoft Foundation Class) offre un modèle de programmation qui prend en charge les points de connexion. Dans ce modèle, les « mappages de connexion » sont utilisés pour désigner des interfaces ou des points de connexion pour le contrôle OLE. Les mappages de connexions contiennent une macro pour chaque point de connexion. Pour plus d’informations sur les mappages de connexions, consultez la classe [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) .

En règle générale, un contrôle ne prend en charge que deux points de connexion : un pour les événements et un pour les notifications de propriété. Celles-ci sont implémentées par la `COleControl` classe de base et ne nécessitent pas de travail supplémentaire par le writer de contrôle. Tous les points de connexion supplémentaires que vous souhaitez implémenter dans votre classe doivent être ajoutés manuellement. Pour prendre en charge les points et les mappages de connexion, MFC fournit les macros suivantes :

### <a name="connection-map-declaration-and-demarcation"></a>Déclaration et délimitation de mappage de connexion

|Nom|Description|
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Déclare une classe incorporée qui implémente un point de connexion supplémentaire (doit être utilisé dans la déclaration de classe).|
|[END_CONNECTION_PART](#end_connection_part)|Termine la déclaration d’un point de connexion (doit être utilisé dans la déclaration de classe).|
|[CONNECTION_IID](#connection_iid)|Spécifie l’ID d’interface du point de connexion du contrôle.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Déclare qu’un mappage de connexions sera utilisé dans une classe (doit être utilisé dans la déclaration de classe).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Commence la définition d’un mappage de connexion (doit être utilisé dans l’implémentation de classe).|
|[END_CONNECTION_MAP](#end_connection_map)|Termine la définition d’un mappage de connexion (doit être utilisé dans l’implémentation de classe).|
|[CONNECTION_PART](#connection_part)|Spécifie un point de connexion dans le mappage de connexion du contrôle.|

Les fonctions suivantes aident un récepteur à établir et à déconnecter une connexion à l’aide de points de connexion :

### <a name="initializationtermination-of-connection-points"></a>Initialisation/arrêt des points de connexion

|Nom|Description|
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Établit une connexion entre une source et un récepteur.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Rompt une connexion entre une source et un récepteur.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a> BEGIN_CONNECTION_PART

Utilisez la macro BEGIN_CONNECTION_PART pour commencer la définition de points de connexion supplémentaires au-delà des points de connexion de notification d’événement et de propriété.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Spécifie le nom de la classe de contrôle dont le point de connexion est.

*localClass*<br/>
Spécifie le nom de la classe locale qui implémente le point de connexion.

### <a name="remarks"></a>Notes

Dans le fichier de déclaration (. h) qui définit les fonctions membres pour votre classe, démarrez le point de connexion avec la macro BEGIN_CONNECTION_PART, ajoutez la macro CONNECTION_IID et toutes les autres fonctions membres que vous souhaitez implémenter, puis complétez la carte de point de connexion avec la macro END_CONNECTION_PART.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="end_connection_part"></a><a name="end_connection_part"></a> END_CONNECTION_PART

Termine la déclaration de votre point de connexion.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Paramètres

*localClass*<br/>
Spécifie le nom de la classe locale qui implémente le point de connexion.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="connection_iid"></a><a name="connection_iid"></a> CONNECTION_IID

Utilisez entre les macros BEGIN_CONNECTION_PART et END_CONNECTION_PART pour définir un ID d’interface pour un point de connexion pris en charge par votre contrôle OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
ID d’interface de l’interface appelée par le point de connexion.

### <a name="remarks"></a>Notes

L’argument *IID* est un ID d’interface utilisé pour identifier l’interface que le point de connexion appellera sur ses récepteurs connectés. Par exemple :

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

spécifie un point de connexion qui appelle l' `ISinkInterface` interface.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a> DECLARE_CONNECTION_MAP

Chaque `COleControl` classe dérivée de votre programme peut fournir un mappage de connexions pour spécifier des points de connexion supplémentaires pris en charge par votre contrôle.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Notes

Si votre contrôle prend en charge des points supplémentaires, utilisez la macro DECLARE_CONNECTION_MAP à la fin de votre déclaration de classe. Ensuite, dans le fichier. cpp qui définit les fonctions membres de la classe, utilisez la macro BEGIN_CONNECTION_MAP, CONNECTION_PART macros pour chacun des points de connexion du contrôle, et la macro END_CONNECTION_MAP pour déclarer la fin du mappage de connexions.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a> BEGIN_CONNECTION_MAP

Chaque `COleControl` classe dérivée de votre programme peut fournir un mappage de connexions pour spécifier les points de connexion que votre contrôle prendra en charge.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Spécifie le nom de la classe de contrôle dont est mappée la connexion.

*theBase*<br/>
Spécifie le nom de la classe de base de *les*.

### <a name="remarks"></a>Notes

Dans l’implémentation (. CPP) qui définit les fonctions membres pour votre classe, démarrez la carte de connexion avec la macro BEGIN_CONNECTION_MAP, puis ajoutez des entrées de macro pour chacun de vos points de connexion à l’aide de la macro [CONNECTION_PART](#connection_part) . Enfin, complétez la carte de connexion avec la macro [END_CONNECTION_MAP](#end_connection_map) .

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="end_connection_map"></a><a name="end_connection_map"></a> END_CONNECTION_MAP

Termine la définition de votre mappage de connexion.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="connection_part"></a><a name="connection_part"></a> CONNECTION_PART

Mappe un point de connexion pour votre contrôle OLE à un ID d’interface spécifique.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Spécifie le nom de la classe de contrôle dont le point de connexion est.

*vaut*<br/>
ID d’interface de l’interface appelée par le point de connexion.

*localClass*<br/>
Spécifie le nom de la classe locale qui implémente le point de connexion.

### <a name="remarks"></a>Notes

Par exemple :

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implémente un mappage de connexions, avec un point de connexion, qui appelle l' `IID_ISinkInterface` interface.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a> AfxConnectionAdvise

Appelez cette fonction pour établir une connexion entre une source, spécifiée par *pUnkSrc* et un récepteur, spécifié par *pUnkSink*.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>Paramètres

*pUnkSrc*<br/>
Pointeur vers l’objet qui appelle l’interface.

*pUnkSink*<br/>
Pointeur vers l’objet qui implémente l’interface.

*vaut*<br/>
ID d’interface de la connexion.

*bRefCount*<br/>
TRUE indique que la création de la connexion doit entraîner l’incrémentation du décompte de références de *pUnkSink* . FALSe indique que le décompte de références ne doit pas être incrémenté.

*pdwCookie*<br/>
Pointeur vers une valeur DWORD dans laquelle un identificateur de connexion est retourné. Cette valeur doit être transmise en tant que paramètre *dwCookie* à lors de la déconnexion de `AfxConnectionUnadvise` la connexion.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si une connexion a été établie ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a> AfxConnectionUnadvise

Appelez cette fonction pour déconnecter une connexion entre une source, spécifiée par *pUnkSrc* et un récepteur, spécifié par *pUnkSink*.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*pUnkSrc*<br/>
Pointeur vers l’objet qui appelle l’interface.

*pUnkSink*<br/>
Pointeur vers l’objet qui implémente l’interface.

*vaut*<br/>
ID d’interface de l’interface de point de connexion.

*bRefCount*<br/>
TRUE indique que la déconnexion de la connexion doit entraîner la décrémentation du décompte de références de *pUnkSink* . FALSe indique que le décompte de références ne doit pas être décrémenté.

*dwCookie*<br/>
Identificateur de connexion retourné par `AfxConnectionAdvise` .

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si une connexion a été déconnectée ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

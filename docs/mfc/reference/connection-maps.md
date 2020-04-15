---
title: Tables de connexions
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: 947cd09023ef4028a32db8e2e4e8b33f7e04e0dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374801"
---
# <a name="connection-maps"></a>Tables de connexions

Les contrôles OLE sont capables d’exposer les interfaces à d’autres applications. Ces interfaces ne permettent l’accès qu’à partir d’un conteneur dans ce contrôle. Si un contrôle OLE veut accéder aux interfaces externes d’autres objets OLE, un point de connexion doit être établi. Ce point de connexion permet un contrôle sortant accès à des cartes de répartition externes, telles que des cartes d’événements ou des fonctions de notification.

La Microsoft Foundation Class Library offre un modèle de programmation qui prend en charge les points de connexion. Dans ce modèle, les « cartes de connexion » sont utilisées pour désigner des interfaces ou des points de connexion pour le contrôle OLE. Les cartes de connexion contiennent une macro pour chaque point de connexion. Pour plus d’informations sur les cartes de connexion, consultez la classe [CConnectionPoint.](../../mfc/reference/cconnectionpoint-class.md)

En règle générale, un contrôle ne prendra en charge que deux points de connexion : l’un pour les événements et l’autre pour les notifications de propriété. Ceux-ci sont `COleControl` mis en œuvre par la classe de base et ne nécessitent aucun travail supplémentaire par l’auteur de contrôle. Tous les points de connexion supplémentaires que vous souhaitez implémenter dans votre classe doivent être ajoutés manuellement. Pour prendre en charge les cartes et les points de connexion, MFC fournit les macros suivantes :

### <a name="connection-map-declaration-and-demarcation"></a>Déclaration et démarcation de la carte de connexion

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Déclare une classe intégrée qui implémente un point de connexion supplémentaire (doit être utilisé dans la déclaration de classe).|
|[END_CONNECTION_PART](#end_connection_part)|Termine la déclaration d’un point de connexion (doit être utilisée dans la déclaration de classe).|
|[CONNECTION_IID](#connection_iid)|Spécifie l’interface ID du point de connexion du contrôle.|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Déclare qu’une carte de connexion sera utilisée dans une classe (doit être utilisée dans la déclaration de classe).|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Commence la définition d’une carte de connexion (doit être utilisée dans la mise en œuvre de la classe).|
|[END_CONNECTION_MAP](#end_connection_map)|Termine la définition d’une carte de connexion (doit être utilisée dans la mise en œuvre de la classe).|
|[CONNECTION_PART](#connection_part)|Spécifie un point de connexion dans la carte de connexion du contrôle.|

Les fonctions suivantes aident un évier à établir et à déconnecter une connexion à l’aide de points de connexion :

### <a name="initializationtermination-of-connection-points"></a>Initialisation/résiliation des points de connexion

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|Établit un lien entre une source et un évier.|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Brise une connexion entre une source et un évier.|

## <a name="begin_connection_part"></a><a name="begin_connection_part"></a>BEGIN_CONNECTION_PART

Utilisez la macro BEGIN_CONNECTION_PART pour commencer la définition de points de connexion supplémentaires au-delà des points de connexion de l’événement et de la notification de propriété.

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Spécifie le nom de la classe de contrôle dont il s’agit de point de connexion.

*LocalClass (en)*<br/>
Spécifie le nom de la classe locale qui implémente le point de connexion.

### <a name="remarks"></a>Notes

Dans le fichier de déclaration (.h) qui définit les fonctions des membres pour votre classe, commencez le point de connexion avec le BEGIN_CONNECTION_PART macro, puis ajoutez le CONNECTION_IID macro et toutes les autres fonctions membres que vous souhaitez implémenter, et complétez la carte de point de connexion avec la macro END_CONNECTION_PART.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="end_connection_part"></a><a name="end_connection_part"></a>END_CONNECTION_PART

Termine la déclaration de votre point de connexion.

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>Paramètres

*LocalClass (en)*<br/>
Spécifie le nom de la classe locale qui implémente le point de connexion.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="connection_iid"></a><a name="connection_iid"></a>CONNECTION_IID

Utilisez entre les BEGIN_CONNECTION_PART et END_CONNECTION_PART macros pour définir un ID d’interface pour un point de connexion pris en charge par votre contrôle OLE.

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
L’interface ID de l’interface appelée par le point de connexion.

### <a name="remarks"></a>Notes

*L’argument iid* est une interface ID utilisé pour identifier l’interface que le point de connexion fera appel à ses éviers connectés. Par exemple :

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

spécifie un point `ISinkInterface` de connexion qui appelle l’interface.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="declare_connection_map"></a><a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP

Chaque `COleControl`classe dérivée de votre programme peut fournir une carte de connexion pour spécifier des points de connexion supplémentaires que votre contrôle prend en charge.

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Notes

Si votre contrôle prend en charge des points supplémentaires, utilisez la macro DECLARE_CONNECTION_MAP à la fin de votre déclaration de classe. Ensuite, dans le fichier .cpp qui définit les fonctions du membre pour la classe, utilisez le BEGIN_CONNECTION_MAP macro, CONNECTION_PART macros pour chacun des points de connexion du contrôle, et le END_CONNECTION_MAP macro pour déclarer la fin de la carte de connexion.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="begin_connection_map"></a><a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP

Chaque `COleControl`classe dérivée de votre programme peut fournir une carte de connexion pour spécifier les points de connexion que votre contrôle prendra en charge.

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Spécifie le nom de la classe de contrôle dont il s’agit de la carte de connexion.

*la Base*<br/>
Spécifie le nom de la classe de base de *la Classe*.

### <a name="remarks"></a>Notes

Dans la mise en œuvre (. Fichier CPP) qui définit les fonctions des membres pour votre classe, démarrez la carte de connexion avec la BEGIN_CONNECTION_MAP macro, puis ajoutez des entrées macro pour chacun de vos points de connexion en utilisant la [macro CONNECTION_PART.](#connection_part) Enfin, complétez la carte de connexion avec la [macro END_CONNECTION_MAP.](#end_connection_map)

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="end_connection_map"></a><a name="end_connection_map"></a>END_CONNECTION_MAP

Termine la définition de votre carte de connexion.

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="connection_part"></a><a name="connection_part"></a>CONNECTION_PART

Cartographiez un point de connexion pour votre contrôle OLE à un ID d’interface spécifique.

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Spécifie le nom de la classe de contrôle dont il s’agit de point de connexion.

*Iid*<br/>
L’interface ID de l’interface appelée par le point de connexion.

*LocalClass (en)*<br/>
Spécifie le nom de la classe locale qui implémente le point de connexion.

### <a name="remarks"></a>Notes

Par exemple :

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

implémente une carte de connexion, `IID_ISinkInterface` avec un point de connexion, qui appelle l’interface .

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="afxconnectionadvise"></a><a name="afxconnectionadvise"></a>AfxConnectionAdvise

Appelez cette fonction pour établir une connexion entre une source, spécifiée par *pUnkSrc*, et un évier, spécifié par *pUnkSink*.

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>Paramètres

*pUnkSrc (en)*<br/>
Un pointeur vers l’objet qui appelle l’interface.

*pUnkSink (en)*<br/>
Un pointeur sur l’objet qui implémente l’interface.

*Iid*<br/>
L’interface ID de la connexion.

*bRefCount (en)*<br/>
TRUE indique que la création de la connexion devrait entraîner l’incrémentation du nombre de références de *pUnkSink.* FALSE indique que le nombre de références ne doit pas être incrémenté.

*pdwCookie*<br/>
Un pointeur vers un DWORD où un identifiant de connexion est retourné. Cette valeur doit être adoptée comme paramètre `AfxConnectionUnadvise` *dwCookie* à lors de la déconnexion de la connexion.

### <a name="return-value"></a>Valeur de retour

Nonzero si une connexion a été établie; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="afxconnectionunadvise"></a><a name="afxconnectionunadvise"></a>AfxConnectionUnadvise

Appelez cette fonction pour déconnecter une connexion entre une source, spécifiée par *pUnkSrc*, et un évier, spécifié par *pUnkSink*.

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>Paramètres

*pUnkSrc (en)*<br/>
Un pointeur vers l’objet qui appelle l’interface.

*pUnkSink (en)*<br/>
Un pointeur sur l’objet qui implémente l’interface.

*Iid*<br/>
L’interface ID de l’interface de point de connexion.

*bRefCount (en)*<br/>
TRUE indique que la déconnexion de la connexion devrait entraîner la diminution du nombre de références de *pUnkSink.* FALSE indique que le nombre de références ne doit pas être décrète.

*dwCookie*<br/>
L’identifiant de `AfxConnectionAdvise`connexion retourné par .

### <a name="return-value"></a>Valeur de retour

Nonzero si une connexion a été déconnectée; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

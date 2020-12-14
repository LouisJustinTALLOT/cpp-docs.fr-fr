---
description: 'En savoir plus sur : tables de récepteurs d’événements'
title: Tables de récepteurs d'événements
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: df18cdbba849ff0c8d7be5b038f997b6cc5df849
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219835"
---
# <a name="event-sink-maps"></a>Tables de récepteurs d'événements

Lorsqu’un contrôle OLE incorporé déclenche un événement, le conteneur du contrôle reçoit l’événement à l’aide d’un mécanisme, appelé « mappage de récepteur d’événements », fourni par MFC. Ce mappage de récepteurs d’événements désigne les fonctions de gestionnaire pour chaque événement spécifique, ainsi que les paramètres de ces événements. Pour plus d’informations sur les tables de récepteurs d’événements, consultez l’article [conteneurs de contrôles ActiveX](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Tables de récepteurs d'événements

|Nom|Description|
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Démarre la définition d’une table de récepteurs d’événements.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Déclare une table de récepteurs d’événements.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Termine la définition d’une table de récepteurs d’événements.|
|[ON_EVENT](#on_event)|Définit un gestionnaire d’événements pour un événement spécifique.|
|[ON_EVENT_RANGE](#on_event_range)|Définit un gestionnaire d’événements pour un événement spécifique déclenché à partir d’un jeu de contrôles OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Reçoit les événements déclenchés par le contrôle avant qu’ils ne soient gérés par le conteneur du contrôle.|
|[ON_PROPNOTIFY](#on_propnotify)|Définit un gestionnaire pour gérer les notifications de propriété à partir d’un contrôle OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Définit un gestionnaire pour gérer les notifications de propriété à partir d’un jeu de contrôles OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Reçoit des notifications de propriété envoyées par le contrôle avant qu’elles ne soient gérées par le conteneur du contrôle.|

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a> BEGIN_EVENTSINK_MAP

Commence la définition de votre mappage de récepteur d’événements.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Spécifie le nom de la classe de contrôle dont se trouve le mappage du récepteur d’événements.

*baseClass*<br/>
Spécifie le nom de la classe de base de *les*.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (. cpp) qui définit les fonctions membres pour votre classe, démarrez le mappage du récepteur d’événements avec la macro BEGIN_EVENTSINK_MAP, puis ajoutez des entrées de macro pour chaque événement à notifier de et complétez le mappage du récepteur d’événements avec la macro END_EVENTSINK_MAP.

Pour plus d’informations sur les tables de récepteurs d’événements et les conteneurs de contrôles OLE, consultez l’article [conteneurs de contrôles ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a> DECLARE_EVENTSINK_MAP

Un conteneur OLE peut fournir un mappage de récepteur d’événements pour spécifier les événements auxquels votre conteneur sera notifié.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Notes

Utilisez la macro DECLARE_EVENTSINK_MAP à la fin de votre déclaration de classe. Puis, dans la. CPP qui définit les fonctions membres de la classe, utilisez la macro BEGIN_EVENTSINK_MAP, les entrées de macro pour chacun des événements à notifier et la macro END_EVENTSINK_MAP pour déclarer la fin de la liste de récepteurs d’événements.

Pour plus d’informations sur les tables de récepteurs d’événements, consultez l’article [conteneurs de contrôles ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Spécifications

  **En-tête** AFXWIN. h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a> END_EVENTSINK_MAP

Termine la définition de votre mappage de récepteur d’événements.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="on_event"></a><a name="on_event"></a> ON_EVENT

Utilisez la macro ON_EVENT pour définir une fonction de gestionnaire d’événements pour un événement déclenché par un contrôle OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Classe à laquelle ce mappage de récepteur d’événements appartient.

*id*<br/>
ID de contrôle du contrôle OLE.

*égal*<br/>
ID de dispatch de l’événement déclenché par le contrôle.

*pfnHandler*<br/>
Pointeur vers une fonction membre qui gère l’événement. Cette fonction doit avoir un type de retour BOOL et des types de paramètres qui correspondent aux paramètres de l’événement (consultez *vtsParams*). La fonction doit retourner la valeur TRUE pour indiquer que l’événement a été géré ; Sinon, FALSe.

*vtsParams*<br/>
Séquence de **VTS_** constantes qui spécifie les types des paramètres de l’événement. Il s’agit des mêmes constantes que celles utilisées dans les entrées de la table de dispatch, par exemple DISP_FUNCTION.

### <a name="remarks"></a>Notes

L’argument *vtsParams* est une liste de valeurs séparées par des espaces des constantes **VTS_** . Une ou plusieurs de ces valeurs, séparées par des espaces (et non par des virgules), spécifient la liste de paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

spécifie une liste contenant un entier Short suivi d’un BOOL.

Pour obtenir la liste des constantes de **VTS_** , consultez [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="on_event_range"></a><a name="on_event_range"></a> ON_EVENT_RANGE

Utilisez la macro ON_EVENT_RANGE pour définir une fonction de gestionnaire d’événements pour un événement déclenché par un contrôle OLE ayant un ID de contrôle dans une plage contiguë d’ID.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Classe à laquelle ce mappage de récepteur d’événements appartient.

*idFirst*<br/>
ID de contrôle du premier contrôle OLE de la plage.

*idLast*<br/>
ID de contrôle du dernier contrôle OLE de la plage.

*égal*<br/>
ID de dispatch de l’événement déclenché par le contrôle.

*pfnHandler*<br/>
Pointeur vers une fonction membre qui gère l’événement. Cette fonction doit avoir un type de retour BOOL, un premier paramètre de type UINT (pour l’ID de contrôle) et des types de paramètres supplémentaires qui correspondent aux paramètres de l’événement (consultez *vtsParams*). La fonction doit retourner la valeur TRUE pour indiquer que l’événement a été géré ; Sinon, FALSe.

*vtsParams*<br/>
Séquence de **VTS_** constantes qui spécifie les types des paramètres de l’événement. La première constante doit être de type VTS_I4, pour l’ID de contrôle. Il s’agit des mêmes constantes que celles utilisées dans les entrées de la table de dispatch, par exemple DISP_FUNCTION.

### <a name="remarks"></a>Notes

L’argument *vtsParams* est une liste de valeurs séparées par des espaces des constantes **VTS_** . Une ou plusieurs de ces valeurs, séparées par des espaces (et non par des virgules), spécifient la liste de paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

spécifie une liste contenant un entier Short suivi d’un BOOL.

Pour obtenir la liste des constantes de **VTS_** , consultez [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Exemple

L’exemple suivant montre un gestionnaire d’événements, pour l’événement MouseDown, implémenté pour trois contrôles (IDC_MYCTRL1 à IDC_MYCTRL3). La fonction de gestionnaire d’événements, `OnRangeMouseDown` , est déclarée dans le fichier d’en-tête de la classe dialog ( `CMyDlg` ) comme suit :

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Le code ci-dessous est défini dans le fichier d’implémentation de la classe dialog.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a> ON_EVENT_REFLECT

La macro ON_EVENT_REFLECT, lorsqu’elle est utilisée dans le mappage de récepteur d’événements de la classe wrapper d’un contrôle OLE, reçoit les événements déclenchés par le contrôle avant qu’ils ne soient gérés par le conteneur du contrôle.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Classe à laquelle ce mappage de récepteur d’événements appartient.

*égal*<br/>
ID de dispatch de l’événement déclenché par le contrôle.

*pfnHandler*<br/>
Pointeur vers une fonction membre qui gère l’événement. Cette fonction doit avoir un type de retour BOOL et des types de paramètres qui correspondent aux paramètres de l’événement (consultez *vtsParams*). La fonction doit retourner la valeur TRUE pour indiquer que l’événement a été géré ; Sinon, FALSe.

*vtsParams*<br/>
Séquence de **VTS_** constantes qui spécifie les types des paramètres de l’événement. Il s’agit des mêmes constantes que celles utilisées dans les entrées de la table de dispatch, par exemple DISP_FUNCTION.

### <a name="remarks"></a>Notes

L’argument *vtsParams* est une liste de valeurs séparées par des espaces des constantes **VTS_** .

Une ou plusieurs de ces valeurs, séparées par des espaces (et non par des virgules), spécifient la liste de paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

spécifie une liste contenant un entier Short suivi d’un BOOL.

Pour obtenir la liste des constantes de **VTS_** , consultez [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="on_propnotify"></a><a name="on_propnotify"></a> ON_PROPNOTIFY

Utilisez la macro ON_PROPNOTIFY pour définir une entrée de mappage de récepteur d’événements pour gérer les notifications de propriété à partir d’un contrôle OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Classe à laquelle ce mappage de récepteur d’événements appartient.

*id*<br/>
ID de contrôle du contrôle OLE.

*égal*<br/>
ID de dispatch de la propriété impliquée dans la notification.

*pfnRequest*<br/>
Pointeur vers une fonction membre qui gère la `OnRequestEdit` notification pour cette propriété. Cette fonction doit avoir un type de retour BOOL et un paramètre **bool** <strong>\*</strong> . Cette fonction doit affecter la valeur TRUE au paramètre pour autoriser la modification de la propriété et FALSe pour l’interdire. La fonction doit retourner la valeur TRUE pour indiquer que la notification a été gérée ; Sinon, FALSe.

*pfnChanged*<br/>
Pointeur vers une fonction membre qui gère la `OnChanged` notification pour cette propriété. La fonction doit avoir un type de retour BOOL et un paramètre UINT. La fonction doit retourner la valeur TRUE pour indiquer que la notification a été gérée ; Sinon, FALSe.

### <a name="remarks"></a>Notes

L’argument *vtsParams* est une liste de valeurs séparées par des espaces des constantes **VTS_** . Une ou plusieurs de ces valeurs, séparées par des espaces (et non par des virgules), spécifient la liste de paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

spécifie une liste contenant un entier Short suivi d’un BOOL.

Pour obtenir la liste des constantes de **VTS_** , consultez [EVENT_CUSTOM](event-maps.md#event_custom).

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a> ON_PROPNOTIFY_RANGE

Utilisez la macro ON_PROPNOTIFY_RANGE pour définir une entrée de mappage de récepteur d’événements pour gérer les notifications de propriété à partir de n’importe quel contrôle OLE ayant un ID de contrôle dans une plage contiguë d’ID.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Classe à laquelle ce mappage de récepteur d’événements appartient.

*idFirst*<br/>
ID de contrôle du premier contrôle OLE de la plage.

*idLast*<br/>
ID de contrôle du dernier contrôle OLE de la plage.

*égal*<br/>
ID de dispatch de la propriété impliquée dans la notification.

*pfnRequest*<br/>
Pointeur vers une fonction membre qui gère la `OnRequestEdit` notification pour cette propriété. Cette fonction doit avoir un `BOOL` type de retour et `UINT` des `BOOL*` paramètres et. La fonction doit affecter la valeur TRUE au paramètre pour autoriser la modification de la propriété et FALSe pour l’interdire. La fonction doit retourner la valeur TRUE pour indiquer que la notification a été gérée ; Sinon, FALSe.

*pfnChanged*<br/>
Pointeur vers une fonction membre qui gère la `OnChanged` notification pour cette propriété. La fonction doit avoir un `BOOL` type de retour et un `UINT` paramètre. La fonction doit retourner la valeur TRUE pour indiquer que la notification a été gérée ; Sinon, FALSe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a> ON_PROPNOTIFY_REFLECT

La macro ON_PROPNOTIFY_REFLECT, lorsqu’elle est utilisée dans le mappage de récepteur d’événements de la classe wrapper d’un contrôle OLE, reçoit les notifications de propriété envoyées par le contrôle avant qu’elles ne soient gérées par le conteneur du contrôle.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Classe à laquelle ce mappage de récepteur d’événements appartient.

*égal*<br/>
ID de dispatch de la propriété impliquée dans la notification.

*pfnRequest*<br/>
Pointeur vers une fonction membre qui gère la `OnRequestEdit` notification pour cette propriété. Cette fonction doit avoir un type de retour BOOL et un paramètre **bool** <strong>\*</strong> . Cette fonction doit affecter la valeur TRUE au paramètre pour autoriser la modification de la propriété et FALSe pour l’interdire. La fonction doit retourner la valeur TRUE pour indiquer que la notification a été gérée ; Sinon, FALSe.

*pfnChanged*<br/>
Pointeur vers une fonction membre qui gère la `OnChanged` notification pour cette propriété. La fonction doit avoir un type de retour BOOL et aucun paramètre. La fonction doit retourner la valeur TRUE pour indiquer que la notification a été gérée ; Sinon, FALSe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

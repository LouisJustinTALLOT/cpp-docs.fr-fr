---
title: Tables de récepteurs d'événements
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: aeec0acad4531e1ef0933388bbee728193853611
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612219"
---
# <a name="event-sink-maps"></a>Tables de récepteurs d'événements

Lorsqu’un contrôle OLE incorporé déclenche un événement, le conteneur du contrôle reçoit l’événement à l’aide d’un mécanisme, appelé « table d’événements récepteur, « fournie par MFC. Cette table de récepteur d’événements désigne les fonctions du gestionnaire pour chaque événement spécifique, ainsi que les paramètres de ces événements. Pour plus d’informations sur les tables de récepteurs d’événements, consultez l’article [conteneurs de contrôles ActiveX](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Tables de récepteurs d'événements

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Démarre la définition d’une table de récepteur d’événements.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Déclare une table de récepteur d’événements.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Termine la définition d’une table de récepteur d’événements.|
|[ON_EVENT](#on_event)|Définit un gestionnaire d’événements pour un événement spécifique.|
|[ON_EVENT_RANGE](#on_event_range)|Définit un gestionnaire d’événements pour un événement particulier déclenché à partir d’un ensemble de contrôles OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Reçoit les événements déclenchés par le contrôle avant qu’ils sont gérés par le conteneur du contrôle.|
|[ON_PROPNOTIFY](#on_propnotify)|Définit un gestionnaire pour la gestion des notifications de propriété à partir d’un contrôle OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Définit un gestionnaire pour la gestion des notifications de propriété à partir d’un ensemble de contrôles OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Reçoit des notifications de propriété envoyées par le contrôle avant qu’ils sont gérés par le conteneur du contrôle.|

##  <a name="begin_eventsink_map"></a>  BEGIN_EVENTSINK_MAP

Commence la définition de votre table de récepteur d’événements.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Spécifie le nom de la classe de contrôle du récepteur d’événement dont le mapper.

*baseClass*<br/>
Spécifie le nom de la classe de base de *theClass*.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (.cpp) qui définit les fonctions membres pour votre classe, démarrer la table de récepteur d’événements avec le begin_eventsink_map (macro), puis ajouter des entrées de macro pour chaque événement d’être averti de terminer la table de récepteur d’événements avec l’END_EVENTSINK_MAP (macro).

Pour plus d’informations sur les tables de récepteurs d’événements et des conteneurs de contrôles OLE, consultez l’article [conteneurs de contrôles ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp.h

##  <a name="declare_eventsink_map"></a>  DECLARE_EVENTSINK_MAP

Un conteneur OLE peut fournir une table de récepteur d’événements pour spécifier les événements de que votre conteneur sera averti.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Notes

Utilisez le declare_eventsink_map (macro) à la fin de votre déclaration de classe. Ensuite, dans le. Fichier CPP qui définit les fonctions membres pour la classe, utiliser le begin_eventsink_map (macro), les entrées de la macro pour chacun des événements de notification des et l’END_EVENTSINK_MAP (macro) pour déclarer la fin de la liste de récepteur d’événements.

Pour plus d’informations sur les tables de récepteurs d’événements, consultez l’article [conteneurs de contrôles ActiveX](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxwin.h

##  <a name="end_eventsink_map"></a>  END_EVENTSINK_MAP

Met fin à la définition de votre table de récepteur d’événements.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp.h

##  <a name="on_event"></a>  ON_EVENT

Utilisez la macro ON_EVENT pour définir une fonction de gestionnaire d’événements pour un événement déclenché par un contrôle OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
La classe à laquelle appartient cette table de récepteur d’événements.

*ID*<br/>
L’ID de contrôle du contrôle OLE.

*dispid*<br/>
L’ID de dispatch de l’événement déclenché par le contrôle.

*pfnHandler*<br/>
Pointeur vers une fonction membre qui gère l’événement. Cette fonction doit avoir une valeur Booléenne en type de retour et les types de paramètres qui correspondent aux paramètres de l’événement (voir *vtsParams*). La fonction doit retourner TRUE pour indiquer que l’événement a été géré ; Sinon, FALSE.

*vtsParams*<br/>
Une séquence de **VTS_** constantes qui spécifie les types des paramètres de l’événement. Il s’agit de l’une des constantes mêmes qui sont utilisés dans les entrées de mappage de répartition comme DISP_FUNCTION.

### <a name="remarks"></a>Notes

Le *vtsParams* argument est une liste séparée par des espaces des valeurs à partir de la **VTS_** constantes. Un ou plusieurs de ces valeurs séparées par des espaces (non par des virgules) spécifie la liste des paramètres de la fonction. Exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Spécifie une liste contenant un entier court suivi d’une valeur Booléenne.

Pour obtenir la liste de la **VTS_** constantes, consultez [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp.h

##  <a name="on_event_range"></a>  ON_EVENT_RANGE

Utilisez l’on_event_range (macro) pour définir une fonction de gestionnaire d’événements pour un événement déclenché par n’importe quel contrôle OLE ayant un ID de contrôle dans une plage contiguë de codes.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
La classe à laquelle appartient cette table de récepteur d’événements.

*idFirst*<br/>
L’ID de contrôle du premier contrôle OLE dans la plage.

*idLast*<br/>
L’ID de contrôle du dernier contrôle OLE dans la plage.

*dispid*<br/>
L’ID de dispatch de l’événement déclenché par le contrôle.

*pfnHandler*<br/>
Pointeur vers une fonction membre qui gère l’événement. Cette fonction doit avoir une valeur Booléenne en type de retour, un premier paramètre de type UINT (l’ID de contrôle) et les types de paramètres supplémentaires qui correspondent aux paramètres de l’événement (voir *vtsParams*). La fonction doit retourner TRUE pour indiquer que l’événement a été géré ; Sinon, FALSE.

*vtsParams*<br/>
Une séquence de **VTS_** constantes qui spécifie les types des paramètres de l’événement. La première constante doit être de type VTS_I4, pour l’ID de contrôle. Il s’agit de l’une des constantes mêmes qui sont utilisés dans les entrées de mappage de répartition comme DISP_FUNCTION.

### <a name="remarks"></a>Notes

Le *vtsParams* argument est une liste séparée par des espaces des valeurs à partir de la **VTS_** constantes. Un ou plusieurs de ces valeurs séparées par des espaces (non par des virgules) spécifie la liste des paramètres de la fonction. Exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Spécifie une liste contenant un entier court suivi d’une valeur Booléenne.

Pour obtenir la liste de la **VTS_** constantes, consultez [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Exemple

L’exemple suivant montre un gestionnaire d’événements pour l’événement MouseDown, implémentée pour trois contrôles (IDC_MYCTRL1 via IDC_MYCTRL3). La fonction de gestionnaire d’événements, `OnRangeMouseDown`, est déclaré dans le fichier d’en-tête de la classe de boîte de dialogue ( `CMyDlg`) en tant que :

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Le code ci-dessous est défini dans le fichier d’implémentation de la classe de boîte de dialogue.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp.h

##  <a name="on_event_reflect"></a>  ON_EVENT_REFLECT

L’on_event_reflect (macro), lorsqu’il est utilisé dans l’événement de table de récepteur de classe de wrapper d’un contrôle OLE, reçoit les événements déclenchés par le contrôle avant qu’ils sont gérés par le conteneur du contrôle.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
La classe à laquelle appartient cette table de récepteur d’événements.

*dispid*<br/>
L’ID de dispatch de l’événement déclenché par le contrôle.

*pfnHandler*<br/>
Pointeur vers une fonction membre qui gère l’événement. Cette fonction doit avoir une valeur Booléenne en type de retour et les types de paramètres qui correspondent aux paramètres de l’événement (voir *vtsParams*). La fonction doit retourner TRUE pour indiquer que l’événement a été géré ; Sinon, FALSE.

*vtsParams*<br/>
Une séquence de **VTS_** constantes qui spécifie les types des paramètres de l’événement. Il s’agit de l’une des constantes mêmes qui sont utilisés dans les entrées de mappage de répartition comme DISP_FUNCTION.

### <a name="remarks"></a>Notes

Le *vtsParams* argument est une liste séparée par des espaces des valeurs à partir de la **VTS_** constantes.

Un ou plusieurs de ces valeurs séparées par des espaces (non par des virgules) spécifie la liste des paramètres de la fonction. Exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Spécifie une liste contenant un entier court suivi d’une valeur Booléenne.

Pour obtenir la liste de la **VTS_** constantes, consultez [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp.h

##  <a name="on_propnotify"></a>  ON_PROPNOTIFY

Utilisez l’on_propnotify (macro) pour définir une entrée de mappage de récepteur événement pour la gestion des notifications de propriété à partir d’un contrôle OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
La classe à laquelle appartient cette table de récepteur d’événements.

*ID*<br/>
L’ID de contrôle du contrôle OLE.

*dispid*<br/>
L’ID de dispatch de la propriété impliquée dans la notification.

*pfnRequest*<br/>
Pointeur vers une fonction membre qui gère la `OnRequestEdit` notification pour cette propriété. Cette fonction doit avoir une valeur Booléenne en type de retour et un **BOOL** <strong>\*</strong> paramètre. Cette fonction doit définir le paramètre sur TRUE pour que la propriété à modifier et FALSE pour interdire. La fonction doit retourner TRUE pour indiquer que la notification a été gérée ; Sinon, FALSE.

*pfnChanged*<br/>
Pointeur vers une fonction membre qui gère la `OnChanged` notification pour cette propriété. La fonction doit avoir une valeur Booléenne de type de retour et un paramètre UINT. La fonction doit retourner TRUE pour indiquer que la notification a été gérée ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Le *vtsParams* argument est une liste séparée par des espaces des valeurs à partir de la **VTS_** constantes. Un ou plusieurs de ces valeurs séparées par des espaces (non par des virgules) spécifie la liste des paramètres de la fonction. Exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

Spécifie une liste contenant un entier court suivi d’une valeur Booléenne.

Pour obtenir la liste de la **VTS_** constantes, consultez [EVENT_CUSTOM](event-maps.md#event_custom).

##  <a name="on_propnotify_range"></a>  ON_PROPNOTIFY_RANGE

Utilisez l’on_propnotify_range (macro) pour définir une entrée de mappage de récepteur événement pour la gestion des notifications de propriété à partir de n’importe quel contrôle OLE ayant un ID de contrôle dans une plage contiguë de codes.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
La classe à laquelle appartient cette table de récepteur d’événements.

*idFirst*<br/>
L’ID de contrôle du premier contrôle OLE dans la plage.

*idLast*<br/>
L’ID de contrôle du dernier contrôle OLE dans la plage.

*dispid*<br/>
L’ID de dispatch de la propriété impliquée dans la notification.

*pfnRequest*<br/>
Pointeur vers une fonction membre qui gère la `OnRequestEdit` notification pour cette propriété. Cette fonction doit avoir un `BOOL` type de retour et `UINT` et `BOOL*` paramètres. La fonction doit définir le paramètre sur TRUE pour que la propriété à modifier et FALSE pour interdire. La fonction doit retourner TRUE pour indiquer que la notification a été gérée ; Sinon, FALSE.

*pfnChanged*<br/>
Pointeur vers une fonction membre qui gère la `OnChanged` notification pour cette propriété. La fonction doit avoir un `BOOL` type de retour et un `UINT` paramètre. La fonction doit retourner TRUE pour indiquer que la notification a été gérée ; Sinon, FALSE.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp.h

##  <a name="on_propnotify_reflect"></a>  ON_PROPNOTIFY_REFLECT

L’on_propnotify_reflect (macro), lorsqu’il est utilisé dans l’événement de table de récepteur de classe de wrapper d’un contrôle OLE, reçoit des notifications de propriété envoyées par le contrôle avant qu’ils sont gérés par le conteneur du contrôle.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
La classe à laquelle appartient cette table de récepteur d’événements.

*dispid*<br/>
L’ID de dispatch de la propriété impliquée dans la notification.

*pfnRequest*<br/>
Pointeur vers une fonction membre qui gère la `OnRequestEdit` notification pour cette propriété. Cette fonction doit avoir une valeur Booléenne en type de retour et un **BOOL** <strong>\*</strong> paramètre. Cette fonction doit définir le paramètre sur TRUE pour que la propriété à modifier et FALSE pour interdire. La fonction doit retourner TRUE pour indiquer que la notification a été gérée ; Sinon, FALSE.

*pfnChanged*<br/>
Pointeur vers une fonction membre qui gère la `OnChanged` notification pour cette propriété. La fonction doit avoir une valeur Booléenne de type de retour et aucun paramètre. La fonction doit retourner TRUE pour indiquer que la notification a été gérée ; Sinon, FALSE.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

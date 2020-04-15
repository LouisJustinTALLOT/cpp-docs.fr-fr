---
title: Tables de récepteurs d'événements
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 731ed2403aae3332e81702673d1181e9e52399a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365732"
---
# <a name="event-sink-maps"></a>Tables de récepteurs d'événements

Lorsqu’un contrôle OLE intégré déclenche un événement, le conteneur du contrôle reçoit l’événement à l’aide d’un mécanisme, appelé « carte d’évier d’événements », fournie par MFC. Cette carte de l’évier d’événement désigne les fonctions de gestionnaire pour chaque événement spécifique, aussi bien que les paramètres de ces événements. Pour plus d’informations sur les cartes de puits d’événements, voir l’article [ActiveX Control Containers](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Tables de récepteurs d'événements

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Commence la définition d’une carte d’évier d’événement.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Déclare une carte de l’évier de l’événement.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Termine la définition d’une carte de l’évier d’événements.|
|[ON_EVENT](#on_event)|Définit un gestionnaire d’événements pour un événement spécifique.|
|[ON_EVENT_RANGE](#on_event_range)|Définit un gestionnaire d’événements pour un événement spécifique tiré à partir d’un ensemble de contrôles OLE.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Reçoit les événements déclenchés par le contrôle avant qu’ils ne soient manipulés par le conteneur du contrôle.|
|[ON_PROPNOTIFY](#on_propnotify)|Définit un gestionnaire pour le traitement des notifications de propriété à partir d’un contrôle OLE.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Définit un gestionnaire pour le traitement des notifications de propriété à partir d’un ensemble de contrôles OLE.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Reçoit les notifications de propriété envoyées par le contrôle avant qu’elles ne soient traitées par le conteneur du contrôle.|

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP

Commence la définition de votre carte d’évier d’événement.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Spécifie le nom de la classe de contrôle dont l’événement coule la carte c’est.

*Baseclass*<br/>
Spécifie le nom de la classe de base de *la Classe*.

### <a name="remarks"></a>Notes

Dans le fichier de mise en œuvre (.cpp) qui définit les fonctions des membres pour votre classe, commencez la carte de l’évier de l’événement avec la BEGIN_EVENTSINK_MAP macro, puis ajoutez des entrées macro pour chaque événement à noter, et complétez la carte de l’évier de l’événement avec la END_EVENTSINK_MAP macro.

Pour plus d’informations sur les cartes des éviers d’événements et les conteneurs de contrôle OLE, voir l’article [ActiveX Control Containers](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP

Un conteneur OLE peut fournir une carte d’évier d’événement pour spécifier les événements que votre conteneur sera informé.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Notes

Utilisez la DECLARE_EVENTSINK_MAP macro à la fin de votre déclaration de classe. Puis, dans le . Fichier du RPC qui définit les fonctions des membres pour la classe, utilisez les BEGIN_EVENTSINK_MAP macro, macro entrées pour chacun des événements à noter, et le END_EVENTSINK_MAP macro pour déclarer la fin de la liste d’évier de l’événement.

Pour plus d’informations sur les cartes de puits d’événements, voir l’article [ActiveX Control Containers](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxwin.h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a>END_EVENTSINK_MAP

Termine la définition de votre carte d’évier d’événement.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="on_event"></a><a name="on_event"></a>ON_EVENT

Utilisez la macro ON_EVENT pour définir une fonction de gestionnaire d’événements pour un événement déclenché par un contrôle OLE.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
La classe à laquelle appartient cette carte d’évier d’événement.

*id*<br/>
L’ID de contrôle du contrôle OLE.

*dispid*<br/>
L’id de répartition de l’événement tiré par le contrôle.

*pfnHandler*<br/>
Pointeur vers une fonction de membre qui gère l’événement. Cette fonction doit avoir un type de retour BOOL, et les types de paramètres qui correspondent aux paramètres de l’événement (voir *vtsParams*). La fonction doit retourner VRAI pour indiquer que l’événement a été géré; autrement FALSE.

*vtsParams*<br/>
Une séquence de constantes **VTS_** qui spécifie les types de paramètres de l’événement. Ce sont les mêmes constantes qui sont utilisées dans les entrées de carte d’expédition telles que DISP_FUNCTION.

### <a name="remarks"></a>Notes

*L’argument de vtsParams* est une liste de valeurs séparées par l’espace des constantes **VTS_.** Une ou plusieurs de ces valeurs séparées par des espaces (et non des virgules) spécifient la liste des paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

spécifie une liste contenant un integer court suivi d’un BOOL.

Pour une liste des constantes **VTS_,** voir [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="on_event_range"></a><a name="on_event_range"></a>ON_EVENT_RANGE

Utilisez la macro ON_EVENT_RANGE pour définir une fonction de gestionnaire d’événements pour un événement déclenché par n’importe quel contrôle OLE ayant une pièce d’identité de contrôle dans une gamme contigue d’ID.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
La classe à laquelle appartient cette carte d’évier d’événement.

*idFirst*<br/>
L’ID de commande du premier contrôle OLE de la plage.

*idLast (en)*<br/>
L’ID de commande du dernier contrôle OLE de la plage.

*dispid*<br/>
L’id de répartition de l’événement tiré par le contrôle.

*pfnHandler*<br/>
Pointeur vers une fonction de membre qui gère l’événement. Cette fonction doit avoir un type de retour BOOL, un premier paramètre de type UINT (pour l’ID de contrôle), et des types de paramètres supplémentaires qui correspondent aux paramètres de l’événement (voir *vtsParams*). La fonction doit retourner VRAI pour indiquer que l’événement a été géré; autrement FALSE.

*vtsParams*<br/>
Une séquence de constantes **VTS_** qui spécifie les types de paramètres de l’événement. La première constante doit être de type VTS_I4, pour l’ID de contrôle. Ce sont les mêmes constantes qui sont utilisées dans les entrées de carte d’expédition telles que DISP_FUNCTION.

### <a name="remarks"></a>Notes

*L’argument de vtsParams* est une liste de valeurs séparées par l’espace des constantes **VTS_.** Une ou plusieurs de ces valeurs séparées par des espaces (et non des virgules) spécifient la liste des paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

spécifie une liste contenant un integer court suivi d’un BOOL.

Pour une liste des constantes **VTS_,** voir [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Exemple

L’exemple suivant montre un gestionnaire d’événements, pour l’événement MouseDown, mis en œuvre pour trois contrôles (IDC_MYCTRL1 par IDC_MYCTRL3). La fonction de `OnRangeMouseDown`gestionnaire d’événement, , est déclarée dans le fichier d’en-tête de la classe de dialogue ( `CMyDlg`) comme:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Le code ci-dessous est défini dans le fichier d’implémentation de la classe de dialogue.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a>ON_EVENT_REFLECT

Le ON_EVENT_REFLECT macro, lorsqu’il est utilisé dans la carte de l’évier de l’événement de la classe d’emballage d’un contrôle OLE, reçoit des événements tirés par le contrôle avant qu’ils ne soient manipulés par le conteneur du contrôle.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
La classe à laquelle appartient cette carte d’évier d’événement.

*dispid*<br/>
L’id de répartition de l’événement tiré par le contrôle.

*pfnHandler*<br/>
Pointeur vers une fonction de membre qui gère l’événement. Cette fonction doit avoir un type de retour BOOL et les types de paramètres qui correspondent aux paramètres de l’événement (voir *vtsParams*). La fonction doit retourner VRAI pour indiquer que l’événement a été géré; autrement FALSE.

*vtsParams*<br/>
Une séquence de constantes **VTS_** qui spécifie les types de paramètres de l’événement. Ce sont les mêmes constantes qui sont utilisées dans les entrées de carte d’expédition telles que DISP_FUNCTION.

### <a name="remarks"></a>Notes

*L’argument de vtsParams* est une liste de valeurs séparées par l’espace des constantes **VTS_.**

Une ou plusieurs de ces valeurs séparées par des espaces (et non des virgules) spécifient la liste des paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

spécifie une liste contenant un integer court suivi d’un BOOL.

Pour une liste des constantes **VTS_,** voir [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="on_propnotify"></a><a name="on_propnotify"></a>ON_PROPNOTIFY

Utilisez la macro ON_PROPNOTIFY pour définir une entrée de carte d’évier d’événement pour le traitement des notifications de propriété à partir d’un contrôle OLE.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
La classe à laquelle appartient cette carte d’évier d’événement.

*id*<br/>
L’ID de contrôle du contrôle OLE.

*dispid*<br/>
L’id de répartition de la propriété impliquée dans la notification.

*pfnRequest*<br/>
Pointeur vers une fonction `OnRequestEdit` de membre qui gère la notification pour cette propriété. Cette fonction doit avoir un type de retour BOOL et un paramètre **BOOL.** <strong>\*</strong> Cette fonction devrait définir le paramètre à TRUE pour permettre à la propriété de changer et FALSE de refuser. La fonction doit retourner TRUE pour indiquer que la notification a été traitée; autrement FALSE.

*pfnChanged*<br/>
Pointeur vers une fonction `OnChanged` de membre qui gère la notification pour cette propriété. La fonction doit avoir un type de retour BOOL et un paramètre UINT. La fonction doit retourner TRUE pour indiquer que la notification a été traitée; autrement FALSE.

### <a name="remarks"></a>Notes

*L’argument de vtsParams* est une liste de valeurs séparées par l’espace des constantes **VTS_.** Une ou plusieurs de ces valeurs séparées par des espaces (et non des virgules) spécifient la liste des paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

spécifie une liste contenant un integer court suivi d’un BOOL.

Pour une liste des constantes **VTS_,** voir [EVENT_CUSTOM](event-maps.md#event_custom).

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE

Utilisez la macro ON_PROPNOTIFY_RANGE pour définir une entrée de carte d’évier d’événement pour manipuler des notifications de propriété de n’importe quel contrôle d’OL ayant une identification de commande dans une gamme contigus de ID.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
La classe à laquelle appartient cette carte d’évier d’événement.

*idFirst*<br/>
L’ID de commande du premier contrôle OLE de la plage.

*idLast (en)*<br/>
L’ID de commande du dernier contrôle OLE de la plage.

*dispid*<br/>
L’id de répartition de la propriété impliquée dans la notification.

*pfnRequest*<br/>
Pointeur vers une fonction `OnRequestEdit` de membre qui gère la notification pour cette propriété. Cette fonction doit `BOOL` avoir `UINT` un `BOOL*` type de retour et des paramètres. La fonction doit définir le paramètre à TRUE pour permettre à la propriété de changer et FALSE de refuser. La fonction doit retourner TRUE pour indiquer que la notification a été traitée; autrement FALSE.

*pfnChanged*<br/>
Pointeur vers une fonction `OnChanged` de membre qui gère la notification pour cette propriété. La fonction doit `BOOL` avoir un `UINT` type de retour et un paramètre. La fonction doit retourner TRUE pour indiquer que la notification a été traitée; autrement FALSE.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT

La macro ON_PROPNOTIFY_REFLECT, lorsqu’elle est utilisée dans la carte de l’évier d’événements de la classe d’emballage d’un contrôle OLE, reçoit des notifications de propriété envoyées par le contrôle avant qu’elles ne soient manipulées par le conteneur du contrôle.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
La classe à laquelle appartient cette carte d’évier d’événement.

*dispid*<br/>
L’id de répartition de la propriété impliquée dans la notification.

*pfnRequest*<br/>
Pointeur vers une fonction `OnRequestEdit` de membre qui gère la notification pour cette propriété. Cette fonction doit avoir un type de retour BOOL et un paramètre **BOOL.** <strong>\*</strong> Cette fonction devrait définir le paramètre à TRUE pour permettre à la propriété de changer et FALSE de refuser. La fonction doit retourner TRUE pour indiquer que la notification a été traitée; autrement FALSE.

*pfnChanged*<br/>
Pointeur vers une fonction `OnChanged` de membre qui gère la notification pour cette propriété. La fonction doit avoir un type de retour BOOL et aucun paramètre. La fonction doit retourner TRUE pour indiquer que la notification a été traitée; autrement FALSE.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

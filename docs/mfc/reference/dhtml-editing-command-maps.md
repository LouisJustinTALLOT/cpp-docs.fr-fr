---
title: Mappages de commande d'édition DHTML
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 62b388eb178be018655ea2b2be00d7321da50335
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365819"
---
# <a name="dhtml-editing-command-maps"></a>Mappages de commande d'édition DHTML

Les macros suivantes peuvent être utilisées pour cartographier les commandes d’édition DHTML dans les classes dérivées de [CHtmlEditView.](../../mfc/reference/chtmleditview-class.md) Pour un exemple de leur utilisation, voir [HTMLEdit Sample](../../overview/visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>DHTML Modification De la carte de commande Macros

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Déclare une carte de commande d’édition DHTML dans une classe.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Démarre la définition d’une carte de commande d’édition DHTML au sein d’une classe.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Marque la fin d’une carte de commande d’édition DHTML.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Cartes d’un ID de commande à une commande d’édition HTML.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Cartes d’un ID de commande à un gestionnaire de commande et de message HTML.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Cartes d’un ID de commande à un élément de commande et d’interface utilisateur HTML.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Cartes d’un ID de commande à une commande d’édition HTML, gestionnaire de message, et élément d’interface utilisateur.|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP

Déclare une carte de commande d’édition DHTML dans une classe.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Nom de la classe.

### <a name="remarks"></a>Notes

Cette macro doit être utilisée dans la définition des classes dérivées de [CHtmlEditView.](../../mfc/reference/chtmleditview-class.md)

Utilisez [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) pour implémenter la carte.

### <a name="example"></a>Exemple

Voir [HTMLEdit Sample](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxhtml.h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP

Démarre la définition d’une carte de commande d’édition DHTML au sein d’une classe.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Le nom de la classe contenant la carte de commande d’édition DHTML. Cette classe devrait dériver directement ou indirectement de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) et inclure la [macro DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) dans sa définition de classe.

### <a name="remarks"></a>Notes

Ajoutez une carte de commande d’édition DHTML à votre classe pour cartographier les commandes d’interface utilisateur aux commandes d’édition HTML.

Placez la BEGIN_DHTMLEDITING_CMDMAP macro dans le fichier de mise en œuvre (.cpp) de la classe suivi [d’DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) macros pour les commandes que la classe est de cartographier (par exemple, de ID_EDIT_CUT à IDM_CUT). Utilisez la [macro END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) pour marquer la fin de la carte de l’événement.

### <a name="requirements"></a>Spécifications

  **En-tête** afxhtml.h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP

Marque la fin d’une carte de commande d’édition DHTML.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Notes

Utilisation en conjonction avec [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Exemple

Voir [HTMLEdit Sample](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxhtml.h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY

Cartes d’un ID de commande à une commande d’édition HTML.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
L’ID de commande (comme ID_EDIT_COPY).

*dhtmlcmdID dhtmlcmdID*<br/>
La commande d’édition HTML à laquelle les cartes *cmdID* (comme IDM_COPY).

### <a name="example"></a>Exemple

Voir [HTMLEdit Sample](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC

Cartes d’un ID de commande à un gestionnaire de commande et de message HTML.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
L’ID de commande (comme ID_EDIT_COPY).

*dhtmlcmdID dhtmlcmdID*<br/>
La commande d’édition HTML à laquelle les cartes *cmdID* (comme IDM_COPY).

*member_func_name*<br/>
Le nom de la fonction de gestionnaire de message à laquelle la commande est cartographiée.

### <a name="example"></a>Exemple

Voir [HTMLEdit Sample](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxhtml.h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE

Cartes d’un ID de commande à un élément de commande et d’interface utilisateur HTML.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
L’ID de commande (comme ID_EDIT_COPY).

*dhtmlcmdID dhtmlcmdID*<br/>
La commande d’édition HTML à laquelle les cartes *cmdID* (comme IDM_COPY).

*elemType*<br/>
Le type d’élément d’interface utilisateur; l’un des AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX, ou AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Exemple

Voir [HTMLEdit Sample](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Cartes d’un ID de commande à une commande d’édition HTML, gestionnaire de message, et élément d’interface utilisateur.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
L’ID de commande (comme ID_EDIT_COPY).

*dhtmlcmdID dhtmlcmdID*<br/>
La commande d’édition HTML à laquelle les cartes *cmdID* (comme IDM_COPY).

*member_func_name*<br/>
Le nom de la fonction de gestionnaire de message à laquelle la commande est cartographiée.

*elemType*<br/>
Le type d’élément d’interface utilisateur; l’un des AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX, ou AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Exemple

Voir [HTMLEdit Sample](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxhtml.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

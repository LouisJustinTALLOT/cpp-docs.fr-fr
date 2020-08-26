---
title: Mappages de commande d'édition DHTML
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: f4bbfb500e8de9594bbaa334b4e227caeaa845da
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837409"
---
# <a name="dhtml-editing-command-maps"></a>Mappages de commande d'édition DHTML

Les macros suivantes peuvent être utilisées pour mapper des commandes d’édition DHTML dans des classes dérivées de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md). Pour obtenir un exemple de leur utilisation, consultez [HtmlEdit, exemple](../../overview/visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>Macros de mappage de commande d’édition DHTML

|Nom|Description|
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Déclare un mappage de commandes d’édition DHTML dans une classe.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Démarre la définition d’un mappage de commandes d’édition DHTML dans une classe.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Marque la fin d’un mappage de commandes d’édition DHTML.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Mappe un ID de commande à une commande d’édition HTML.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Mappe un ID de commande à une commande d’édition HTML et un gestionnaire de messages.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Mappe un ID de commande à une commande d’édition HTML et à un élément d’interface utilisateur.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Mappe un ID de commande à une commande d’édition HTML, un gestionnaire de messages et un élément d’interface utilisateur.|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a> DECLARE_DHTMLEDITING_CMDMAP

Déclare un mappage de commandes d’édition DHTML dans une classe.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Nom de la classe.

### <a name="remarks"></a>Notes

Cette macro doit être utilisée dans la définition de classes dérivées de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md).

Utilisez [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) pour implémenter le mappage.

### <a name="example"></a>Exemple

Consultez l' [exemple HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxhtml. h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a> BEGIN_DHTMLEDITING_CMDMAP

Démarre la définition d’un mappage de commandes d’édition DHTML dans une classe.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Nom de la classe contenant le mappage de commande d’édition DHTML. Cette classe doit dériver directement ou indirectement de [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) et inclure la macro [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) dans sa définition de classe.

### <a name="remarks"></a>Notes

Ajoutez un mappage de commandes d’édition DHTML à votre classe pour mapper les commandes de l’interface utilisateur aux commandes d’édition HTML.

Placez la macro BEGIN_DHTMLEDITING_CMDMAP dans le fichier d’implémentation (. cpp) de la classe, suivi de [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) macros pour les commandes que la classe doit mapper (par exemple, de ID_EDIT_CUT à IDM_CUT). Utilisez la macro [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) pour marquer la fin de la table des événements.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxhtml. h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a> END_DHTMLEDITING_CMDMAP

Marque la fin d’un mappage de commandes d’édition DHTML.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Notes

À utiliser conjointement avec [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Exemple

Consultez l' [exemple HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxhtml. h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a> DHTMLEDITING_CMD_ENTRY

Mappe un ID de commande à une commande d’édition HTML.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de commande (par exemple, ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Commande d’édition HTML à laquelle *cmdID* mappe (par exemple, IDM_COPY).

### <a name="example"></a>Exemple

Consultez l' [exemple HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxhtml. h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a> DHTMLEDITING_CMD_ENTRY_FUNC

Mappe un ID de commande à une commande d’édition HTML et un gestionnaire de messages.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de commande (par exemple, ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Commande d’édition HTML à laquelle *cmdID* mappe (par exemple, IDM_COPY).

*member_func_name*<br/>
Nom de la fonction de gestionnaire de messages à laquelle la commande est mappée.

### <a name="example"></a>Exemple

Consultez l' [exemple HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxhtml. h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a> DHTMLEDITING_CMD_ENTRY_TYPE

Mappe un ID de commande à une commande d’édition HTML et à un élément d’interface utilisateur.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de commande (par exemple, ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Commande d’édition HTML à laquelle *cmdID* mappe (par exemple, IDM_COPY).

*elemType*<br/>
Type d’élément d’interface utilisateur ; l’une des AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX ou AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Exemple

Consultez l' [exemple HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxhtml. h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a> DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Mappe un ID de commande à une commande d’édition HTML, un gestionnaire de messages et un élément d’interface utilisateur.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de commande (par exemple, ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Commande d’édition HTML à laquelle *cmdID* mappe (par exemple, IDM_COPY).

*member_func_name*<br/>
Nom de la fonction de gestionnaire de messages à laquelle la commande est mappée.

*elemType*<br/>
Type d’élément d’interface utilisateur ; l’une des AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX ou AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Exemple

Consultez l' [exemple HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxhtml. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

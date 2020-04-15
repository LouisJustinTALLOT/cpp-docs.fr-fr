---
title: Classe COleCmdUI
ms.date: 09/12/2018
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
ms.openlocfilehash: 1b7a6b21a3ad778b4a5ca345b1aaf42875810e4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376265"
---
# <a name="colecmdui-class"></a>Classe COleCmdUI

Implémente une méthode pour que MFC mette à jour l'état des objets d'interface utilisateur associés aux fonctionnalités pilotées par `IOleCommandTarget`de votre application.

## <a name="syntax"></a>Syntaxe

```
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|Construit un objet `COleCmdUI`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleCmdUI::Active](#enable)|Définit ou efface le drapeau de commande d’activation.|
|[COleCmdUI::SetCheck](#setcheck)|Définit l’état d’une commande de basculement sur/off.|
|[COleCmdUI::SetText](#settext)|Renvoie un nom de texte ou une chaîne de statut pour une commande.|

## <a name="remarks"></a>Notes

Dans une application qui n’est pas activée pour DocObjects, lorsque l’utilisateur consulte un menu dans l’application, MFC traite UPDATE_COMMAND_UI notifcations. Chaque notification reçoit un objet [CCmdUI](../../mfc/reference/ccmdui-class.md) qui peut être manipulé pour refléter l’état d’une commande particulière. Toutefois, lorsque votre application est activée pour DocObjects, MFC `COleCmdUI` traite UPDATE_OLE_COMMAND_UI notifications et assigne des objets.

`COleCmdUI`permet à un DocObject de recevoir des commandes provenant de l’interface utilisateur de son conteneur (comme FileNew, Open, Print, etc.), et permet à un conteneur de recevoir des commandes provenant de l’interface utilisateur du DocObject. Bien `IDispatch` qu’il puisse être utilisé `IOleCommandTarget` pour expédier les mêmes commandes, fournit un moyen plus simple de poser des questions et d’exécuter parce qu’il repose sur un ensemble standard de commandes, généralement sans arguments, et aucune information type n’est impliquée. `COleCmdUI`peut être utilisé pour activer, mettre à jour et définir d’autres propriétés des commandes d’interface utilisateur DocObject. Lorsque vous voulez invoquer la commande, appelez [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).

Pour plus d’informations sur DocObjects, voir [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) et [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdocobj.h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI::COleCmdUI

Construit un `COleCmdUI` objet associé à une commande particulière d’interface utilisateur.

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Paramètres

*rgCmds*<br/>
Une liste de commandes prises en charge associées au GUID donné. La `OLECMD` structure associe les commandes avec des drapeaux de commandement.

*cCmds*<br/>
Le nombre de commandes dans *rgCmds*.

*pGroup (en anglais)*<br/>
Un pointeur à un GUID qui identifie un ensemble de commandes.

### <a name="remarks"></a>Notes

L’objet `COleCmdUI` fournit une interface programmatique pour mettre à jour les objets d’interface utilisateur DocObject tels que les éléments de menu ou les boutons de barre de contrôle. Les objets d’interface utilisateur peuvent être activés, désactivés, vérifiés et/ou effacés à travers l’objet. `COleCmdUI`

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI::Active

Appelez cette fonction pour définir `COleCmdUI` le drapeau de commande de l’objet à OLECOMDF_ENABLED, qui indique l’interface de la commande est disponible et activée, ou pour effacer le drapeau de commande.

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
Indique si la commande `COleCmdUI` associée à l’objet doit être activée ou désactivée. Nonzero permet la commande; 0 désactive la commande.

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI::SetCheck

Appelez cette fonction pour définir l’état d’une commande de basculement sur/off.

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Paramètres

*nCheck (en)*<br/>
Une valeur déterminant l’état pour définir une commande de basculement sur/off. Les valeurs sont les suivantes :

|Valeur|Description|
|-----------|-----------------|
|**1**|Donne la commande.|
|**2**|Définit l’ordre d’indéterminer; l’État ne peut pas être déterminé parce que l’attribut de cette commande se trouve à la fois dans les états en cours et en dehors de la sélection pertinente.|
|toute autre valeur|Donne la commande à l’off off.|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI::SetText

Appelez cette fonction pour retourner un nom de texte ou une chaîne de statut pour une commande.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Un pointeur sur le texte à utiliser avec la commande.

## <a name="see-also"></a>Voir aussi

[CCmdUI, classe](../../mfc/reference/ccmdui-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

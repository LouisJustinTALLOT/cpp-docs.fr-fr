---
description: 'En savoir plus sur : classe COleCmdUI'
title: COleCmdUI, classe
ms.date: 07/24/2020
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
ms.openlocfilehash: 0fca9d4947b40077658866b6b22a595aee13481c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333440"
---
# <a name="colecmdui-class"></a>COleCmdUI, classe

Implémente une méthode pour que MFC mette à jour l'état des objets d'interface utilisateur associés aux fonctionnalités pilotées par `IOleCommandTarget`de votre application.

## <a name="syntax"></a>Syntaxe

```cpp
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
|[COleCmdUI :: Enable](#enable)|Définit ou désactive l’indicateur de commande Enable.|
|[COleCmdUI::SetCheck](#setcheck)|Définit l’état d’une commande d’activation/désactivation.|
|[COleCmdUI :: SetText](#settext)|Retourne un nom de texte ou une chaîne d’État pour une commande.|

## <a name="remarks"></a>Notes

Dans une application qui n’est pas activée pour DocObjects, lorsque l’utilisateur consulte un menu dans l’application, MFC traite UPDATE_COMMAND_UI notifications en vertu. Chaque notification reçoit un objet [CCmdUI](../../mfc/reference/ccmdui-class.md) qui peut être manipulé pour refléter l’état d’une commande particulière. Toutefois, lorsque votre application est activée pour DocObjects, les MFC traitent UPDATE_OLE_COMMAND_UI les notifications et assignent des `COleCmdUI` objets.

`COleCmdUI` permet à un DocObject de recevoir des commandes qui proviennent de l’interface utilisateur de son conteneur (par exemple, FileNew, Open, Print, etc.) et permet à un conteneur de recevoir des commandes qui proviennent de l’interface utilisateur de DocObject. Bien qu' `IDispatch` il soit possible d’utiliser pour distribuer les mêmes commandes, `IOleCommandTarget` offre un moyen plus simple d’interroger et d’exécuter, car il s’appuie sur un ensemble standard de commandes, généralement sans arguments, et aucune information de type n’est impliquée. `COleCmdUI` peut être utilisé pour activer, mettre à jour et définir d’autres propriétés de la commande de l’interface utilisateur DocObject. Lorsque vous souhaitez appeler la commande, appelez [COleServerDoc :: OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).

Pour plus d’informations sur DocObjects, consultez [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) et [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Spécifications

**En-tête :** AfxDocOb. h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a> COleCmdUI::COleCmdUI

Construit un `COleCmdUI` objet associé à une commande d’interface utilisateur particulière.

```cpp
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Paramètres

*rgCmds*<br/>
Liste des commandes prises en charge associées au GUID donné. La `OLECMD` structure associe des commandes à des indicateurs de commande.

*cCmds*<br/>
Nombre de commandes dans *rgCmds*.

*pGroup*<br/>
Pointeur vers un GUID qui identifie un jeu de commandes.

### <a name="remarks"></a>Notes

L' `COleCmdUI` objet fournit une interface de programmation pour la mise à jour des objets d’interface utilisateur DocObject tels que les éléments de menu ou les boutons de la barre de contrôle. Les objets de l’interface utilisateur peuvent être activés, désactivés, cochés et/ou effacés via l' `COleCmdUI` objet.

## <a name="colecmduienable"></a><a name="enable"></a> COleCmdUI :: Enable

Appelez cette fonction pour définir l’indicateur de commande de l' `COleCmdUI` objet sur OLECOMDF_ENABLED, ce qui indique à l’interface que la commande est disponible et activée, ou pour effacer l’indicateur de commande.

```cpp
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Paramètres

*Ble*<br/>
Indique si la commande associée à l' `COleCmdUI` objet doit être activée ou désactivée. Une valeur différente de zéro active la commande ; la valeur 0 désactive la commande.

## <a name="colecmduisetcheck"></a><a name="setcheck"></a> COleCmdUI::SetCheck

Appelez cette fonction pour définir l’état d’une commande d’activation/désactivation.

```cpp
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Paramètres

*nConsultez*<br/>
Valeur déterminant l’État pour définir une commande d’activation/désactivation. Les valeurs sont les suivantes :

|Valeur|Description|
|-----------|-----------------|
|**1**|Affecte la valeur on à la commande.|
|**2**|Affecte la valeur Indeterminate à la commande. Impossible de déterminer l’État, car l’attribut de cette commande est à la fois dans l’état activé ou désactivé dans la sélection appropriée.|
|toute autre valeur|Définit la commande sur OFF.|

## <a name="colecmduisettext"></a><a name="settext"></a> COleCmdUI :: SetText

Appelez cette fonction pour retourner un nom de texte ou une chaîne d’État pour une commande.

```cpp
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Pointeur vers le texte à utiliser avec la commande.

## <a name="see-also"></a>Voir aussi

[CCmdUI, classe](../../mfc/reference/ccmdui-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

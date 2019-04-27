---
title: Colecmdui, classe
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
ms.openlocfilehash: 5dc4e9504805146a9eff0f5ab937868226e4516e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148508"
---
# <a name="colecmdui-class"></a>Colecmdui, classe

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
|[COleCmdUI::Enable](#enable)|Définit ou efface l’indicateur de commande enable.|
|[COleCmdUI::SetCheck](#setcheck)|Définit l’état d’un bouton bascule activé/désactivé commande.|
|[COleCmdUI::SetText](#settext)|Retourne une chaîne de texte Nom ou l’état d’une commande.|

## <a name="remarks"></a>Notes

Dans une application qui est désactivée pour DocObjects, lorsque les vues de l’utilisateur un menu dans l’application, MFC traite les notifications en vertu UPDATE_COMMAND_UI. Chaque notification reçoit un [CCmdUI](../../mfc/reference/ccmdui-class.md) objet pouvant être manipulée pour refléter l’état d’une commande particulière. Toutefois, lorsque votre application est activée pour DocObjects, traite les notifications de UPDATE_OLE_COMMAND_UI MFC et assigne `COleCmdUI` objets.

`COleCmdUI` autorise DocObject à recevoir des commandes lancées dans l’interface utilisateur de son conteneur (par exemple, le fichier-nouveau, ouvrir, imprimer et ainsi de suite), et permet à un conteneur de recevoir des commandes qui proviennent de l’interface utilisateur de DocObject. Bien que `IDispatch` peut être utilisé pour distribuer les mêmes commandes `IOleCommandTarget` offre un moyen plus simple pour interroger et exécuter, car elle s’appuie sur un ensemble standard de commandes, généralement sans arguments, et aucune information de type n’est impliquée. `COleCmdUI` peut être utilisé pour activer, mettre à jour et définir d’autres propriétés de commandes de l’interface utilisateur DocObject. Lorsque vous souhaitez appeler la commande, appelez [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).

Pour plus d’informations sur DocObjects, consultez [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) et [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdocobj.h

##  <a name="colecmdui"></a>  COleCmdUI::COleCmdUI

Construit un `COleCmdUI` objet associé à une commande d’interface utilisateur particulier.

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Paramètres

*rgCmds*<br/>
Liste des commandes prises en charge associé avec le GUID donné. Le `OLECMD` structure associe les commandes avec des indicateurs de commande.

*cCmds*<br/>
Le nombre de commandes dans *rgCmds*.

*pGroup*<br/>
Pointeur vers un GUID qui identifie un ensemble de commandes.

### <a name="remarks"></a>Notes

Le `COleCmdUI` objet fournit une interface de programmation pour la mise à jour des objets d’interface utilisateur DocObject tels que les éléments de menu ou des boutons de barre de contrôle. Les objets d’interface utilisateur peuvent être activés, désactivés, activés, et/ou effacés par la `COleCmdUI` objet.

##  <a name="enable"></a>  COleCmdUI::Enable

Appelez cette fonction pour définir l’indicateur de commande de le `COleCmdUI` pour OLECOMDF_ENABLED, ce qui indique à l’interface de la commande est disponible et activée, ou pour effacer l’indicateur de commande de l’objet.

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Paramètres

*bOn*<br/>
Indique si la commande associée à la `COleCmdUI` objet doit être activé ou désactivé. Valeur différente de zéro permet la commande ; 0 désactive la commande.

##  <a name="setcheck"></a>  COleCmdUI::SetCheck

Appelez cette fonction pour définir l’état d’un bouton bascule activé/désactivé commande.

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Paramètres

*nCheck*<br/>
Une valeur déterminant l’état à définir un bouton bascule activé/désactivé commande. Les valeurs possibles sont :

|Value|Description|
|-----------|-----------------|
|**1**|Définit la commande sur activé.|
|**2**|Définit la commande à indéterminé ; l’état ne peut pas être déterminé, car l’attribut de cette commande est à la fois et désactiver les États dans la sélection appropriée.|
|toute autre valeur|Définit la commande à off.|

##  <a name="settext"></a>  COleCmdUI::SetText

Appelez cette fonction pour retourner une chaîne de texte Nom ou l’état d’une commande.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Un pointeur vers le texte à utiliser avec la commande.

## <a name="see-also"></a>Voir aussi

[CCmdUI, classe](../../mfc/reference/ccmdui-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

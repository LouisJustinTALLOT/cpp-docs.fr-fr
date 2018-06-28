---
title: Classe de COleCmdUI | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
dev_langs:
- C++
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c80c3b81b804a66e70efe9269b12d4e18d31c676
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040712"
---
# <a name="colecmdui-class"></a>Classe de COleCmdUI
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
|[COleCmdUI::Enable](#enable)|Active ou désactive l’indicateur de commande enable.|  
|[COleCmdUI::SetCheck](#setcheck)|Définit l’état d’un bouton bascule activé/désactivé commande.|  
|[COleCmdUI::SetText](#settext)|Retourne une chaîne de texte Nom ou l’état d’une commande.|  
  
## <a name="remarks"></a>Notes  
 Dans une application qui n’est pas activée pour DocObjects, lorsque l’utilisateur affiche un menu dans l’application, le processus MFC **UPDATE_COMMAND_UI** notifications en vertu. La fonction de chaque notification un [CCmdUI](../../mfc/reference/ccmdui-class.md) objet qui peut être manipulé pour refléter l’état d’une commande particulière. Toutefois, lorsque votre application est activée pour DocObjects, MFC traite **UPDATE_OLE_COMMAND_UI** notifications et lui affecte `COleCmdUI` objets.  
  
 `COleCmdUI` autorise DocObject à recevoir des commandes qui proviennent de l’interface d’utilisateur de son conteneur (par exemple, le fichier-nouveau, ouvrir, imprimer et ainsi de suite), et permet à un conteneur de recevoir des commandes qui proviennent de l’interface utilisateur de la DocObject. Bien que `IDispatch` peut être utilisé pour distribuer les mêmes commandes `IOleCommandTarget` offre un moyen plus simple pour interroger et exécuter, car il s’appuie sur un ensemble standard de commandes, généralement sans arguments, et qu’aucune information de type n’est impliquée. `COleCmdUI` peut être utilisé pour activer, de mettre à jour et de définir d’autres propriétés de commandes d’interface utilisateur de DocObject. Lorsque vous souhaitez appeler la commande, appelez [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).  
  
 Pour plus d’informations sur DocObjects, consultez [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) et [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md). Consultez également [Internet premières étapes : Documents actifs](../../mfc/active-documents-on-the-internet.md) et [Documents actifs](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdocobj.h  
  
##  <a name="colecmdui"></a>  COleCmdUI::COleCmdUI  
 Construit un `COleCmdUI` objet associé à une commande de l’interface utilisateur particulier.  
  
```  
COleCmdUI(
    OLECMD* rgCmds,  
    ULONG cCmds,  
    const GUID* m_pGroup);
```  
  
### <a name="parameters"></a>Paramètres  
 *rgCmds*  
 Liste des commandes prises en charge, associé au GUID spécifié. Le **OLECMD** structure associe les commandes avec des indicateurs de commande.  
  
 *cCmds*  
 Le nombre de commandes dans *rgCmds*.  
  
 *pGroup*  
 Pointeur vers un GUID qui identifie un ensemble de commandes.  
  
### <a name="remarks"></a>Notes  
 Le `COleCmdUI` objet fournit une interface de programmation pour la mise à jour des objets d’interface utilisateur DocObject tels que les éléments de menu ou des boutons de barre de contrôle. Les objets d’interface utilisateur peuvent être activés, désactivés, vérifiées et/ou désactivées via la `COleCmdUI` objet.  
  
##  <a name="enable"></a>  COleCmdUI::Enable  
 Appelez cette fonction pour définir l’indicateur de commande de la `COleCmdUI` objet **OLECOMDF_ENABLED**, ce qui indique la commande à l’interface est disponible et activée, ou pour effacer l’indicateur de commande.  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>Paramètres  
 *bOn*  
 Indique si la commande associée à la `COleCmdUI` objet doit être activé ou désactivé. NonZero Active la commande ; 0 désactive la commande.  
  
##  <a name="setcheck"></a>  COleCmdUI::SetCheck  
 Appelez cette fonction pour définir l’état d’un bouton bascule activé/désactivé commande.  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Paramètres  
 *nVérifiez*  
 Une valeur qui détermine l’état à définir un bouton bascule activé/désactivé commande. Les valeurs possibles sont :  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Définit la commande à on.|  
|**2**|Définit la commande à indéterminé ; l’état ne peut pas être déterminé, car l’attribut de cette commande est à la fois et désactiver les États dans la sélection appropriée.|  
|Toute autre valeur|Définit la commande à off.|  
  
##  <a name="settext"></a>  COleCmdUI::SetText  
 Appelez cette fonction pour retourner une chaîne de texte Nom ou l’état d’une commande.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszText*  
 Pointeur vers le texte à utiliser avec la commande.  
  
## <a name="see-also"></a>Voir aussi  
 [CCmdUI (classe)](../../mfc/reference/ccmdui-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)




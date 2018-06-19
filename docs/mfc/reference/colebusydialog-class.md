---
title: Classe de la classe COleBusyDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
dev_langs:
- C++
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b061d2cc31a67c2e6059abeaadb6062b77cacb88
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374368"
---
# <a name="colebusydialog-class"></a>Classe de la classe COleBusyDialog
Utilisé pour les boîtes de dialogue OLE Le serveur ne répond pas ou Le serveur est occupé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|Construit un objet `COleBusyDialog`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleBusyDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE le serveur est occupé.|  
|[COleBusyDialog::GetSelectionType](#getselectiontype)|Détermine le choix effectué dans la boîte de dialogue.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleBusyDialog::m_bz](#m_bz)|Structure de type **OLEUIBUSY** qui contrôle le comportement de la boîte de dialogue.|  
  
## <a name="remarks"></a>Notes  
 Créer un objet de classe `COleBusyDialog` lorsque vous souhaitez appeler ces boîtes de dialogue. Après un `COleBusyDialog` objet a été construit, vous pouvez utiliser la [m_bz](#m_bz) structure pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. Le `m_bz` structure est de type **OLEUIBUSY**. Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la [DoModal](#domodal) fonction membre.  
  
> [!NOTE]
>  Code généré par l’Assistant de conteneur d’application utilise cette classe.  
  
 Pour plus d’informations, consultez la [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) structure dans le SDK Windows.  
  
 Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleBusyDialog`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxodlgs.h  
  
##  <a name="colebusydialog"></a>  COleBusyDialog::COleBusyDialog  
 Cette fonction crée uniquement une `COleBusyDialog` objet.  
  
```  
explicit COleBusyDialog(
    HTASK htaskBusy,  
    BOOL bNotResponding = FALSE,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *htaskBusy*  
 Handle vers la tâche de serveur est occupée.  
  
 *bNotResponding*  
 Si **TRUE**, appelez la boîte de dialogue ne répond pas au lieu de la boîte de dialogue serveur occupé. Le libellé dans la boîte de dialogue ne répond pas est légèrement différent de celle du texte dans la boîte de dialogue serveur occupé, et le bouton Annuler est désactivé.  
  
 `dwFlags`  
 Indicateur de création. Peut contenir zéro ou plusieurs des valeurs suivantes associées à l’opérateur OR au niveau du bit :  
  
- **BZ_DISABLECANCELBUTTON** désactiver le bouton Annuler lors de l’appel de la boîte de dialogue.  
  
- **BZ_DISABLESWITCHTOBUTTON** désactiver le bouton Basculer vers lors de l’appel de la boîte de dialogue.  
  
- **BZ_DISABLERETRYBUTTON** désactiver le bouton de nouvelle tentative lors de l’appel de la boîte de dialogue.  
  
 `pParentWnd`  
 Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. S’il s’agit **NULL**, la fenêtre parente de l’objet de la boîte de dialogue est définie dans la fenêtre principale de l’application.  
  
### <a name="remarks"></a>Notes  
 Pour afficher la boîte de dialogue, appelez [DoModal](#domodal).  
  
 Pour plus d’informations, consultez la [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) structure dans le SDK Windows.  
  
##  <a name="domodal"></a>  COleBusyDialog::DoModal  
 Appelez cette fonction pour afficher la boîte de dialogue OLE le serveur est occupé ou serveur ne répond pas.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valeur de retour  
 État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :  
  
- **IDOK** si la boîte de dialogue a été affichée avec succès.  
  
- **IDCANCEL** si l’utilisateur a annulé la boîte de dialogue.  
  
- **IDABORT** si une erreur s’est produite. Si **IDABORT** est retourné, appelez le `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez la [OleUIBusy](http://msdn.microsoft.com/library/windows/desktop/ms680125) fonction dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez initialiser le contrôle de boîte de dialogue différentes en définissant les membres de la [m_bz](#m_bz) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.  
  
 Si `DoModal` retourne **IDOK**, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations qu’il a été entrées par l’utilisateur dans la boîte de dialogue autres membres.  
  
##  <a name="getselectiontype"></a>  COleBusyDialog::GetSelectionType  
 Appelez cette fonction pour obtenir le type de sélection choisi par l’utilisateur dans la boîte de dialogue serveur occupé.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Type de la sélection effectuée.  
  
### <a name="remarks"></a>Notes  
 Les valeurs de type de retour sont spécifiées par le **sélection** type énumération déclarée dans la `COleBusyDialog` classe.  
  
```  
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```  
  
 Procédez de brèves descriptions de ces valeurs :  
  
- **COleBusyDialog::switchTo** basculer vers le bouton a été enfoncé.  
  
- **COleBusyDialog::retry** a cliqué sur Réessayer.  
  
- **COleBusyDialog::callUnblocked** appel pour activer le serveur est maintenant débloqué.  
  
##  <a name="m_bz"></a>  COleBusyDialog::m_bz  
 Structure de type **OLEUIBUSY** utilisé pour contrôler le comportement de la boîte de dialogue serveur occupé.  
  
```  
OLEUIBUSY m_bz;  
```  
  
### <a name="remarks"></a>Notes  
 Membres de cette structure peuvent être modifiés directement ou via les fonctions membres.  
  
 Pour plus d’informations, consultez la [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) structure dans le SDK Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de COleDialog](../../mfc/reference/coledialog-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleDialog, classe](../../mfc/reference/coledialog-class.md)

---
title: Coleupdatedialog, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc5d51bfeb18b51be5a54c51046e3cd420fb1cb8
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852105"
---
# <a name="coleupdatedialog-class"></a>Coleupdatedialog, classe
Utilisée pour un cas particulier de la boîte de dialogue OLE Modifier les liens, qui doit être utilisée lorsque vous devez mettre à jour uniquement les objets liés ou incorporés d'un document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Construit un objet `COleUpdateDialog`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleUpdateDialog::DoModal](#domodal)|Affiche le **modifier les liens** boîte de dialogue dans un mode de mise à jour.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
 `COleUpdateDialog`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxodlgs.h  
  
##  <a name="coleupdatedialog"></a>  COleUpdateDialog::COleUpdateDialog  
 Construit un objet `COleUpdateDialog`.  
  
```  
explicit COleUpdateDialog(
    COleDocument* pDoc,  
    BOOL bUpdateLinks = TRUE,  
    BOOL bUpdateEmbeddings = FALSE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDoc*  
 Pointe vers le document qui contient les liens qui peuvent nécessiter la mise à jour.  
  
 *bUpdateLinks*  
 Indicateur qui détermine si les objets liés doivent être mis à jour.  
  
 *bUpdateEmbeddings*  
 Indicateur qui détermine si les objets incorporés doivent être mis à jour.  
  
 *pParentWnd*  
 Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. Si sa valeur est NULL, la fenêtre parente de la boîte de dialogue est fixée à la fenêtre principale de l’application.  
  
### <a name="remarks"></a>Notes  
 Cette fonction construit uniquement un `COleUpdateDialog` objet. Pour afficher la boîte de dialogue, appelez [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Cette classe doit être utilisée à la place de `COleLinksDialog` lorsque vous souhaitez mettre à jour uniquement les éléments liés ou incorporés.  
  
##  <a name="domodal"></a>  COleUpdateDialog::DoModal  
 Affiche la boîte de dialogue Modifier les liens zone mettre à jour le mode.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valeur de retour  
 État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :  
  
- IDOK si la boîte de dialogue a été retourné avec succès.  
  
- IDCANCEL, si aucun élément lié ou incorporé dans le document actif avez besoin de la mise à jour.  
  
- IDABORT si une erreur s’est produite. Si IDABORT est retournée, appelez le [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez le [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) (fonction) dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Tous les liens et/ou des incorporations sont mis à jour, sauf si l’utilisateur sélectionne le bouton Annuler.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [COleLinksDialog, classe](../../mfc/reference/colelinksdialog-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleLinksDialog, classe](../../mfc/reference/colelinksdialog-class.md)

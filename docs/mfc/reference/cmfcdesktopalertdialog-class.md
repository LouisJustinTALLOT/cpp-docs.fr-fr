---
title: Classe de CMFCDesktopAlertDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::CreateFromParams
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::GetDlgSize
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::HasFocus
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::PreTranslateMessage
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertDialog [MFC], CreateFromParams
- CMFCDesktopAlertDialog [MFC], GetDlgSize
- CMFCDesktopAlertDialog [MFC], HasFocus
- CMFCDesktopAlertDialog [MFC], PreTranslateMessage
ms.assetid: a53c60aa-9607-485b-b826-ec64962075f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 815f9e8177cc908d7d76ca6d0f3130d1d50c93ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368168"
---
# <a name="cmfcdesktopalertdialog-class"></a>Classe de CMFCDesktopAlertDialog
Le `CMFCDesktopAlertDialog` classe est utilisée conjointement avec la [classe CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md) pour afficher une boîte de dialogue personnalisée dans une fenêtre contextuelle.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDesktopAlertDialog : public CDialogEx  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCDesktopAlertDialog::CreateFromParams](#createfromparams)||  
|[CMFCDesktopAlertDialog::GetDlgSize](#getdlgsize)||  
|[CMFCDesktopAlertDialog::HasFocus](#hasfocus)||  
|[CMFCDesktopAlertDialog::PreTranslateMessage](#pretranslatemessage)|(Substitue `CDialogEx::PreTranslateMessage`.)|  
  
### <a name="remarks"></a>Notes  
 Pour afficher une boîte de dialogue personnalisé dans une fenêtre contextuelle, procédez comme suit :  
  
1.  Dérivez une classe de `CMFCDesktopAlertDialog`.  
  
2.  Créez un modèle de boîte de dialogue enfant dans les ressources du projet.  
  
3.  Appelez [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) avec l’ID de ressource de modèle de la boîte de dialogue et un pointeur vers les informations de classe runtime de la classe dérivée en tant que paramètres.  
  
4.  Programmez la boîte de dialogue personnalisée de sorte qu'elle traite toutes les notifications en provenance des contrôles hébergés ou programmez les contrôles hébergés de sorte qu'ils traitent directement ces notifications.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxDesktopAlertDialog.h  
  
##  <a name="createfromparams"></a>  CMFCDesktopAlertDialog::CreateFromParams  

  
```  
BOOL CreateFromParams(
    CMFCDesktopAlertWndInfo& params,  
    CMFCDesktopAlertWnd* pParent);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `params`  
 [in] `pParent`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdlgsize"></a>  CMFCDesktopAlertDialog::GetDlgSize  

  
```  
CSize GetDlgSize();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="hasfocus"></a>  CMFCDesktopAlertDialog::HasFocus  

  
```  
BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="pretranslatemessage"></a>  CMFCDesktopAlertDialog::PreTranslateMessage  

  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pMsg`  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [Cmfcdesktopalertwndinfo, classe](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CDialogEx, classe](../../mfc/reference/cdialogex-class.md)

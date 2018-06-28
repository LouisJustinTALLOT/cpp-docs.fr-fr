---
title: Classe de la classe COleChangeIconDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
dev_langs:
- C++
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a67b1e405f1e3be472f9b9b3b5ebe00be3fb8a5d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041043"
---
# <a name="colechangeicondialog-class"></a>Classe de la classe COleChangeIconDialog
Utilisé pour la boîte de dialogue OLE Changer d'icône.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Construit un objet `COleChangeIconDialog`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Effectue la modification spécifiée dans la boîte de dialogue.|  
|[COleChangeIconDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE 2 changer d’icône.|  
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle vers le métafichier associé au formulaire sous forme d’icône de cet élément.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleChangeIconDialog::m_ci](#m_ci)|Une structure qui contrôle le comportement de la boîte de dialogue.|  
  
## <a name="remarks"></a>Notes  
 Créer un objet de classe `COleChangeIconDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Après un `COleChangeIconDialog` objet a été construit, vous pouvez utiliser la [m_ci](#m_ci) structure pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. Le `m_ci` structure est de type **OLEUICHANGEICON**. Pour plus d’informations sur l’utilisation de cette classe de boîte de dialogue, consultez la [DoModal](#domodal) fonction membre.  
  
 Pour plus d’informations, consultez la [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) structure dans le SDK Windows.  
  
 Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeIconDialog`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxodlgs.h  
  
##  <a name="colechangeicondialog"></a>  COleChangeIconDialog::COleChangeIconDialog  
 Cette fonction crée uniquement une `COleChangeIconDialog` objet.  
  
```  
explicit COleChangeIconDialog(
    COleClientItem* pItem,  
    DWORD dwFlags = CIF_SELECTCURRENT,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pItem*  
 Pointe vers l’élément à convertir.  
  
 *dwFlags*  
 Indicateur de création, qui contient un nombre quelconque des valeurs suivantes associées à l’aide de l’opérateur de bits- or (opérateur) :  
  
- **CIF_SELECTCURRENT** Spécifie que la case d’option en cours sera sélectionnée initialement lorsque la boîte de dialogue est appelée. Il s'agit de la valeur par défaut.  
  
- **CIF_SELECTDEFAULT** Spécifie que la case d’option par défaut sera sélectionnée initialement lorsque la boîte de dialogue est appelée.  
  
- **CIF_SELECTFROMFILE** Spécifie que la case d’option à partir du fichier sera sélectionnée initialement lorsque la boîte de dialogue est appelée.  
  
- **CIF_SHOWHELP** Spécifie que le bouton d’aide s’affiche lorsque la boîte de dialogue est appelée.  
  
- **CIF_USEICONEXE** Spécifie que l’icône doit être extraits à partir de l’exécutable spécifié dans le **szIconExe** champ [m_ci](#m_ci) au lieu de récupérer à partir du type. Cela est utile pour incorporer ou lier les fichiers autres que OLE.  
  
 *pParentWnd*  
 Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. S’il s’agit **NULL**, la fenêtre parente de la boîte de dialogue sera définie sur la fenêtre principale de l’application.  
  
### <a name="remarks"></a>Notes  
 Pour afficher la boîte de dialogue, appelez le [DoModal](#domodal) (fonction).  
  
 Pour plus d’informations, consultez la [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) structure dans le SDK Windows.  
  
##  <a name="dochangeicon"></a>  COleChangeIconDialog::DoChangeIcon  
 Appelez cette fonction pour modifier l’icône qui représente l’élément à celui sélectionné dans la boîte de dialogue après [DoModal](#domodal) retourne **IDOK**.  
  
```  
BOOL DoChangeIcon(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *pItem*  
 Pointe vers l’élément dont l’icône change.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la modification aboutit ; Sinon, 0.  
  
##  <a name="domodal"></a>  COleChangeIconDialog::DoModal  
 Appelez cette fonction pour afficher la boîte de dialogue OLE changer d’icône.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valeur de retour  
 État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :  
  
- **IDOK** si la boîte de dialogue a été affichée avec succès.  
  
- **IDCANCEL** si l’utilisateur a annulé la boîte de dialogue.  
  
- **IDABORT** si une erreur s’est produite. Si **IDABORT** est retourné, appelez le `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez la [OleUIChangeIcon](http://msdn.microsoft.com/library/windows/desktop/ms688307) fonction dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez initialiser le contrôle de boîte de dialogue différentes en définissant les membres de la [m_ci](#m_ci) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.  
  
 Si `DoModal` retourne **IDOK**, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations qu’il a été entrées par l’utilisateur dans la boîte de dialogue autres membres.  
  
##  <a name="geticonicmetafile"></a>  COleChangeIconDialog::GetIconicMetafile  
 Appelez cette fonction pour obtenir un handle de métafichier qui contient l’aspect sous forme d’icône de l’élément sélectionné.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du métafichier contenant l’aspect des icône de l’icône Nouveau, si la boîte de dialogue a été fermée en choisissant **OK**; sinon, l’icône tel qu’il était avant l’affichage de la boîte de dialogue.  
  
##  <a name="m_ci"></a>  COleChangeIconDialog::m_ci  
 Structure de type **OLEUICHANGEICON** utilisé pour contrôler le comportement de la boîte de dialogue Changer d’icône.  
  
```  
OLEUICHANGEICON m_ci;  
```  
  
### <a name="remarks"></a>Notes  
 Membres de cette structure peuvent être modifiés directement ou via les fonctions membres.  
  
 Pour plus d’informations, consultez la [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) structure dans le SDK Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de COleDialog](../../mfc/reference/coledialog-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleDialog, classe](../../mfc/reference/coledialog-class.md)

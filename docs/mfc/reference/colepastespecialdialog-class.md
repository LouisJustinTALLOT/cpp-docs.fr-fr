---
title: Classe de la classe COlePasteSpecialDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
dev_langs:
- C++
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e2e668a2ad15ec9ec2fb779be32d35c17eb57cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374355"
---
# <a name="colepastespecialdialog-class"></a>Classe de la classe COlePasteSpecialDialog
Utilisée pour la boîte de dialogue OLE Collage spécial.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COlePasteSpecialDialog : public COleDialog  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Construit un objet `COlePasteSpecialDialog`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COlePasteSpecialDialog::AddFormat](#addformat)|Ajoute des formats personnalisés à la liste des formats de que votre application peut coller.|  
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Ajoute une nouvelle entrée à la liste des formats de Presse-papiers pris en charge.|  
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Ajoute **CF_BITMAP**, **CF_DIB**, `CF_METAFILEPICT`et éventuellement `CF_LINKSOURCE` à la liste des formats de votre application peut coller.|  
|[COlePasteSpecialDialog::CreateItem](#createitem)|Crée l’élément dans le document conteneur à l’aide du format spécifié.|  
|[COlePasteSpecialDialog::DoModal](#domodal)|Affiche la boîte de dialogue OLE Collage spécial.|  
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Indique s’il faut dessiner élément sous forme d’icône ou non.|  
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Obtient un handle vers le métafichier associé au formulaire sous forme d’icône de cet élément.|  
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Obtient l’index d’options de collage disponibles qui a été choisi par l’utilisateur.|  
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Obtient le type de sélection.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COlePasteSpecialDialog::m_ps](#m_ps)|Une structure de type **OLEUIPASTESPECIAL** qui contrôle la fonction de la boîte de dialogue.|  
  
## <a name="remarks"></a>Notes  
 Créer un objet de classe `COlePasteSpecialDialog` lorsque vous souhaitez appeler cette boîte de dialogue. Après un `COlePasteSpecialDialog` objet a été construit, vous pouvez utiliser la [AddFormat](#addformat) et [AddStandardFormats](#addstandardformats) des fonctions membres pour ajouter des formats de Presse-papiers à la boîte de dialogue. Vous pouvez également utiliser le [m_ps](#m_ps) structure pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. Le `m_ps` structure est de type **OLEUIPASTESPECIAL**.  
  
 Pour plus d’informations, consultez la [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) structure dans le SDK Windows.  
  
 Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxodlgs.h  
  
##  <a name="addformat"></a>  COlePasteSpecialDialog::AddFormat  
 Appelez cette fonction pour ajouter de nouveaux formats à la liste des formats de que votre application peut prendre en charge dans une opération de collage spécial.  
  
```  
void AddFormat(
    const FORMATETC& formatEtc,  
    LPTSTR lpszFormat,  
    LPTSTR lpszResult,  
    DWORD flags);

 
void AddFormat(
    UINT cf,  
    DWORD tymed,  
    UINT nFormatID,  
    BOOL bEnableIcon,  
    BOOL bLink);
```  
  
### <a name="parameters"></a>Paramètres  
 *FMT*  
 Référence au type de données à ajouter.  
  
 `lpszFormat`  
 Chaîne qui décrit le format à l’utilisateur.  
  
 *lpszResult*  
 Chaîne qui décrit le résultat si ce format est choisi dans la boîte de dialogue.  
  
 `flags`  
 L’autre liaison et incorporation options disponibles pour ce format. Cet indicateur est une combinaison d’un ou plusieurs des valeurs différentes dans les **OLEUIPASTEFLAG** type énuméré.  
  
 `cf`  
 Le format du Presse-papiers à ajouter.  
  
 *TYMED*  
 Les types de média disponibles dans ce format. Il s’agit d’une combinaison d’une ou plusieurs des valeurs dans le **TYMED** type énuméré.  
  
 `nFormatID`  
 L’ID de la chaîne qui identifie ce format. Le format de cette chaîne est de deux chaînes séparées par un caractère « \n ». La première chaîne est celle qui est passée dans le *lpstrFormat* paramètre et le deuxième est le même que le *lpstrResult* paramètre.  
  
 *bEnableIcon*  
 Indicateur qui détermine si la case à cocher Afficher sous forme d’icône est activée quand ce format est choisi dans la zone de liste.  
  
 *bLink*  
 Indicateur qui détermine si la case d’option Coller avec liaison est activée quand ce format est choisi dans la zone de liste.  
  
### <a name="remarks"></a>Notes  
 Cette fonction peut être appelée pour ajouter deux formats standard tels que **CF_TEXT** ou **CF_TIFF** ou des formats personnalisés pour votre application est enregistrée avec le système. Pour plus d’informations à propos du collage des objets de données dans votre application, consultez l’article [des objets de données et Sources de données : Manipulation](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Pour plus d’informations, consultez la [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) type d’énumération et la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure dans le SDK Windows.  
  
 Pour plus d’informations, consultez la [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) type dans le SDK Windows énuméré.  
  
##  <a name="addlinkentry"></a>  COlePasteSpecialDialog::AddLinkEntry  
 Ajoute une nouvelle entrée à la liste des formats de Presse-papiers pris en charge.  
  
```  
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```  
  
### <a name="parameters"></a>Paramètres  
 `cf`  
 Le format du Presse-papiers à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 Un [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) structure contenant les informations de la nouvelle entrée de lien.  
  
##  <a name="addstandardformats"></a>  COlePasteSpecialDialog::AddStandardFormats  
 Appelez cette fonction pour ajouter les formats de Presse-papiers suivants à la liste des formats de que votre application peut prendre en charge dans une opération de collage spécial :  
  
```  
void AddStandardFormats(BOOL bEnableLink = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bEnableLink*  
 Indicateur qui détermine s’il faut ajouter `CF_LINKSOURCE` à la liste des formats de votre application peut coller.  
  
### <a name="remarks"></a>Notes  
  
- **CF_BITMAP**  
  
- **CF_DIB**  
  
- `CF_METAFILEPICT`  
  
- **« L’objet incorporé »**  
  
-   (facultatif) **« Lier la Source »**  
  
 Ces formats sont utilisés pour prendre en charge l’incorporation et la liaison.  
  
##  <a name="colepastespecialdialog"></a>  COlePasteSpecialDialog::COlePasteSpecialDialog  
 Construit un objet `COlePasteSpecialDialog`.  
  
```  
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,  
    COleDataObject* pDataObject = NULL,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 Indicateur de création, contient un ou plusieurs indicateurs suivants associés à l’aide de l’opérateur OR au niveau du bit :  
  
- `PSF_SELECTPASTE` Spécifie que la case d’option Coller est vérifiée initialement lors de la boîte de dialogue est appelée. Ne peut pas être utilisé en association avec `PSF_SELECTPASTELINK`. Il s'agit de la valeur par défaut.  
  
- `PSF_SELECTPASTELINK` Spécifie que le lien coller case seront vérifiées initialement lorsque la boîte de dialogue est appelée. Ne peut pas être utilisé en association avec `PSF_SELECTPASTE`.  
  
- `PSF_CHECKDISPLAYASICON` Spécifie que la case à cocher Afficher comme icône seront vérifié initialement lorsque la boîte de dialogue est appelée.  
  
- `PSF_SHOWHELP` Spécifie que le bouton d’aide s’affichera lorsque la boîte de dialogue est appelée.  
  
 `pDataObject`  
 Pointe vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) de collage. Si cette valeur est **NULL**, il obtient le `COleDataObject` à partir du Presse-papiers.  
  
 `pParentWnd`  
 Pointe vers l’objet de fenêtre parente ou propriétaire (de type `CWnd`) auquel appartient l’objet de la boîte de dialogue. S’il s’agit **NULL**, la fenêtre parente de la boîte de dialogue est définie dans la fenêtre principale de l’application.  
  
### <a name="remarks"></a>Notes  
 Cette fonction crée uniquement une `COlePasteSpecialDialog` objet. Pour afficher la boîte de dialogue, appelez le [DoModal](#domodal) (fonction).  
  
 Pour plus d’informations, consultez la [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) type dans le SDK Windows énuméré.  
  
##  <a name="createitem"></a>  COlePasteSpecialDialog::CreateItem  
 Crée le nouvel élément a été choisi dans la boîte de dialogue Collage spécial.  
  
```  
BOOL CreateItem(COleClientItem* pNewItem);
```  
  
### <a name="parameters"></a>Paramètres  
 *pNewItem*  
 Pointe vers un `COleClientItem` instance. Ne peut pas être **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément a été créé avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit uniquement être appelée après [DoModal](#domodal) retourne **IDOK**.  
  
##  <a name="domodal"></a>  COlePasteSpecialDialog::DoModal  
 Affiche la boîte de dialogue OLE Collage spécial.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valeur de retour  
 État d’achèvement de la boîte de dialogue. Une des valeurs suivantes :  
  
- **IDOK** si la boîte de dialogue a été affichée avec succès.  
  
- **IDCANCEL** si l’utilisateur a annulé la boîte de dialogue.  
  
- **IDABORT** si une erreur s’est produite. Si **IDABORT** est retourné, appelez le `COleDialog::GetLastError` fonction membre pour obtenir plus d’informations sur le type d’erreur qui s’est produite. Pour obtenir la liste des erreurs possibles, consultez la [OleUIPasteSpecial](http://msdn.microsoft.com/library/windows/desktop/ms694512) fonction dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez initialiser le contrôle de boîte de dialogue différentes en définissant les membres de la [m_ps](#m_ps) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.  
  
 Si `DoModal` retourne **IDOK**, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations saisies par l’utilisateur dans la boîte de dialogue autres membres.  
  
##  <a name="getdrawaspect"></a>  COlePasteSpecialDialog::GetDrawAspect  
 Détermine si l’utilisateur a choisi d’afficher l’élément sélectionné sous forme d’icône.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La méthode nécessaire pour restituer l’objet.  
  
- `DVASPECT_CONTENT` Retourné si la case à cocher Afficher comme icône n’était pas vérifiée lorsque la boîte de dialogue a été ignorée.  
  
- `DVASPECT_ICON` Retourné si la case à cocher Afficher comme icône a été vérifiée lorsque la boîte de dialogue a été ignorée.  
  
### <a name="remarks"></a>Notes  
 Uniquement appeler cette fonction après [DoModal](#domodal) retourne **IDOK**.  
  
 Pour plus d’informations sur l’aspect de dessin, consultez la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) structure dans le SDK Windows.  
  
##  <a name="geticonicmetafile"></a>  COlePasteSpecialDialog::GetIconicMetafile  
 Obtient le métafichier associé à l’élément sélectionné par l’utilisateur.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le handle du métafichier contenant l’aspect sous forme d’icône de l’élément sélectionné, si la case à cocher Afficher comme icône a été sélectionnée lors de la boîte de dialogue a été ignorée en choisissant **OK**; sinon **NULL**.  
  
##  <a name="getpasteindex"></a>  COlePasteSpecialDialog::GetPasteIndex  
 Obtient la valeur d’index associé à l’entrée de l’utilisateur sélectionné.  
  
```  
int GetPasteIndex() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’index dans le tableau de **OLEUIPASTEENTRY** des structures qui a été sélectionnée par l’utilisateur. Le format qui correspond à l’index sélectionné doit être utilisé lors de l’exécution de l’opération de collage.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez la [OLEUIPASTEENTRY](http://msdn.microsoft.com/library/windows/desktop/ms690165) structure dans le SDK Windows.  
  
##  <a name="getselectiontype"></a>  COlePasteSpecialDialog::GetSelectionType  
 Détermine le type de sélection effectué par l’utilisateur.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le type de la sélection effectuée.  
  
### <a name="remarks"></a>Notes  
 Les valeurs de type de retour sont spécifiées par le **sélection** type énumération déclarée dans la `COlePasteSpecialDialog` classe.  
  
```  
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };  
```  
  
 Procédez de la brèves desccriptions des valeurs suivantes :  
  
- **COlePasteSpecialDialog::pasteLink** case d’option Coller avec la liaison a été vérifiée et le format choisi a un format OLE standard.  
  
- **COlePasteSpecialDialog::pasteNormal** case d’option Coller l’a été vérifiée et le format choisi a un format OLE standard.  
  
- **COlePasteSpecialDialog::pasteOther** le format sélectionné n’est pas un format OLE standard.  
  
- **COlePasteSpecialDialog::pasteStatic** le format choisi a été un métafichier.  
  
##  <a name="m_ps"></a>  COlePasteSpecialDialog::m_ps  
 Structure de type **OLEUIPASTESPECIAL** utilisé pour contrôler le comportement de la boîte de dialogue Collage spécial.  
  
```  
OLEUIPASTESPECIAL m_ps;  
```  
  
### <a name="remarks"></a>Notes  
 Membres de cette structure peuvent être modifiés directement ou via les fonctions membres.  
  
 Pour plus d’informations, consultez la [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) structure dans le SDK Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [Classe de COleDialog](../../mfc/reference/coledialog-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleDialog, classe](../../mfc/reference/coledialog-class.md)

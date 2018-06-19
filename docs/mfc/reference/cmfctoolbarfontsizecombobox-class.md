---
title: Classe de CMFCToolBarFontSizeComboBox | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b2c5734618bf1bedc72fe78dbeaada8c437391f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372780"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>Classe de CMFCToolBarFontSizeComboBox
Un bouton de barre d’outils qui contient un contrôle de zone de liste modifiable qui permet à l’utilisateur de sélectionner une taille de police.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Construit un objet `CMFCToolBarFontSizeComboBox`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Retourne la taille de police sélectionnée en twips.|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Remplit la zone de liste modifiable avec toutes les tailles de police pris en charge d’une police spécifiée.|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Définit la taille de police en twips.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser un `CMFCToolBarFontSizeComboBox` de l’objet avec un [CMFCToolBarFontComboBox classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objet pour permettre à un utilisateur de sélectionner une police et la taille de police.  
  
 Vous pouvez ajouter un bouton de zone de liste déroulante de police taille à une barre d’outils comme vous ajoutez un bouton de zone de liste déroulante de police. Pour plus d’informations, consultez [CMFCToolBarFontComboBox classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
 Lorsque l’utilisateur sélectionne une nouvelle police dans un `CMFCToolBarFontComboBox` de l’objet, vous pouvez remplir la zone de liste déroulante de taille de police avec les tailles prises en charge pour cette police en utilisant la [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) (méthode).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCToolBarFontSizeComboBox` classe permettant de configurer un `CMFCToolBarFontSizeComboBox` objet. L’exemple montre comment récupérer la taille de police, en twips, à partir de la zone de texte, remplissage de la zone de liste déroulante de taille de police avec toutes les tailles valides de la police donnée et spécifier la taille de police en twips. Cet extrait de code fait partie de l’ [exemple Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox  
 Construit un objet `CMFCToolBarFontSizeComboBox`.  
  
```  
CMFCToolBarFontSizeComboBox();
```  
  
##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize  
 Récupère la taille de police, en twips, à partir de la zone de texte d’une zone de liste déroulante de taille de police.  
  
```  
int GetTwipSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si la valeur de retour est positive, il est la taille de police en twips. Il est -1 si la zone de texte de la zone de liste déroulante est vide. Il est -2 si une erreur se produit.  
  
##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes  
 Remplit une zone de liste déroulante de taille de police avec toutes les tailles valides de la police donnée.  
  
```  
void RebuildFontSizes(const CString& strFontName);
```  
  
### <a name="parameters"></a>Paramètres  
 `[in] strFontName`  
 Spécifie un nom de police.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction lorsque vous souhaitez synchroniser entre la sélection dans une zone de liste déroulante de police et une zone de liste déroulante de taille de police, comme un [CMFCToolBarFontComboBox classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md).  
  
##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize  
 Arrondit spécifié une taille (en twips) de la taille la plus proche des points, puis définit la taille sélectionnée dans la zone de liste déroulante pour cette valeur.  
  
```  
void SetTwipSize(int nSize);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nSize`  
 Spécifie la taille de police (en twips) pour définir.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez récupérer ultérieurement la taille de police valide précédente en appelant le [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Classe de CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Classe de CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [Classe de CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Procédure pas à pas : placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)




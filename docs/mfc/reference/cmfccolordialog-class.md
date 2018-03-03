---
title: Classe de CMFCColorDialog | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc8b547b72a7094bb6337e9e412f8548a48820f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccolordialog-class"></a>Classe de CMFCColorDialog
La `CMFCColorDialog` classe représente une boîte de dialogue de sélection de couleur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Construit un objet `CMFCColorDialog`.|  
|`CMFCColorDialog::~CMFCColorDialog`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCColorDialog::GetColor](#getcolor)|Retourne la couleur sélectionnée en cours.|  
|[CMFCColorDialog::GetPalette](#getpalette)|Retourne la palette de la couleur.|  
|`CMFCColorDialog::PreTranslateMessage`|Convertit les messages de fenêtre avant d’être distribués à le [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) et [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) fonctions Windows. Pour la syntaxe et plus d’informations, consultez [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CDialogEx::PreTranslateMessage`.)|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Dérive une palette de la palette système.|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Définit la couleur sélectionnée en cours.|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Définit la couleur plus équivalent à une valeur RVB spécifiée.|  
|[CMFCColorDialog::SetPageOne](#setpageone)|Sélectionne une valeur RVB pour la première page de propriété.|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Sélectionne une valeur RVB de la deuxième page de propriété.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|`m_bIsMyPalette`|`TRUE`Si la boîte de dialogue de sélection de couleur utilise sa propre palette de couleurs, ou `FALSE` si la boîte de dialogue utilise une palette est spécifiée dans le `CMFCColorDialog` constructeur.|  
|`m_bPickerMode`|`TRUE`pendant que l’utilisateur sélectionne une couleur à partir de la boîte de dialogue de sélection ; dans le cas contraire, `FALSE`.|  
|`m_btnColorSelect`|Le bouton de couleur que l’utilisateur a sélectionnée.|  
|`m_CurrentColor`|La couleur actuellement sélectionnée.|  
|`m_hcurPicker`|Le curseur qui est utilisé pour choisir une couleur.|  
|`m_NewColor`|Couleur sélectionnée potentiel, qui peut être sélectionnée définitivement ou restauration de la couleur d’origine.|  
|`m_pColourSheetOne`|Pointeur vers la première page de propriété de la feuille de propriétés de sélection de couleur.|  
|`m_pColourSheetTwo`|Pointeur vers la deuxième page de propriétés de la feuille de propriétés de sélection de couleur.|  
|`m_pPalette`|La palette logique en cours.|  
|`m_pPropSheet`|Pointeur vers la feuille de propriétés de la boîte de dialogue de sélection de couleur.|  
|`m_wndColors`|Un objet de contrôle de sélecteur de couleurs.|  
|`m_wndStaticPlaceHolder`|Un contrôle statique est un espace réservé pour la feuille de propriétés de sélecteur de couleurs.|  
  
## <a name="remarks"></a>Notes  
 La boîte de dialogue de sélection de couleur s’affiche en tant qu’une feuille de propriétés avec deux pages. Sur la première page, vous sélectionnez une couleur standard à partir de la palette système ; dans la deuxième page, sélectionnez une couleur personnalisée.  
  
 Vous pouvez construire un `CMFCColorDialog` de l’objet sur la pile, puis appelez `DoModal`, en passant la couleur initiale en tant que paramètre à la `CMFCColorDialog` constructeur. La boîte de dialogue de sélection de couleur, puis crée plusieurs [CMFCColorPickerCtrl classe](../../mfc/reference/cmfccolorpickerctrl-class.md) objets à gérer chaque palette de couleurs.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer une boîte de dialogue couleur à l’aide de différentes méthodes de la `CMFCColorDialog` classe. L’exemple montre comment définir actuel et les nouvelles couleurs de la boîte de dialogue et comment définir les composants rouges, verts et bleus d’une couleur sélectionnée sur les pages de propriétés de deux de la boîte de dialogue couleur. Cet exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcolordialog.h  
  
##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog  
 Construit un objet `CMFCColorDialog`.  
  
```  
CMFCColorDialog(
    COLORREF clrInit=0,  
    DWORD dwFlags=0,  
    CWnd* pParentWnd=NULL,  
    HPALETTE hPal=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `clrInit`  
 La sélection de couleur par défaut. Si aucune valeur n’est spécifiée, la valeur par défaut est RGB(0,0,0) (noir).  
  
 [in] `dwFlags`  
 (Réservé).  
  
 [in] `pParentWnd`  
 Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue.  
  
 [in] `hPal`  
 Handle vers une palette de couleurs.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcolor"></a>CMFCColorDialog::GetColor  
 Récupère la couleur de l’utilisateur sélectionne dans la boîte de dialogue couleur.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur qui contient les informations RVB pour la couleur sélectionnée dans la boîte de dialogue couleur.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction après avoir appelé la `DoModal` (méthode).  
  
##  <a name="getpalette"></a>CMFCColorDialog::GetPalette  
 Récupère la palette de couleurs qui est disponible dans la boîte de dialogue couleur actuelle.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `CPalette` objet qui a été spécifié dans le `CMFCColorDialog` constructeur.  
  
### <a name="remarks"></a>Notes  
 La palette de couleurs spécifie les couleurs que l’utilisateur peut choisir.  
  
##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette  
 Dérive une palette de la palette système.  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor  
 Définit la couleur actuelle de la boîte de dialogue.  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rgb`  
 Une valeur de couleur RVB  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor  
 Définit la couleur actuelle à la couleur de la palette en cours est le plus proche.  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `rgb`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) qui spécifie une couleur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne  
 Spécifie explicitement les composants rouges, verts et bleus d’une couleur sélectionnée sur la première page de propriété de boîte de dialogue couleur.  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `R`  
 Spécifie la composante rouge de la valeur RVB.  
  
 [in] `G`  
 Spécifie la composante verte de la valeur RVB.  
  
 [in] `B`  
 Spécifie la composante bleue de la valeur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo  
 Spécifie explicitement les composants rouges, verts et bleus d’une couleur sélectionnée sur la deuxième page de propriété de boîte de dialogue couleur.  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `R`  
 Spécifie un composant rouge de la valeur RVB  
  
 [in] `G`  
 Spécifie un composant vert d’une valeur RVB  
  
 [in] `B`  
 Spécifie un composant bleu d’une valeur RVB  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl, classe](../../mfc/reference/cmfccolorpickerctrl-class.md)

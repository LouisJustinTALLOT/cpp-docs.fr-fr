---
title: Cmfccolordialog, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cf85ec6de81ca18f32b8cd6bea015341f78287c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715356"
---
# <a name="cmfccolordialog-class"></a>Cmfccolordialog, classe
Le `CMFCColorDialog` classe représente une boîte de dialogue de sélection de couleur.  
  
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
|`CMFCColorDialog::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils soient distribués à le [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) des fonctions de Windows. Pour la syntaxe et plus d’informations, consultez [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CDialogEx::PreTranslateMessage`.)|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Dérive une palette de la palette système.|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Définit la couleur sélectionnée en cours.|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Définit la couleur plus équivalent à une valeur RVB spécifiée.|  
|[CMFCColorDialog::SetPageOne](#setpageone)|Sélectionne une valeur RVB pour la première page de propriété.|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Sélectionne une valeur RVB de la deuxième page de propriété.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|`m_bIsMyPalette`|TRUE si la boîte de dialogue de sélection de couleur utilise sa propre palette de couleurs, ou FALSE si la boîte de dialogue utilise une palette est spécifiée dans le `CMFCColorDialog` constructeur.|  
|`m_bPickerMode`|TRUE si l’utilisateur sélectionne une couleur à partir de la boîte de dialogue de sélection ; Sinon, FALSE.|  
|`m_btnColorSelect`|Le bouton de couleur que l’utilisateur a sélectionnée.|  
|`m_CurrentColor`|La couleur actuellement sélectionnée.|  
|`m_hcurPicker`|Le curseur qui est utilisé pour choisir une couleur.|  
|`m_NewColor`|Couleur sélectionnée potentiel, qui peut être définitivement sélectionnée ou restauration de la couleur d’origine.|  
|`m_pColourSheetOne`|Pointeur vers la première page de propriété de la feuille de propriétés de sélection de couleur.|  
|`m_pColourSheetTwo`|Pointeur vers la deuxième page de propriété de la feuille de propriétés de sélection de couleur.|  
|`m_pPalette`|La palette logique en cours.|  
|`m_pPropSheet`|Pointeur vers la feuille de propriétés pour la boîte de dialogue de sélection de couleur.|  
|`m_wndColors`|Un objet de contrôle de sélecteur de couleur.|  
|`m_wndStaticPlaceHolder`|Un contrôle statique est un espace réservé pour la feuille de propriétés de sélecteur de couleur.|  
  
## <a name="remarks"></a>Notes  
 La boîte de dialogue de sélection de couleur s’affiche comme une feuille de propriétés avec deux pages. Sur la première page, vous sélectionnez une couleur standard à partir de la palette système ; dans la deuxième page, vous sélectionnez une couleur personnalisée.  
  
 Vous pouvez construire un `CMFCColorDialog` de l’objet sur la pile, puis appelez `DoModal`, en passant la couleur initiale en tant que paramètre à la `CMFCColorDialog` constructeur. La boîte de dialogue de sélection de couleur, puis crée plusieurs [CMFCColorPickerCtrl, classe](../../mfc/reference/cmfccolorpickerctrl-class.md) objets pour traiter chaque palette de couleurs.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer une boîte de dialogue couleur à l’aide de différentes méthodes de la `CMFCColorDialog` classe. L’exemple montre comment définir actuel et les nouvelles couleurs de la boîte de dialogue et comment définir les composants rouges, vert et bleus de la couleur sélectionnée sur les pages de deux propriétés de la boîte de dialogue couleur. Cet exemple fait partie de la [exemple nouveaux contrôles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcolordialog.h  
  
##  <a name="cmfccolordialog"></a>  CMFCColorDialog::CMFCColorDialog  
 Construit un objet `CMFCColorDialog`.  
  
```  
CMFCColorDialog(
    COLORREF clrInit=0,  
    DWORD dwFlags=0,  
    CWnd* pParentWnd=NULL,  
    HPALETTE hPal=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
*clrInit*<br/>
[in] La sélection de couleur par défaut. Si aucune valeur n’est spécifiée, la valeur par défaut est RGB(0,0,0) (noir).  
  
*dwFlags*<br/>
[in] Réservé.
  
*pParentWnd*<br/>
[in] Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue.  
  
*hPal*<br/>
[in] Handle vers une palette de couleurs.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcolor"></a>  CMFCColorDialog::GetColor  
 Récupère la couleur de l’utilisateur sélectionne dans la boîte de dialogue couleur.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un [COLORREF](/windows/desktop/gdi/colorref) valeur qui contient les informations de RVB pour la couleur sélectionnée dans la boîte de dialogue couleur.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction une fois que vous appelez le `DoModal` (méthode).  
  
##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette  
 Récupère la palette de couleurs qui est disponible dans la boîte de dialogue couleur actuelle.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `CPalette` objet qui a été spécifié dans le `CMFCColorDialog` constructeur.  
  
### <a name="remarks"></a>Notes  
 La palette de couleurs spécifie les couleurs que l’utilisateur peut choisir.  
  
##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette  
 Dérive une palette de la palette système.  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>  CMFCColorDialog::SetCurrentColor  
 Définit la couleur actuelle de la boîte de dialogue.  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Paramètres  
*rgb*<br/>
[in] Une valeur de couleur RVB  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor  
 Définit la couleur actuelle à la couleur de la palette actuelle est la plus proche.  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Paramètres  
*rgb*<br/>
[in] Un [COLORREF](/windows/desktop/gdi/colorref) qui spécifie une couleur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne  
 Spécifie explicitement les composants rouges, vert et bleus de la couleur sélectionnée sur la première page de propriété d’une boîte de dialogue couleur.  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Paramètres  
*R*<br/>
[in] Spécifie la composante rouge de la valeur RVB.  
  
*G*<br/>
[in] Spécifie la composante verte de la valeur RVB.  
  
*B*<br/>
[in] Spécifie la composante bleue de la valeur RVB.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo  
 Spécifie explicitement les composants rouges, vert et bleus de la couleur sélectionnée dans la deuxième page de propriété d’une boîte de dialogue couleur.  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Paramètres  
*R*<br/>
[in] Spécifie un composant rouge de la valeur RVB  
  
*G*<br/>
[in] Spécifie un composant vert de la valeur RVB  
  
*B*<br/>
[in] Spécifie un composant bleu de la valeur RVB  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl, classe](../../mfc/reference/cmfccolorpickerctrl-class.md)

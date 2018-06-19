---
title: Classe de CMFCToolBarFontComboBox | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea8f05c20c3a3276f51b4267b6763831dc23eacf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373525"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Classe de CMFCToolBarFontComboBox
Un bouton de barre d’outils qui contient un contrôle de zone de liste modifiable qui permet à l’utilisateur de sélectionner une police dans la liste des polices système.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Construit un objet `CMFCToolBarFontComboBox`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Retourne un pointeur vers le `CMFCFontInfo` objet pour un index spécifié dans la zone de liste déroulante.|  
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Sélectionne une police dans la zone de liste déroulante de police en fonction d’une, le nom de la police, ou le préfixe et jeu de caractères de la police.|  
  
### <a name="data-members"></a>Membres de données  
 [CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)  
 La hauteur des caractères dans la zone de liste déroulante de police.  
  
## <a name="remarks"></a>Notes  
 Pour ajouter un bouton de zone de liste déroulante de police à une barre d’outils, procédez comme suit :  
  
1.  Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.  
  
2.  Construire un `CMFCToolBarFontComboBox` objet.  
  
3.  Dans le Gestionnaire de messages qui traite le `AFX_WM_RESETTOOLBAR` message, de remplacer le bouton d’origine avec le nouveau bouton de zone de liste déroulante à l’aide de [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
4.  Synchroniser la police sélectionnée dans la zone de liste déroulante avec la police dans le document à l’aide de la [CMFCToolBarFontComboBox::SetFont](#setfont) (méthode).  
  
 Pour synchroniser les polices du document avec la police sélectionnée dans la zone de liste modifiable, utilisez la [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) méthode pour récupérer les attributs de la police sélectionnée et utiliser ces attributs pour créer un [ CFont (classe)](../../mfc/reference/cfont-class.md) objet.  
  
 Le bouton de zone de liste modifiable police appelle la fonction Win32 [EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620) pour déterminer les polices écran et d’imprimante disponibles pour le système.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox  
 Construit un [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objet.  
  
```  
public:  
CMFCToolBarFontComboBox(
    UINT uiID,  
    int iImage,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    DWORD dwStyle = CBS_DROPDOWN,  
    int iWidth = 0,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);

 
protected:  
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,  
    int nFontType,  
    BYTE nCharSet,  
    BYTE nPitchAndFamily);  
  
CMFCToolBarFontComboBox();
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiID`  
 L’ID de commande de la zone de liste déroulante.  
  
 [in] `iImage`  
 Index de base zéro d’une image de la barre d’outils. L’image se trouve dans le [CMFCToolBarImages classe](../../mfc/reference/cmfctoolbarimages-class.md) objet [CMFCToolBar classe](../../mfc/reference/cmfctoolbar-class.md) classe conserve.  
  
 [in] `nFontType`  
 Les types de polices qui contient de la zone de liste déroulante. Ce paramètre peut être une combinaison (OR booléenne) des valeurs suivantes :  
  
 DEVICE_FONTTYPE  
  
 RASTER_FONTTYPE  
  
 TRUETYPE_FONTTYPE  
  
 [in] `nCharSet`  
 Si la valeur DEFAULT_CHARSET, la zone de liste déroulante contient tout-nommés de manière unique les polices dans tous les jeux de caractères. (S’il existe deux polices portant le même nom, la zone de liste déroulante contient un d’eux.) Si défini sur une valeur valide de caractères, la zone de liste déroulante contient uniquement les polices dans le jeu de caractères spécifié. Consultez [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) définit une liste de caractères possibles.  
  
 [in] `dwStyle`  
 Style de la zone de liste déroulante. (consultez [Styles de zone de liste déroulante](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))  
  
 [in] `iWidth`  
 La largeur en pixels du contrôle d’édition.  
  
 [in] `nPitchAndFamily`  
 Si la valeur DEFAULT_PITCH, la zone de liste déroulante contient des polices, quelle que soit la tonalité. Si la valeur FIXED_PITCH ou VARIABLE_PITCH, la zone de liste déroulante contient uniquement les polices avec ce type d’espacement. Filtrage basé sur la famille de polices n’est pas pris en charge actuellement.  
  
 [out] `pLstFontsExternal`  
 Pointeur vers un [CObList classe](../../mfc/reference/coblist-class.md) objet qui stocke les polices disponibles.  
  
### <a name="remarks"></a>Notes  
 En règle générale, `CMFCToolBarFontComboBox` objets stockent la liste des polices disponibles dans une seule partagée `CObList` objet. Si vous utilisez la deuxième surcharge de constructeur et fournir un pointeur valide vers `pLstFontsExternal`, qui `CMFCToolBarFontComboBox` objet remplira à la place la `CObList` qui `pLstFontsExternal` pointe vers des polices disponibles.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un `CMFCToolBarFontComboBox` objet. Cet extrait de code fait partie de l’ [exemple Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]  
  
##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc  
 Retourne un pointeur vers le `CMFCFontInfo` objet pour un index spécifié dans la zone de liste déroulante.  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIndex`  
 Spécifie l’index de base zéro d’un élément de zone de liste déroulante.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CMFCFontInfo` objet. Si `iIndex` ne spécifie pas un index d’élément valide, la valeur de retour est `NULL`.  
  
##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight  
 Spécifie la hauteur, en pixels, de caractères dans la zone de liste déroulante de police si la zone de liste déroulante possède un propriétaire de style de dessin.  
  
```  
static int m_nFontHeight  
```  
  
### <a name="remarks"></a>Notes  
 Si la `m_nFontHeight` est égale à 0, la hauteur est calculée automatiquement en fonction de la police par défaut de la zone de liste déroulante. La hauteur inclut à la fois la hauteur de caractères au-dessus de la ligne de base et la profondeur des caractères en dessous de la ligne de base.  
  
##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont  
 Sélectionne que la police dans la zone de liste déroulante de police en fonction du nom de la police et le caractère définie qui est spécifiés dans les paramètres.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BOOL bExact=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszName`  
 Spécifie le préfixe ou le nom de la police.  
  
 [in] `nCharSet`  
 Spécifie le jeu de caractères.  
  
 [in] `bExact`  
 Spécifie si `lpszName` contient le nom de la police ou le préfixe de la police.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la police a été activée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si `bExact` est `TRUE`, cette méthode sélectionne une police qui correspond exactement au nom que vous avez spécifié en tant que `lpszName`. Si `bExact` est `FALSE`, cette méthode sélectionne une police qui commence par le texte spécifié en tant que `lpszName` et qui utilise le jeu de caractères que vous avez spécifié en tant que `nCharSet`. Si `nCharSet` est définie à DEFAULT_CHARSET, le jeu de caractères sera ignoré et seuls `lpszName` permet de sélectionner une police.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Classe de CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Classe de CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [Classe de CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Procédure pas à pas : placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)




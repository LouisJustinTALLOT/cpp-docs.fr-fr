---
title: Cmfcribbonfontcombobox, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 79facf2498769c0f4385f6dbc84133c3773fe0e7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705689"
---
# <a name="cmfcribbonfontcombobox-class"></a>Cmfcribbonfontcombobox, classe
Implémente une zone de liste déroulante contenant une liste de polices. Vous placez la zone de liste déroulante sur un panneau de ruban.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destructeur.|  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Construit et initialise un objet `CMFCRibbonFontComboBox`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Remplit la zone de liste modifiable Police du ruban avec des polices du type, du jeu de caractères, du pas et de la famille spécifiés.|  
|`CMFCRibbonFontComboBox::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Retourne le jeu de caractères spécifié.|  
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||  
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Retourne les types de police à afficher dans la zone de liste modifiable. Les options valides sont DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE ou toute autre combinaison au niveau du bit de ces options.|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Retourne le pas et la famille des polices affichées dans la zone de liste modifiable.|  
|`CMFCRibbonFontComboBox::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Remplit la zone de liste modifiable Police du ruban avec des polices du type, du jeu de caractères, du pas et de la famille spécifiés précédemment.|  
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Sélectionne la police spécifiée dans la zone de liste modifiable.|  
  
## <a name="remarks"></a>Notes  
 Après avoir créé un `CMFCRibbonFontComboBox` d’objet, ajoutez-le à un panneau de ruban en appelant [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxRibbonComboBox.h  
  
##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts  
 Remplit la zone de liste déroulante du ruban avec des polices.  
  
```  
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Paramètres  
*nFontType*<br/>
[in] Spécifie le type de police des polices à ajouter.  
  
*nCharSet*<br/>
[in] Spécifie le jeu de caractères des polices à ajouter.  
  
*nPitchAndFamily*<br/>
[in] Spécifie la hauteur et la famille de polices à ajouter.  
  
##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox  
 Crée et initialise un [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) objet.  
  
```  
CMFCRibbonFontComboBox(
    UINT nID,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BYTE nPitchAndFamily = DEFAULT_PITCH,  
    int nWidth = -1);
```  
  
### <a name="parameters"></a>Paramètres  
*nID*<br/>
[in] ID de commande de la commande qui s’exécute lorsque l’utilisateur sélectionne un élément dans la zone de liste déroulante.  
  
*nFontType*<br/>
[in] Spécifie les types de police à afficher dans la zone de liste déroulante. Les options valides sont DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE ou toute autre combinaison au niveau du bit de ces options.  
  
*nCharSet*<br/>
[in] Filtre les polices dans la zone de liste déroulante pour ceux qui appartiennent au jeu de caractères spécifié...  
  
*nPitchAndFamily*<br/>
[in] Spécifie la hauteur et la famille de polices qui sont affichés dans la zone de liste déroulante.  
  
*nWidth*<br/>
[in] Spécifie la largeur, en pixels, de la zone de liste déroulante.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur les éventuelles *nFontType* les valeurs de paramètre, consultez [EnumFontFamProc](https://msdn.microsoft.com/library/windows/desktop/dd162621) dans la documentation du SDK Windows.  
  
 Pour plus d’informations sur les jeux de caractères valide qui peut être affecté à *nCharSet*et les valeurs valides qui peuvent être affectés à *nPitchAndFamily*, consultez [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) dans le Documentation du Kit de développement logiciel Windows.  
  
##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc  
 Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iIndex*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts  
 Remplit la zone de liste déroulante du ruban avec des polices d’un type de police spécifié précédemment, le jeu de caractères et pas et la famille.  
  
```  
void RebuildFonts();
```  
  
### <a name="remarks"></a>Notes  
 Vous pouvez spécifier le type de police, le jeu de caractères, et pas et la famille de polices à inclure dans la liste déroulante de police du ruban zone le [constructeur](#cmfcribbonfontcombobox) pour cette classe, ou en appelant [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).  
  
##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont  
 Sélectionne la police spécifiée dans la zone de liste modifiable.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    BOOL bExact = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 ' le caractère *  
 Spécifie le nom de la police à sélectionner.  
  
 *nCharSet*  
 Spécifie le jeu de caractères pour la police sélectionnée.  
  
 *bExact*  
 TRUE pour spécifier que le jeu de caractères doit correspondre à lors de la sélection d’une police ; FALSE pour indiquer que le jeu de caractères peut être ignoré lors de la sélection d’une police.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la police spécifiée a été trouvée et sélectionnée ; Sinon, zéro.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet  
 Retourne le jeu de caractères spécifié.  
  
```  
BYTE GetCharSet() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Jeu de caractères (voir LOGFONT dans la documentation du SDK Windows).  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType  
 Retourne les types de police à afficher dans la zone de liste modifiable. Les options valides sont DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE ou toute autre combinaison au niveau du bit de ces options.  
  
```  
int GetFontType() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Types de police (voir EnumFontFamProc dans la documentation du SDK Windows).  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily  
 Retourne le pas et la famille des polices affichées dans la zone de liste modifiable.  
  
```  
BYTE GetPitchAndFamily() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pas et la famille (voir LOGFONT dans la documentation du SDK Windows).  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonComboBox, classe](../../mfc/reference/cmfcribboncombobox-class.md)

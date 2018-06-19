---
title: Classe de CSmartDockingInfo | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
dev_langs:
- C++
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3328eacb9789b892a271208193e82546eb73f7e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373665"
---
# <a name="csmartdockinginfo-class"></a>Classe de CSmartDockingInfo
Définit l'apparence des marqueurs d'ancrage intelligents.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSmartDockingInfo : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CSmartDockingInfo::CSmartDockingInfo`|Constructeur par défaut.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSmartDockingInfo::CopyTo](#copyto)|Copie les paramètres des informations d’ancrage actives dans fourni [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) objet.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|Spécifie s’il faut utiliser la couleur de thème actuel lorsque l’infrastructure affiche des marqueurs d’ancrage intelligents.|  
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|Spécifie la couleur d’arrière-plan de base des marqueurs d’ancrage intelligents.|  
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|Spécifie la couleur qui remplace `m_clrToneSrc` dans les bitmaps de marqueur d’ancrage intelligents.|  
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|Spécifie la couleur des bitmaps de marqueur d’ancrage intelligents.|  
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|Spécifie la couleur des bitmaps de marqueur d’ancrage intelligents lorsqu’ils sont transparents.|  
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|Spécifie le décalage du groupe central des marqueurs d’ancrage intelligents depuis les limites du rectangle du groupe central.|  
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|Spécifie la taille totale de tous les marqueurs d’ancrage intelligents dans un groupe.|  
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|Définit l’ID des bitmaps par le framework pour les marqueurs d’ancrage intelligents qui ne sont pas mises en surbrillance de la ressource.|  
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|Définit l’ID des bitmaps par le framework pour les marqueurs d’ancrage intelligents qui sont mises en surbrillance de la ressource.|  
  
## <a name="remarks"></a>Notes  
 Les descripteurs de framework actives en interne les marqueurs d’ancrage. L’illustration suivante montre les marqueurs d’ancrage actifs standards :  
  
 ![Standards marqueurs d’ancrage actifs](../../mfc/reference/media/nextsdmarkers.png "nextsdmarkers")  
  
 Dans cette figure, l’image de gauche montre un marqueur d’ancrage intelligents groupe central qui ne dispose pas d’ancrage à un onglet activé. L’image du milieu affiche un marqueur d’ancrage actives du bord droit. L’image de droite montre un marqueur d’ancrage intelligents groupe central qui a d’ancrage à un onglet activé. Le marqueur d’ancrage intelligents de groupe central possède un bitmap principal et cinq actives les bitmaps de marqueur d’ancrage.  
  
 Vous pouvez personnaliser les paramètres suivants de marqueurs d’ancrage intelligents :  
  
-   Couleur. Par exemple, vous pouvez remplacer la couleur bleue des marqueurs dans la figure par n’importe quelle couleur définie par l’utilisateur.  
  
-   Couleur de transparence.  
  
-   Décalage d’un marqueur d’ancrage actif dans le groupe central à partir de la bordure du rectangle englobant.  
  
-   L’image bitmap principale qui représente le groupe central.  
  
-   Les bitmaps qui représente les marqueurs d’ancrage actifs standard et mis en surbrillance.  
  
 L’illustration suivante montre un exemple de marqueurs d’ancrage intelligents qui ont été personnalisées :  
  
 ![Personnalisé marqueurs d’ancrage actifs](../../mfc/reference/media/nextsdmarkerscustom.png "nextsdmarkerscustom")  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxDockingManager.h  
  
##  <a name="copyto"></a>  CSmartDockingInfo::CopyTo  
 Copie les paramètres de station d’accueil actives en cours dans fourni [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) objet.  
  
```  
void CopyTo(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `params`  
 Un objet de type `CSmartDockingInfo` qui est remplie avec les paramètres d’ancrage intelligents.  
  
##  <a name="m_busethemecolorinshading"></a>  CSmartDockingInfo::m_bUseThemeColorInShading  
 Spécifie s’il faut utiliser la couleur de thème actuel lorsque l’infrastructure affiche des marqueurs d’ancrage intelligents.  
  
```  
BOOL m_bUseThemeColorInShading;  
```  
  
### <a name="remarks"></a>Notes  
 Si `TRUE`, les marqueurs sont dessinées à l’aide de la couleur de thème actuel ; sinon, les marqueurs sont dessinés avec une couleur bleu clair.  
  
 La valeur par défaut est `FALSE`.  
  
##  <a name="m_clrbasebackground"></a>  CSmartDockingInfo::m_clrBaseBackground  
 Spécifie la couleur d’arrière-plan de base des marqueurs d’ancrage intelligents.  
  
```  
COLORREF m_clrBaseBackground;  
```  
  
##  <a name="m_clrtonedest"></a>  CSmartDockingInfo::m_clrToneDest  
 Spécifie la couleur qui remplace `m_clrToneSrc` dans les bitmaps de marqueur d’ancrage intelligents.  
  
```  
COLORREF m_clrToneDest;  
```  
  
### <a name="remarks"></a>Notes  
 Définissez cette valeur pour modifier la couleur de marqueur bitmaps par programmation. Par exemple, si vous souhaitez modifier la couleur des marqueurs standards fournis avec le framework, définissez cette valeur à la couleur souhaitée. Par défaut, [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) a la valeur RVB (61, 123, 241) (une couleur bleue).  
  
 Pour modifier la couleur des marqueurs personnalisés, vous devez spécifier les deux `m_clrToneDest` et `m_clrToneSrc`.  
  
##  <a name="m_clrtonesrc"></a>  CSmartDockingInfo::m_clrToneSrc  
 Spécifie la couleur des bitmaps de marqueur d’ancrage intelligents.  
  
```  
COLORREF m_clrToneSrc;  
```  
  
### <a name="remarks"></a>Notes  
 Définissez cette valeur uniquement lorsque vous souhaitez remplacer la couleur d’une image bitmap personnalisée avec une autre couleur. Il est inutile de définir cette valeur si vous modifiez la couleur de la norme (framework fournie) marqueur.  
  
 Utilisez `(COLORREF)-1` pour renseigner un membre du groupe d’ancrage intelligent.  
  
##  <a name="m_clrtransparent"></a>  CSmartDockingInfo::m_clrTransparent  
 Spécifie la couleur des bitmaps de marqueur d’ancrage intelligents lorsqu’ils sont transparents.  
  
```  
COLORREF m_clrTransparent;  
```  
  
### <a name="remarks"></a>Notes  
 Vous devez définir cette valeur lorsque vous affichez des marqueurs personnalisés et des bitmaps personnalisées dans le groupe d’ancrage.  
  
##  <a name="m_ncentralgroupoffset"></a>  CSmartDockingInfo::m_nCentralGroupOffset  
 Spécifie le décalage entre le groupe central des marqueurs d’ancrage intelligents et les limites du rectangle du groupe central.  
  
```  
int m_nCentralGroupOffset;  
```  
  
### <a name="remarks"></a>Notes  
 Spécifiez cette valeur si vous souhaitez modifier le décalage par défaut entre les marqueurs personnalisés et les limites du groupe central des marqueurs d’ancrage intelligents. Le décalage par défaut est de 5 pixels.  
  
##  <a name="m_sizetotal"></a>  CSmartDockingInfo::m_sizeTotal  
 Spécifie la taille totale d’un rectangle qui englobe tous les marqueurs d’ancrage actives dans le groupe central.  
  
```  
CSize m_sizeTotal;  
```  
  
### <a name="remarks"></a>Notes  
 Définissez `m_sizeTotal` à la taille du rectangle englobant de l’indicateur de groupe central. Vous devez spécifier cette valeur si vous utilisez des images personnalisées pour les marqueurs.  
  
##  <a name="m_uimarkerbmpresid"></a>  CSmartDockingInfo::m_uiMarkerBmpResID  
 Définit l’ID des bitmaps qui sont utilisés pour les marqueurs d’ancrage intelligents personnalisés non mis en surbrillance de la ressource.  
  
```  
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>Notes  
 Remplissez avec les ID des bitmaps représentant les marqueurs d’ancrage intelligents de ressources. `AFX_SD_MARKERS_NUM` est actuellement définie en tant que 5. Vous remplissez le tableau comme suit :  
  
 `params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;`  
  
 `params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;`  
  
 `params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;`  
  
 `params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;`  
  
 `params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;`  
  
##  <a name="m_uimarkerlightbmpresid"></a>  CSmartDockingInfo::m_uiMarkerLightBmpResID  
 Définit l’ID des bitmaps qui sont utilisés pour les marqueurs d’ancrage intelligents personnalisées en surbrillance de la ressource.  
  
```  
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];  
```  
  
### <a name="remarks"></a>Notes  
 Remplissez avec les ID des bitmaps représentant les marqueurs d’ancrage intelligents en surbrillance de ressources. `AFX_SD_MARKERS_NUM` est actuellement définie en tant que 5. Vous remplissez le tableau comme suit :  
  
 `params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;`  
  
 `params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;`  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CObject, classe](../../mfc/reference/cobject-class.md)

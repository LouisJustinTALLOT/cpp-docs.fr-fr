---
title: Cmfcribbonapplicationbutton, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eddce134c3cda27e57a6a20d709bc4eab08d6e80
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849013"
---
# <a name="cmfcribbonapplicationbutton-class"></a>Cmfcribbonapplicationbutton, classe
Implémente un bouton spécial situé dans l'angle supérieur gauche de la fenêtre d'application. Une fois activé, le bouton ouvre un menu qui contient généralement des commandes **Fichier** courantes telles que **Ouvrir**, **Enregistrer**et **Quitter**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonApplicationButton : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Construit et initialise un objet `CMFCRibbonApplicationButton`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCRibbonApplicationButton::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|`CMFCRibbonApplicationButton::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Assigne une image au bouton d’application du ruban.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCRibbonApplicationButton` classe. L’exemple montre comment affecter une image pour le bouton d’application et comment définir son info-bulle. Cet extrait de code fait partie de l’ [exemple Draw Client](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxRibbonBar.h  
  
##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton  
 Crée et initialise un [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md) objet.  
  
```  
CMFCRibbonApplicationButton();  
CMFCRibbonApplicationButton(UINT uiBmpResID);  
  CMFCRibbonApplicationButton(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>Paramètres  
 *uiBmpResID*  
 L’ID de ressource de l’image à afficher sur le bouton d’application.  
  
 *hBmp*  
 Handle vers une image bitmap à afficher sur le bouton d’application.  
  
### <a name="remarks"></a>Notes  
 Le bouton d’application de ruban est un bouton spécial qui se trouve dans le coin supérieur gauche de la fenêtre d’application. Lorsqu’un utilisateur clique sur ce bouton, l’application ouvre un menu contenant généralement courantes **fichier** commandes, telles que **Open**, **enregistrer**, et **Exit**.  
  
##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage  
 Assigne une image pour le bouton d’application.  
  
```  
void SetImage(UINT uiBmpResID);  
void SetImage(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiBmpResID*  
 L’ID de ressource de l’image à afficher sur le bouton d’application.  
  
 [in] *hBmp*  
 Handle vers une image bitmap à afficher sur le bouton d’application.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour affecter une nouvelle image pour le bouton d’application de ruban après avoir créé le bouton. Le bouton d’application se trouve dans le coin supérieur gauche de la fenêtre d’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)

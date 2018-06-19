---
title: CDialogBar (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
dev_langs:
- C++
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7dbb2d8202e9b87d2825b7d40a0dde4323246aa0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366712"
---
# <a name="cdialogbar-class"></a>CDialogBar (classe)
Fournit les fonctionnalités d'une boîte de dialogue non modale Windows dans une barre de contrôles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDialogBar : public CControlBar  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDialogBar::CDialogBar](#cdialogbar)|Construit un objet `CDialogBar`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDialogBar::Create](#create)|Crée une barre de boîte de dialogue Windows et l’attache à le `CDialogBar` objet.|  
  
## <a name="remarks"></a>Notes  
 Une barre de boîte de dialogue ressemble à une boîte de dialogue car elle contient des contrôles Windows standard que l’utilisateur peut passer. Un autre similarité est que vous créez un modèle de boîte de dialogue pour représenter la barre de boîte de dialogue.  
  
 Création et utilisation d’une barre de boîte de dialogue sont similaire à la création et utilisation d’un `CFormView` objet. Tout d’abord, utilisez le [éditeur de boîte de dialogue](../../windows/dialog-editor.md) pour définir un modèle de boîte de dialogue avec le style **WS_CHILD** et aucun autre style. Le modèle ne doit pas avoir le style **WS_VISIBLE**. Dans votre code d’application, appelez le constructeur pour construire le `CDialogBar` de l’objet, puis appelez **créer** pour créer la fenêtre de la barre de boîte de dialogue et l’attacher à la `CDialogBar` objet.  
  
 Pour plus d’informations sur `CDialogBar`, consultez l’article [barres de boîte de dialogue](../../mfc/dialog-bars.md) et [Technical Note 31](../../mfc/tn031-control-bars.md), barres de contrôles.  
  
> [!NOTE]
>  Dans la version actuelle, un `CDialogBar` objet ne peut pas héberger des contrôles Windows Forms. Pour plus d’informations sur les contrôles Windows Forms dans Visual C++, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxext.h  
  
##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar  
 Construit un objet `CDialogBar`.  
  
```  
CDialogBar();
```  
  
##  <a name="create"></a>  CDialogBar::Create  
 Charge le modèle de ressource de boîte de dialogue spécifié par `lpszTemplateName` ou `nIDTemplate`, crée la fenêtre de la barre de boîte de dialogue, définit son style et associe la `CDialogBar` objet.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
virtual BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 `pParentWnd`  
 Un pointeur vers le parent `CWnd` objet.  
  
 `lpszTemplateName`  
 Un pointeur vers le nom de la `CDialogBar` modèle de ressource de boîte de dialogue de l’objet.  
  
 `nStyle`  
 Le style de la barre d’outils. Styles de barre d’outils supplémentaires pris en charge sont :  
  
- `CBRS_TOP` Barre de contrôle est en haut de la fenêtre frame.  
  
- `CBRS_BOTTOM` Barre de contrôle est en bas de la fenêtre frame.  
  
- `CBRS_NOALIGN` Barre de contrôle n’est pas repositionné lorsque le parent est redimensionné.  
  
- `CBRS_TOOLTIPS` Barre de contrôle affiche des info-bulles.  
  
- **CBRS_SIZE_DYNAMIC** barre de contrôle est dynamique.  
  
- **CBRS_SIZE_FIXED** barre de contrôle est fixe.  
  
- **CBRS_FLOATING** barre de contrôle est flottant.  
  
- `CBRS_FLYBY` Barre d’état affiche des informations sur le bouton.  
  
- **CBRS_HIDE_INPLACE** barre de contrôle n’est pas affichée à l’utilisateur.  
  
 `nID`  
 L’ID de contrôle de la barre de boîte de dialogue.  
  
 `nIDTemplate`  
 L’ID de ressource de la `CDialogBar` modèle de boîte de dialogue de l’objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si vous spécifiez la `CBRS_TOP` ou `CBRS_BOTTOM` style d’alignement, la largeur de la barre de boîte de dialogue est celle de la fenêtre frame et sa hauteur est celle de la ressource spécifiée par `nIDTemplate`. Si vous spécifiez la `CBRS_LEFT` ou `CBRS_RIGHT` style d’alignement, hauteur de la barre de boîte de dialogue est celle de la fenêtre frame et sa largeur est celle de la ressource spécifiée par `nIDTemplate`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC CTRLBARS](../../visual-cpp-samples.md)   
 [CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CFormView, classe](../../mfc/reference/cformview-class.md)   
 [CControlBar, classe](../../mfc/reference/ccontrolbar-class.md)

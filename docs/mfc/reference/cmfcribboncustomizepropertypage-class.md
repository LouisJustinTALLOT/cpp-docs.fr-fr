---
title: Cmfcribboncustomizepropertypage, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7bb2f799dedd11ed1c8e0e909e7a5b1dcbb7adc5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707499"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>Cmfcribboncustomizepropertypage, classe
Implémente une page personnalisée pour le **personnaliser** boîte de dialogue dans les applications basées sur le ruban.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Construit un objet `CMFCRibbonCustomizePropertyPage`.|  
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Ajoute une catégorie personnalisée à la **commandes** zone de liste déroulante.|  
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|  
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Appelée par le système lorsqu’un utilisateur clique **OK** sur le **personnaliser** boîte de dialogue.|  
  
## <a name="remarks"></a>Notes  
 Si vous souhaitez ajouter des commandes personnalisées pour le **personnaliser** boîte de dialogue, vous devez gérer le message AFX_WM_ON_RIBBON_CUSTOMIZE. Dans le Gestionnaire de messages, vous devez instancier un `CMFCRibbonCustomizePropertyPage` objet sur la pile. Créer une liste des commandes personnalisées et appelez ensuite `AddCustomCategory` pour ajouter la nouvelle page à la **personnaliser** boîte de dialogue.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un `CMFCRibbonCustomizePropertyPage` objet et ajouter une catégorie personnalisée.  
  
 [!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
 [CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxribboncustomizedialog.h  
  
##  <a name="addcustomcategory"></a>  CMFCRibbonCustomizePropertyPage::AddCustomCategory  
 Ajoute une catégorie personnalisée à la **commandes** zone de liste déroulante.  
  
```  
void AddCustomCategory(
    LPCTSTR lpszName,  
    const CList<UINT, UINT>& lstIDS);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|*Caractère*|[in] Spécifie le nom de la catégorie personnalisée.|  
|*lstIDS*|[in] Contient l’ID de commandes de ruban à afficher dans la catégorie personnalisée.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode ajoute une catégorie nommée *le caractère* à la **commandes** zone de liste déroulante. Lorsque l’utilisateur sélectionne la catégorie, les commandes spécifiées dans *lstIDS* apparaissent dans la liste de commandes.  
  
##  <a name="cmfcribboncustomizepropertypage"></a>  CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage  
 Construit un objet `CMFCRibbonCustomizePropertyPage`.  
  
```  
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
*pRibbonBar*<br/>
[in] Un pointeur vers un contrôle de ruban pour lequel les options pour personnaliser.  
  
##  <a name="onok"></a>  CMFCRibbonCustomizePropertyPage::OnOK  
 Calleld par le système lorsqu’un utilisateur clique **OK** sur le **personnaliser** boîte de dialogue.  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut s’applique les options sélectionnées dans le **personnaliser** boîte de dialogue pour la barre d’outils Accès rapide.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)

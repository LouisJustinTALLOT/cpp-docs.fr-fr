---
title: Classe CWinFormsView | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd0af17faf3eb4a7206f50d81753e1def508aed4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370547"
---
# <a name="cwinformsview-class"></a>Classe CWinFormsView
Fournit les fonctionnalités génériques pour l'hébergement d'un contrôle Windows Forms en tant que vue MFC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWinFormsView : public CView;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinFormsView::CWinFormsView](#cwinformsview)|Construit un objet `CWinFormsView`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinFormsView::GetControl](#getcontrol)|Récupère un pointeur vers le contrôle Windows Forms.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Name||  
|----------|-|  
|[Contrôle de CWinFormsView::operator ^](#operator_control)|Convertit un type comme un pointeur vers un contrôle Windows Forms.|  
  
## <a name="remarks"></a>Notes  
 MFC utilise le `CWinFormsView` classe pour héberger un contrôle Windows Forms .NET Framework dans une vue MFC. Le contrôle est un enfant de la vue native et occupe la zone cliente de la vue MFC. Le résultat est similaire à un `CFormView` vue, ce qui vous permet de tirer parti du Concepteur Windows Forms et d’exécution pour créer des vues basées sur le formulaire riches.  
  
 Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
> [!NOTE]
>  Intégration de MFC Windows Forms fonctionne uniquement dans les projets qui se lient dynamiquement avec MFC (projets dans lesquels AFXDLL est défini).  
  
> [!NOTE]
>  CWinFormsView ne prend pas en charge la fenêtre fractionnée MFC ( [CSplitterWnd classe](../../mfc/reference/csplitterwnd-class.md)). Actuellement uniquement la Splitter Windows Forms contrôle est pris en charge.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwinforms.h  
  
##  <a name="cwinformsview"></a>  CWinFormsView::CWinFormsView  
 Construit un objet `CWinFormsView`.  
  
```  
CWinFormsView(System::Type^ pManagedViewType);  
```  
  
### <a name="parameters"></a>Paramètres  
 `pManagedViewType`  
 Pointeur vers le type de données du contrôle utilisateur Windows Forms.   
  
### <a name="example"></a>Exemple  
 Dans l’exemple suivant, la `CUserView` hérite de la classe `CWinFormsView` et passe le type de `UserControl1` à la `CWinFormsView` constructeur. `UserControl1` est un contrôle personnalisé dans ControlLibrary1.dll.  
  
 [!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]  
  
 [!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]  
  
##  <a name="getcontrol"></a>  CWinFormsView::GetControl  
 Récupère un pointeur vers le contrôle Windows Forms.  
  
```  
System::Windows::Forms::Control^ GetControl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `System.Windows.Forms.Control` objet.  
  
### <a name="remarks"></a>Notes  
 Pour obtenir un exemple montrant comment utiliser Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_control"></a>  Contrôle de CWinFormsView::operator ^  
 Convertit un type comme un pointeur vers un contrôle Windows Forms.  
  
```  
operator System::Windows::Forms::Control^() const;  
```  
  
### <a name="remarks"></a>Notes  
 Cet opérateur vous permet de passer un `CWinFormsView` affichage pour les fonctions qui acceptent un pointeur vers un contrôle Windows Forms de type <xref:System.Windows.Forms.Control>.  
  
### <a name="example"></a>Exemple  
  Consultez [CWinFormsView::GetControl](#getcontrol).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)   
 [Classe de CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView, classe](../../mfc/reference/cformview-class.md)

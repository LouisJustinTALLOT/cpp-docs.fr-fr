---
title: Classe de CMFCPropertyGridFileProperty | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2b123b5c473c834e958263edb926ef25103d788
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367794"
---
# <a name="cmfcpropertygridfileproperty-class"></a>Classe de CMFCPropertyGridFileProperty
La `CMFCPropertyGridFileProperty` classe prend en charge un élément de contrôle de liste de propriétés qui ouvre une boîte de dialogue de sélection de fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Construit un objet `CMFCPropertyGridFileProperty`.|  
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|`CMFCPropertyGridFileProperty::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|`CMFCPropertyGridFileProperty::OnClickButton`|(Substitue [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
  
### <a name="remarks"></a>Notes  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfileproperty"></a>  CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty  
 Construit un objet `CMFCPropertyGridFileProperty`.  
  
```  
CMFCPropertyGridFileProperty(
    const CString& strName,  
    BOOL bOpenFileDialog,  
    const CString& strFileName,  
    LPCTSTR lpszDefExt=NULL,  
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,  
    LPCTSTR lpszFilter=NULL,  
    LPCTSTR lpszDescr=NULL,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `strName`  
 Nom de la propriété.  
  
 [in] `bOpenFileDialog`  
 `TRUE` Pour ouvrir un **ouvrir un fichier** boîte de dialogue. `FALSE` pour ouvrir un **enregistrer le fichier** boîte de dialogue.  
  
 [in] `strFileName`  
 Nom de fichier initial.  
  
 [in] `lpszDefExt`  
 Chaîne d'une ou plusieurs extensions de nom de fichier. La valeur par défaut est `NULL`.  
  
 [in] `dwFlags`  
 Indicateurs de boîte de dialogue. La valeur par défaut est une combinaison (OR) au niveau du bit de `OFN_HIDEREADONLY` et `OFN_OVERWRITEPROMPT`.  
  
 [in] `lpszFilter`  
 Chaîne d'un ou plusieurs filtres de fichiers. La valeur par défaut est `NULL`.  
  
 [in] `lpszDescr`  
 Description d'élément de propriété. La valeur par défaut est `NULL`.  
  
 [in] `dwData`  
 Données propres à l'application associées à l'élément de propriété. Par exemple, un entier 32 bits ou un pointeur vers d'autres données. La valeur par défaut est 0.  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
 Pour obtenir une liste complète des indicateurs disponibles, consultez [structure OPENFILENAME](https://msdn.microsoft.com/library/ms646839.aspx).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre comment créer un objet en utilisant le constructeur de la classe `CMFCPropertyGridFileProperty`. Cet exemple fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty, classe](../../mfc/reference/cmfcpropertygridproperty-class.md)

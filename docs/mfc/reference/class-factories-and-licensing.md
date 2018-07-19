---
title: Fabriques de classes et gestion des licences | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abb9d5ca169edf28bb3f72c26e644894c12ccb93
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336220"
---
# <a name="class-factories-and-licensing"></a>Fabriques de classes et gestion des licences
Pour créer une instance de votre contrôle OLE, une application de conteneur appelle une fonction membre de la fabrique de classe du contrôle. Étant donné que votre contrôle est un objet OLE réel, la fabrique de classe est responsable de la création d’instances de votre contrôle. Chaque classe de contrôle OLE doit avoir une fabrique de classe.  
  
 Une autre fonctionnalité importante des contrôles OLE est leur capacité à appliquer une licence. ControlWizard vous permet d’incorporer la gestion des licences pendant la création de votre projet de contrôle. Pour plus d’informations sur les licences de contrôle, consultez l’article [contrôles ActiveX : gestion des licences An ActiveX Control](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
 Le tableau suivant répertorie plusieurs macros et fonctions utilisées pour déclarer et implémenter la fabrique de classe de votre contrôle et à la licence de votre contrôle.  
  
### <a name="class-factories-and-licensing"></a>Fabriques de classes et gestion des licences  
  
|||  
|-|-|  
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Déclare la fabrique de classe pour une page de propriété ou de contrôle OLE.|  
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implémente le contrôle `GetClassID` de fonction et déclare une instance de la fabrique de classe.|  
|[BEGIN_OLEFACTORY](#begin_olefactory)|Commence la déclaration de fonctions licence.|  
|[END_OLEFACTORY](#end_olefactory)|Met fin à la déclaration de fonctions licence.|  
|[AfxVerifyLicFile](#afxverifylicfile)|Vérifie si un contrôle a une licence pour une utilisation sur un ordinateur particulier.|  
  
##  <a name="declare_olecreate_ex"></a>  DECLARE_OLECREATE_EX  
 Déclare une fabrique de classe et le `GetClassID` fonction membre de votre classe de contrôle.  
  
```   
DECLARE_OLECREATE_EX(class_name)   
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom de la classe de contrôle.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette macro dans le fichier d’en-tête de classe contrôle pour un contrôle qui ne prend pas en charge la gestion des licences.  
  
 Notez que cette macro a le même objectif que l’exemple de code suivant :  
  
 [!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="implement_olecreate_ex"></a>  IMPLEMENT_OLECREATE_EX  
 Implémente la fabrique de classe de votre contrôle et le [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) fonction membre de votre classe de contrôle.  
  
```   
IMPLEMENT_OLECREATE_EX(
   class_name,   
    external_name,    
    l,   
    w1,   
    w2,   
    b1,   
    b2,   
    b3,   
    b4,   
    b5,   
    b6,   
    b7,
    b8)   
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom de la classe de page de propriété de contrôle.  
  
 *external_name*  
 Le nom d’objet exposé aux applications.  
  
 *l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*  
 Composants du CLSID de la classe. Pour plus d’informations sur ces paramètres, consultez la section Notes pour [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).  
  
### <a name="remarks"></a>Notes  
 Cette macro doit apparaître dans le fichier d’implémentation pour n’importe quelle classe de contrôle qui utilise le declare_olecreate_ex (macro) ou les macros BEGIN_OLEFACTORY et END_OLEFACTORY. Le nom externe est l’identificateur du contrôle OLE qui est exposé à d’autres applications. Conteneurs utilisent ce nom pour demander un objet de cette classe de contrôle.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="begin_olefactory"></a>  BEGIN_OLEFACTORY  
 Commence la déclaration de votre fabrique de classe dans le fichier d’en-tête de votre classe de contrôle.  
  
``` 
BEGIN_OLEFACTORY(class_name)  
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Spécifie le nom de la classe de contrôle dont il s’agit de fabrique de classe.  
  
### <a name="remarks"></a>Notes  
 Les déclarations de fonctions de gestion de licences de fabrique de classe doivent commencer immédiatement après BEGIN_OLEFACTORY.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="end_olefactory"></a>  END_OLEFACTORY  
 Met fin à la déclaration de la fabrique de classe de votre contrôle.  
  
```  
END_OLEFACTORY(class_name)   
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom de la classe de contrôle dont il s’agit de fabrique de classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="afxverifylicfile"></a>  AfxVerifyLicFile  
 Appelez cette fonction pour vérifier que le fichier de licence nommé par `pszLicFileName` est valide pour le contrôle OLE.  
  
```   
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,  
    LPCTSTR  pszLicFileName,  
    LPOLESTR  pszLicFileContents,  
    UINT cch = -1); 
```  
  
### <a name="parameters"></a>Paramètres  
 *hInstance*  
 Le handle d’instance de la DLL associée au contrôle sous licence.  
  
 *pszLicFileName*  
 Pointe vers une chaîne de caractères se terminant par null qui contient le nom de fichier de licence.  
  
 *pszLicFileContents*  
 Pointe vers une séquence d’octets qui doit correspondre à la séquence trouvée au début du fichier de licence.  
  
 *CCH*  
 Nombre de caractères dans *pszLicFileContents*.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le fichier de licence existe et qu’il commence par la séquence de caractères dans *pszLicFileContents*; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si *cch* est -1, cette fonction utilise :  
  
 [!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]  

### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  

## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

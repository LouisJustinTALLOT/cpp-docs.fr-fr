---
title: Services du modèle objet d’exécution | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cff506d559ab44ba4034e982bb909db763917594
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378293"
---
# <a name="run-time-object-model-services"></a>Services du modèle objet au moment de l'exécution
Les classes [CObject](../../mfc/reference/cobject-class.md) et [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) encapsulent plusieurs services d’objet, notamment l’accès aux informations de classe d’exécution, la sérialisation et la création d’objet dynamique. Toutes les classes dérivées de `CObject` héritent de cette fonctionnalité.  
  
 L'accès aux informations sur la classe d'exécution vous permet de déterminer les informations sur une classe d'objets au moment de l'exécution. La capacité de déterminer la classe d’un objet au moment de l’exécution est utile lorsque vous avez besoin de vérifications de type supplémentaires d’arguments de fonction et lorsque vous devez écrire un code spécial en fonction de la classe d’un objet. Les informations sur la classe d'exécution ne sont pas prises en charge directement par le langage C++.  
  
 La sérialisation est le processus d'écriture ou de lecture du contenu d'un objet vers et à partir d'un fichier. Vous pouvez utiliser la sérialisation pour stocker le contenu d'un objet même après que l'application se termine. L'objet peut ensuite être lu à partir du fichier lorsque l'application est redémarrée. De tels objets de données sont dits "persistants".  
  
 La création d'objets dynamique permet de créer un objet d'une classe spécifiée au moment de l'exécution. Par exemple, les objets document, vue et frame doivent prendre en charge la création dynamique car le framework doit les créer dynamiquement.  
  
 Le tableau suivant répertorie les macros MFC qui prennent en charge les informations relatives à la classe au moment de l'exécution, la sérialisation et la création dynamique.  
  
 Pour plus d’informations sur ces services de l’objet d’exécution et la sérialisation, consultez l’article [classe CObject : l’accès aux informations de classe d’exécution](../../mfc/accessing-run-time-class-information.md).  
  
### <a name="run-time-object-model-services-macros"></a>Macros des services du modèle objet au moment de l'exécution  
  


|||  
|-|-|  
|[DECLARE_DYNAMIC](#declare_dynamic)|Permet d'accéder aux informations sur la classe d'exécution (doit être utilisé dans la déclaration de classe).|  
|[DECLARE_DYNCREATE](#declare_dyncreate)|Permet la création dynamique et l'accès aux informations sur la classe d'exécution (doit être utilisé dans la déclaration de classe).|  
|[DECLARE_SERIAL](#declare_serial)|Permet la sérialisation dynamique et l'accès aux informations sur la classe d'exécution (doit être utilisé dans la déclaration de classe).|  
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Permet d'accéder aux informations sur la classe d'exécution (doit être utilisé dans l'implémentation de classe).|  
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Permet la création dynamique et l'accès aux informations sur la classe d'exécution (doit être utilisé dans l'implémentation de classe).|  
|[IMPLEMENT_SERIAL](#implement_serial)|Permet la sérialisation et l'accès aux informations sur la classe d'exécution (doit être utilisé dans l'implémentation de classe).|  
|[RUNTIME_CLASS](#runtime_class)|Retourne la structure `CRuntimeClass` qui correspond à la classe nommée.|  


 OLE requiert souvent la création dynamique des objets au moment de l'exécution. Par exemple, une application serveur OLE doit pouvoir créer des éléments OLE dynamiquement en réponse à la demande d'un client. De même, un serveur Automation doit être en mesure de créer des éléments en réponse aux demandes des clients Automation.  
  
 La bibliothèque MFC fournit deux macros spécifiques à OLE.  
  
### <a name="dynamic-creation-of-ole-objects"></a>Création dynamique des objets OLE  

 






|||  
|-|-|  
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Détermine si la bibliothèque de contrôles communs implémente l’API spécifiée.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Détermine si la bibliothèque de contrôles communs implémente l’API spécifiée.|
|[DECLARE_OLECREATE](#declare_olecreate)|Active les objets à créer par l'intermédiaire de OLE Automation.|  
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Déclare le **GetUserTypeNameID** et `GetMiscStatus` les fonctions membres de votre classe du contrôle.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Déclare que le contrôle OLE fournit une liste de pages de propriétés pour afficher ses propriétés.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Active les objets à créer par le système OLE.|  
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implémente le **GetUserTypeNameID** et `GetMiscStatus` les fonctions membres de votre classe du contrôle.|  
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Soit cette macro ou [IMPLEMENT_OLECREATE](#implement_olecreate) doit apparaître dans le fichier d’implémentation pour toute classe qui utilise `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS
Détermine si la bibliothèque de contrôles communs implémente l’API spécifiée.  
   
### <a name="syntax"></a>Syntaxe  
  ```  
AFX_COMCTL32_IF_EXISTS(  proc );  
```
### <a name="parameters"></a>Paramètres  
 `proc`  
 Pointeur vers une chaîne terminée par le caractère null qui contient le nom de fonction, ou spécifie la valeur ordinale de la fonction. Si ce paramètre est une valeur ordinale, il doit être dans le mot de poids faible ; le mot de poids fort doit être égal à zéro. Ce paramètre doit être au format Unicode.  
   
### <a name="remarks"></a>Notes  
 Utilisez cette macro pour déterminer si la bibliothèque de contrôles communs la fonction spécifiée par `proc` (au lieu d’appeler [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212).  
   
### <a name="requirements"></a>Spécifications  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Voir aussi  
 [Bibliothèque de contrôles d’isolation courantes MFC](../isolation-of-the-mfc-common-controls-library.md) [AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)
 
## <a name="afx_comctl32_if_exists2"></a>  AFX_COMCTL32_IF_EXISTS2
Détermine si la bibliothèque de contrôles communs implémente l’API spécifiée (c’est la version Unicode de [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).  
   
### <a name="syntax"></a>Syntaxe    
```  
AFX_COMCTL32_IF_EXISTS2( proc );  
```
### <a name="parameters"></a>Paramètres  
 `proc`  
 Pointeur vers une chaîne terminée par le caractère null qui contient le nom de fonction, ou spécifie la valeur ordinale de la fonction. Si ce paramètre est une valeur ordinale, il doit être dans le mot de poids faible ; le mot de poids fort doit être égal à zéro. Ce paramètre doit être au format Unicode.  
   
### <a name="remarks"></a>Notes  
 Utilisez cette macro pour déterminer si la bibliothèque de contrôles communs la fonction spécifiée par `proc` (au lieu d’appeler [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212). Cette macro est la version Unicode de `AFX_COMCTL32_IF_EXISTS`.  
   
### <a name="requirements"></a>Spécifications  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Voir aussi  
 [Bibliothèque de contrôles d’isolation courantes MFC](../isolation-of-the-mfc-common-controls-library.md) [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)



##  <a name="declare_dynamic"></a>  DECLARE_DYNAMIC  
 Ajoute la possibilité d’accéder aux informations d’exécution sur une classe d’objets lorsque vous dérivez une classe à partir de `CObject`.  
  
```
DECLARE_DYNAMIC(class_name) 
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe.  
  
### <a name="remarks"></a>Notes  
 Ajouter le `DECLARE_DYNAMIC` macro pour le module d’en-tête (.h) pour la classe, puis inclure ce module dans tous les modules .cpp qui ont besoin d’accéder aux objets de cette classe.  
  
 Si vous utilisez la **DECLARE**_ **dynamique** et `IMPLEMENT_DYNAMIC` macros comme décrit, vous pouvez ensuite utiliser le `RUNTIME_CLASS` (macro) et le `CObject::IsKindOf` pour déterminer la classe de vos objets à exécuter (fonction) heure.  
  
 Si `DECLARE_DYNAMIC` est inclus dans la déclaration de classe, puis `IMPLEMENT_DYNAMIC` doit être inclus dans l’implémentation de classe.  
  
 Pour plus d’informations sur la `DECLARE_DYNAMIC` (macro), consultez [rubriques de la classe CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [IMPLEMENT_DYNAMIC](#implement_dynamic).  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h 

##  <a name="declare_dyncreate"></a>  DECLARE_DYNCREATE  
 Permet aux objets de `CObject`-classes dérivées pour créer dynamiquement au moment de l’exécution.  
  
```
DECLARE_DYNCREATE(class_name)   
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure utilise cette possibilité de créer des objets de manière dynamique. Par exemple, le nouvel affichage créé lorsque vous ouvrez un nouveau document. Document, vue et classes de frame doivent prendre en charge la création dynamique, car l’infrastructure doit créer dynamiquement.  
  
 Ajouter le `DECLARE_DYNCREATE` macro dans un module .h pour la classe, puis inclure ce module dans tous les modules .cpp qui ont besoin d’accéder aux objets de cette classe.  
  
 Si `DECLARE_DYNCREATE` est inclus dans la déclaration de classe, puis `IMPLEMENT_DYNCREATE` doit être inclus dans l’implémentation de classe.  
  
 Pour plus d’informations sur la `DECLARE_DYNCREATE` (macro), consultez [rubriques de la classe CObject](../../mfc/using-cobject.md).  
  
> [!NOTE]
>  Le `DECLARE_DYNCREATE` macro inclut toutes les fonctionnalités de `DECLARE_DYNAMIC`.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [IMPLEMENT_DYNCREATE](#implement_dyncreate).  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h 

 
## <a name="declareolectltype"></a>DECLARE_OLECTLTYPE
Déclare le **GetUserTypeNameID** et `GetMiscStatus` les fonctions membres de votre classe du contrôle.  
   
### <a name="syntax"></a>Syntaxe    
```
DECLARE_OLECTLTYPE( class_name )  
```
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom de la classe du contrôle.  
   
### <a name="remarks"></a>Notes  
 **GetUserTypeNameID** et `GetMiscStatus` sont des fonctions virtuelles pures, déclarées dans `COleControl`. Étant donné que ces fonctions sont pures virtuelle, il doivent être substituées dans votre classe de contrôle. En plus de **DECLARE_OLECTLTYPE**, vous devez ajouter le `IMPLEMENT_OLECTLTYPE` macro pour que votre déclaration de classe du contrôle.  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxctl.h  
   
### <a name="see-also"></a>Voir aussi  
 [IMPLEMENT_OLECTLTYPE](#implement_olectltype)
 

## <a name="declareproppageids"></a>DECLARE_PROPPAGEIDS
Déclare que le contrôle OLE fournit une liste de pages de propriétés pour afficher ses propriétés.  
   
### <a name="syntax"></a>Syntaxe    
```
DECLARE_PROPPAGEIDS( class_name )  
```
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom de la classe de contrôle qui possède les pages de propriétés.  
   
### <a name="remarks"></a>Notes  
 Utilisez le `DECLARE_PROPPAGEIDS` (macro) à la fin de votre déclaration de classe. Ensuite, dans le fichier .cpp qui définit les fonctions membres de la classe, utilisez le `BEGIN_PROPPAGEIDS` (macro), les entrées de la macro pour chacune des pages de propriétés de votre contrôle et le `END_PROPPAGEIDS` macro pour déclarer la fin de la liste de propriétés de page.  
  
 Pour plus d’informations sur les pages de propriétés, consultez l’article [contrôles ActiveX : Pages de propriétés](../mfc-activex-controls-property-pages.md).  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxctl.h  
   
### <a name="see-also"></a>Voir aussi   
 [BEGIN_PROPPAGEIDS](#begin_proppageids)   
 [END_PROPPAGEIDS](#end_proppageids)

##  <a name="declare_serial"></a>  DECLARE_SERIAL  
 Génère le code d’en-tête C++ nécessaire pour un `CObject`-classe dérivée qui peut être sérialisé.  
  
```
DECLARE_SERIAL(class_name)   
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe.  
  
### <a name="remarks"></a>Notes  
 La sérialisation est le processus d’écriture ou de la lecture du contenu d’un objet vers et à partir d’un fichier.  
  
 Utilisez le `DECLARE_SERIAL` macro dans un module .h, puis inclure ce module dans tous les modules .cpp qui ont besoin d’accéder aux objets de cette classe.  
  
 Si `DECLARE_SERIAL` est inclus dans la déclaration de classe, puis `IMPLEMENT_SERIAL` doit être inclus dans l’implémentation de classe.  
  
 Le `DECLARE_SERIAL` macro inclut toutes les fonctionnalités de `DECLARE_DYNAMIC` et `DECLARE_DYNCREATE`.  
  
 Vous pouvez utiliser la **AFX_API** macro pour exporter automatiquement la `CArchive` opérateur d’extraction pour les classes qui utilisent la `DECLARE_SERIAL` et `IMPLEMENT_SERIAL` macros. Crochet les déclarations de classe (situées dans le fichier .h) avec le code suivant :  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Pour plus d’informations sur la `DECLARE_SERIAL` (macro), consultez [rubriques de la classe CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]  
  
### <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h 

##  <a name="implement_dynamic"></a>  IMPLEMENT_DYNAMIC  
 Génère le code C++ nécessaire pour un dynamique `CObject`-dérivée de classe avec un accès d’exécution pour le nom de classe et la position dans la hiérarchie.  
  
```
IMPLEMENT_DYNAMIC(class_name, base_class_name)  
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe.  
  
 `base_class_name`  
 Le nom de la classe de base.  
  
### <a name="remarks"></a>Notes  
 Utilisez le `IMPLEMENT_DYNAMIC` macro dans un module de .cpp, puis liez l’objet résultant de code qu’une seule fois.  
  
 Pour plus d’informations, consultez [rubriques de la classe CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h 

##  <a name="implement_dyncreate"></a>  IMPLEMENT_DYNCREATE  
 Permet aux objets de `CObject`-classes dérivées de créé dynamiquement à l’exécution de temps lorsqu’il est utilisé avec le `DECLARE_DYNCREATE` (macro).  
  
```
IMPLEMENT_DYNCREATE(class_name, base_class_name)   
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe.  
  
 `base_class_name`  
 Le nom réel de la classe de base.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure utilise cette possibilité de créer des objets de manière dynamique, par exemple, lorsqu’il lit un objet à partir du disque pendant la sérialisation. Ajouter le `IMPLEMENT_DYNCREATE` macro dans le fichier d’implémentation de classe. Pour plus d’informations, consultez [rubriques de la classe CObject](../../mfc/using-cobject.md).  
  
 Si vous utilisez la `DECLARE_DYNCREATE` et `IMPLEMENT_DYNCREATE` macros, vous pouvez ensuite utiliser le `RUNTIME_CLASS` macro et `CObject::IsKindOf` fonction membre pour déterminer la classe de vos objets au moment de l’exécution.  
  
 Si `DECLARE_DYNCREATE` est inclus dans la déclaration de classe, puis `IMPLEMENT_DYNCREATE` doit être inclus dans l’implémentation de classe.  
  
 Notez que cette définition de macro va appeler le constructeur par défaut pour votre classe. Si un constructeur non trivial est explicitement implémenté par la classe, elle doit implémenter explicitement également le constructeur par défaut. Le constructeur par défaut peut être ajouté à la classe **privé** ou **protégé** sections de membre pour l’empêcher de qui est appelée depuis l’extérieur de l’implémentation de classe.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h 

## <a name="implement_olecreate_flags"></a>  IMPLEMENT_OLECREATE_FLAGS
Soit cette macro ou [IMPLEMENT_OLECREATE](#implement_olecreate) doit apparaître dans le fichier d’implémentation pour toute classe qui utilise `DECLARE_OLECREATE`.  
   
### <a name="syntax"></a>Syntaxe    
```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags, 
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
  
```
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe.  
  
 *external_name*  
 Le nom d’objet exposé à d’autres applications (entourées guillemets).  
  
 `nFlags`  
 Contient un ou plusieurs des indicateurs suivants :  
  
-   `afxRegInsertable` Permet le contrôle s’affiche dans la boîte de dialogue Insérer un objet pour les objets OLE.    
-   `afxRegApartmentThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = cloisonnement.    
-   **afxRegFreeThreading** définit le modèle de thread dans le Registre pour ThreadingModel = libre.  
  
     Vous pouvez combiner les deux indicateurs `afxRegApartmentThreading` et `afxRegFreeThreading` pour définir ThreadingModel = les deux. Consultez [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) dans le SDK Windows pour plus d’informations sur l’inscription du modèle de thread.    
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *M8*  
 Composants de la classe **CLSID**.  
   
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Si vous utilisez `IMPLEMENT_OLECREATE_FLAGS`, vous pouvez spécifier le modèle de thread votre objet prend en charge à l’aide de le `nFlags` paramètre. Si vous souhaitez prendre en charge le modèle la marche périlleuse unique, utilisez `IMPLEMENT_OLECREATE`.  
  
 Le nom externe est l’identificateur exposée à d’autres applications. Applications clientes utilisent le nom externe pour demander un objet de cette classe à partir d’un serveur automation.  
  
 L’ID de classe est un identificateur unique de 128 bits pour l’objet. Il se compose d’une **long**, deux **WORD**s et huit **octets**s, telle que représentée par *l*, *w1*, *w2*, et *b1* via *M8* dans la description de la syntaxe. Les Assistants code et Assistant Application créent unique ID de classe OLE pour vous, en fonction des besoins.  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [DECLARE_OLECREATE](#declare_olecreate)   
 [Clé de CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424)


## <a name="implement_olecreate"></a> IMPLEMENT_OLECTLTYPE
Implémente le **GetUserTypeNameID** et `GetMiscStatus` les fonctions membres de votre classe du contrôle.  
   
### <a name="syntax"></a>Syntaxe    
```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )  
```
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom de la classe du contrôle.  
  
 *idsUserTypeName*  
 L’ID de ressource d’une chaîne contenant le nom externe du contrôle.  
  
 *dwOleMisc*  
 Énumération qui contient un ou plusieurs indicateurs. Pour plus d’informations sur cette énumération, consultez [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) dans le Kit de développement logiciel Windows.  
   
### <a name="remarks"></a>Notes  
 En plus de `IMPLEMENT_OLECTLTYPE`, vous devez ajouter le **DECLARE_OLECTLTYPE** macro pour que votre déclaration de classe du contrôle.  
  
 Le **GetUserTypeNameID** fonction membre retourne la chaîne de ressource qui identifie la classe du contrôle. `GetMiscStatus` Retourne le **OLEMISC** bits pour votre contrôle. Cette énumération spécifie une collection de paramètres qui décrivent les diverses caractéristiques de votre contrôle. Pour obtenir une description complète de la **OLEMISC** paramètres, voir [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) dans le Kit de développement logiciel Windows.  
  
> [!NOTE]
>  Les paramètres par défaut utilisés par le ActiveX ControlWizard sont : **OLEMISC_ACTIVATEWHENVISIBLE**, **OLEMISC_SETCLIENTSITEFIRST**, **OLEMISC_INSIDEOUT**, **OLEMISC_CANTLINKINSIDE**, et **OLEMISC_RECOMPOSEONRESIZE**.  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxctl.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [DECLARE_OLECTLTYPE](#declare_olectltype)

##  <a name="implement_serial"></a>  IMPLEMENT_SERIAL  
 Génère le code C++ nécessaire pour un dynamique `CObject`-dérivée de classe avec un accès d’exécution pour le nom de classe et la position dans la hiérarchie.  
  
```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)  
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe.  
  
 `base_class_name`  
 Le nom de la classe de base.  
  
 *wSchema*  
 A **UINT** « numéro de version » qui doit être encodé dans l’archive pour activer un programme de la désérialisation identifier et gérer les données créées par programme plus tôt les versions. Le numéro de schéma de classe ne doit pas être -1.  
  
### <a name="remarks"></a>Notes  
 Utilisez le `IMPLEMENT_SERIAL` macro dans un module .cpp ; puis lier le code d’objet qui en résulte qu’une seule fois.  
  
 Vous pouvez utiliser la **AFX_API** macro pour exporter automatiquement la `CArchive` opérateur d’extraction pour les classes qui utilisent la `DECLARE_SERIAL` et `IMPLEMENT_SERIAL` macros. Crochet les déclarations de classe (situées dans le fichier .h) avec le code suivant :  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Pour plus d’informations, consultez la [rubriques de la classe CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h 

##  <a name="runtime_class"></a>  RUNTIME_CLASS  
 Obtient la structure de classe d’exécution à partir du nom d’une classe C++.  
  
```
RUNTIME_CLASS(class_name)  
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe (ne pas entourée guillemets).  
  
### <a name="remarks"></a>Notes  
 `RUNTIME_CLASS` Retourne un pointeur vers un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure pour la classe spécifiée par *class_name*. Uniquement `CObject`-déclarés avec des classes dérivées `DECLARE_DYNAMIC`, `DECLARE_DYNCREATE`, ou `DECLARE_SERIAL` retourne des pointeurs vers un `CRuntimeClass` structure.  
  
 Pour plus d’informations, consultez [rubriques de la classe CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h 
   
##  <a name="declare_olecreate"></a>  DECLARE_OLECREATE  
 Permet aux objets de `CCmdTarget`-classes dérivées pour être créé via OLE automation.  
  
```
DECLARE_OLECREATE(class_name) 
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’autres applications OLE créer des objets de ce type.  
  
 Ajouter le `DECLARE_OLECREATE` macro dans un module pour la classe, .h, puis inclure ce module dans tous les modules .cpp qui ont besoin d’accéder aux objets de cette classe.  
  
 Si `DECLARE_OLECREATE` est inclus dans la déclaration de classe, puis `IMPLEMENT_OLECREATE` doit être inclus dans l’implémentation de classe. Une déclaration de classe à l’aide de `DECLARE_OLECREATE` doit également utiliser `DECLARE_DYNCREATE` ou `DECLARE_SERIAL`.  

### <a name="requirements"></a>Spécifications  
 **En-tête**: afxdisp.h  

##  <a name="implement_olecreate"></a>  IMPLEMENT_OLECREATE  
 Soit cette macro ou [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) doit apparaître dans le fichier d’implémentation pour toute classe qui utilise `DECLARE_OLECREATE`.  
  
```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom réel de la classe.  
  
 *external_name*  
 Le nom d’objet exposé à d’autres applications (entourées guillemets).  
  
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *M8*  
 Composants de la classe **CLSID**.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Si vous utilisez `IMPLEMENT_OLECREATE`, par défaut, vous prenez en charge le modèle de thread unique. Si vous utilisez `IMPLEMENT_OLECREATE_FLAGS`, vous pouvez spécifier le modèle de thread votre objet prend en charge à l’aide de le `nFlags` paramètre.  
  
 Le nom externe est l’identificateur exposée à d’autres applications. Applications clientes utilisent le nom externe pour demander un objet de cette classe à partir d’un serveur automation.  
  
 L’ID de classe est un identificateur unique de 128 bits pour l’objet. Il se compose d’une **long**, deux **WORD**s et huit **octets**s, telle que représentée par *l*, *w1*, *w2*, et *b1* via *M8* dans la description de la syntaxe. Les Assistants code et Assistant Application créent unique ID de classe OLE pour vous, en fonction des besoins.  

### <a name="requirements"></a>Spécifications  
 **En-tête**: afxdisp.h 

## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)


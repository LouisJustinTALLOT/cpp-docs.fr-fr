---
title: Tables de dispatch | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 313e465698da5799a107bc3bdbeb6d2cbbe47303
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377094"
---
# <a name="dispatch-maps"></a>Tables de dispatch
OLE Automation fournit des méthodes pour appeler des méthodes et pour accéder aux propriétés entre les applications. Le mécanisme fourni par la bibliothèque Microsoft Foundation Class pour la distribution de ces requêtes est la « table de dispatch, » qui désigne les noms internes et externes de fonctions de l’objet et les propriétés, ainsi que les types de données des propriétés eux-mêmes et de arguments de fonction.  
  
### <a name="dispatch-maps"></a>Tables de dispatch  
  
|||  
|-|-|  
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Déclare qu’une table de dispatch servira pour exposer des méthodes et des propriétés (doit être utilisé dans la déclaration de classe) d’une classe.|  
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Démarre la définition d’une table de dispatch.|  
|[END_DISPATCH_MAP](#end_dispatch_map)|Termine la définition d’une table de dispatch.|  
|[DISP_FUNCTION](#disp_function)|Utilisé dans une table de dispatch pour définir une fonction d’automatisation OLE.|  
|[DISP_PROPERTY](#disp_property)|Définit une propriété d’automation OLE.|  
|[DISP_PROPERTY_EX](#disp_property_ex)|Les noms de fonctions Get et Set et définit une propriété d’automation OLE.|  
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Définit une propriété d’automation OLE avec notification.|  
|[DISP_PROPERTY_PARAM](#disp_property_param)|Définit une propriété automation OLE qui prend des paramètres et des noms de fonctions Get et Set.|  
|[DISP_DEFVALUE](#disp_defvalue)|Rend une propriété existante de la valeur par défaut d’un objet.|  
  
##  <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP  
 Si un `CCmdTarget`-classe dérivée dans votre programme prend en charge OLE Automation, que classe doit fournir une table de dispatch pour exposer ses méthodes et propriétés.  
  
```   
DECLARE_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>Notes  
 Utilisez le `DECLARE_DISPATCH_MAP` (macro) à la fin de votre déclaration de classe. Puis, dans le. Les fonctions de fichier CPP qui définit le membre de la classe, utilisez le `BEGIN_DISPATCH_MAP` (macro). Puis inclure les entrées de la macro pour chacun de votre classe d’exposée de méthodes et propriétés ( `DISP_FUNCTION`, `DISP_PROPERTY`, et ainsi de suite). Enfin, utilisez la `END_DISPATCH_MAP` (macro).  
  
> [!NOTE]
>  Si vous déclarez des membres après `DECLARE_DISPATCH_MAP`, vous devez spécifier un nouveau type d’accès ( **public**, `private`, ou `protected`) pour eux.  
  
 Les Assistants code et Assistant Application aident à créer des classes Automation et maintenance des tables de dispatch. Pour plus d’informations sur les tables de dispatch, consultez [serveurs Automation](../../mfc/automation-servers.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  

##  <a name="begin_dispatch_map"></a>  BEGIN_DISPATCH_MAP  
 Déclare la définition de votre table de dispatch.  
  
```  
BEGIN_DISPATCH_MAP(theClass, baseClass)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Spécifie le nom de la classe qui possède cette table de dispatch.  
  
 `baseClass`  
 Spécifie le nom de la classe de base de `theClass`.  
  
### <a name="remarks"></a>Notes  
 Dans le fichier d’implémentation (.cpp) qui définit les fonctions membres pour votre classe, démarrez la table de dispatch avec la `BEGIN_DISPATCH_MAP` (macro), ajouter des entrées de la macro pour chacun de vos fonctions de distribution et les propriétés et terminer la table de dispatch avec la `END_DISPATCH_MAP` (macro).  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h  

##  <a name="end_dispatch_map"></a>  END_DISPATCH_MAP  
 Met fin à la définition de votre table de dispatch.  
  
```   
END_DISPATCH_MAP()  
```  
  
### <a name="remarks"></a>Notes  
 Il doit être utilisé conjointement avec `BEGIN_DISPATCH_MAP`.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h  

##  <a name="disp_function"></a>  DISP_FUNCTION  
 Définit une fonction d’automatisation OLE dans une table de dispatch.  
  
```   
DISP_FUNCTION(
  theClass, 
  pszName, 
  pfnMember, 
  vtRetVal, 
  vtsParams)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Nom de la classe.  
  
 `pszName`  
 Nom externe de la fonction.  
  
 `pfnMember`  
 Nom de la fonction membre.  
  
 `vtRetVal`  
 Valeur spécifiant le type de retour de la fonction.  
  
 `vtsParams`  
 Une liste séparée par des espaces d’une ou plusieurs des constantes en spécifiant la liste des paramètres de la fonction.  
  
### <a name="remarks"></a>Notes  
 Le `vtRetVal` argument est de type **VARTYPE**. Les valeurs possibles suivantes pour cet argument sont effectuées à partir de la `VARENUM` énumération :  
  
|Symbole|Type de retour|  
|------------|-----------------|  
|`VT_EMPTY`|`void`|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATE**|  
|`VT_BSTR`|`BSTR`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 Le `vtsParams` argument est une liste séparée par des espaces, des valeurs à partir de la **VTS_** constantes. Un ou plusieurs de ces valeurs séparées par des espaces (non par des virgules) spécifie la liste des paramètres de la fonction. Par exemple : 
  
 [!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]  
  
 Spécifie une liste contenant un entier court, suivi d’un pointeur vers un entier court.  
  
 Le **VTS_** constantes et leurs significations sont les suivants :  
  
|Symbole|Type de paramètre|  
|------------|--------------------|  
|**VTS_I2**|`Short`|  
|**VTS_I4**|`Long`|  
|**VTS_R4**|**Float**|  
|**VTS_R8**|`Double`|  
|**VTS_CY**|**CY const** ou **CY\***|  
|**VTS_DATE**|**DATE**|  
|**VTS_BSTR**|`LPCSTR`|  
|**VTS_DISPATCH**|`LPDISPATCH`|  
|**VTS_SCODE**|`SCODE`|  
|**VTS_BOOL**|**BOOL**|  
|**VTS_VARIANT**|**VARIANTE const\***  ou **VARIANT &**|  
|**VTS_UNKNOWN**|`LPUNKNOWN`|  
|**VTS_PI2**|**courte\***|  
|**VTS_PI4**|**Long\***|  
|**VTS_PR4**|**float\***|  
|**VTS_PR8**|**double\***|  
|**VTS_PCY**|**CY\***|  
|**VTS_PDATE**|**DATE\***|  
|**VTS_PBSTR**|**BSTR\***|  
|**VTS_PDISPATCH**|**LPDISPATCH\***|  
|**VTS_PSCODE**|**SCODE\***|  
|**VTS_PBOOL**|**BOOL\***|  
|**VTS_PVARIANT**|**VARIANT\***|  
|**VTS_PUNKNOWN**|**LPUNKNOWN\***|  
|**VTS_NONE**|Aucun paramètre|  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h 

##  <a name="disp_property"></a>  DISP_PROPERTY  
 Définit une propriété d’automation OLE dans une table de dispatch.  
  
```   
DISP_PROPERTY(
  theClass, 
  pszName, 
  memberName, 
  vtPropType)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Nom de la classe.  
  
 `pszName`  
 Nom externe de la propriété.  
  
 `memberName`  
 Nom de la variable de membre dans lequel la propriété est stockée.  
  
 `vtPropType`  
 Valeur qui spécifie le type de propriété.  
  
### <a name="remarks"></a>Notes  
 Le `vtPropType` argument est de type **VARTYPE**. Les valeurs possibles pour cet argument sont tirées de la `VARENUM` énumération :  
  
|Symbole|**Type de propriété**|  
|------------|-----------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATE**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  
  
 Quand un client externe modifie la valeur de la variable de membre spécifiée par la propriété `memberName` change ; il n’existe aucune notification de la modification.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h 

##  <a name="disp_property_ex"></a>  DISP_PROPERTY_EX  
 Définit une propriété d’OLE automation et le nom les fonctions utilisées pour obtenir et définir la valeur de propriété dans une table de dispatch.  
  
```   
DISP_PROPERTY_EX(
  theClass, 
  pszName, 
  memberGet, 
  memberSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Nom de la classe.  
  
 `pszName`  
 Nom externe de la propriété.  
  
 `memberGet`  
 Nom de la fonction de membre utilisée pour obtenir la propriété.  
  
 `memberSet`  
 Nom de la fonction membre permet de définir la propriété.  
  
 `vtPropType`  
 Valeur qui spécifie le type de propriété.  
  
### <a name="remarks"></a>Notes  
 Le `memberGet` et `memberSet` fonctions ont des signatures déterminés par le `vtPropType` argument. Le `memberGet` fonction n’accepte aucun argument et retourne une valeur du type spécifié par `vtPropType`. Le `memberSet` fonction accepte un argument de type spécifié par `vtPropType` et ne retourne rien.  
  
 Le `vtPropType` argument est de type **VARTYPE**. Les valeurs possibles pour cet argument sont tirées de la `VARENUM` énumération. Pour obtenir la liste de ces valeurs, consultez la section Notes pour le `vtRetVal` paramètre dans [DISP_FUNCTION](#disp_function). Notez que `VT_EMPTY`, mentionné dans le `DISP_FUNCTION` Remarques, n’est pas autorisée en tant que type de données de propriété.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h 

##  <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY  
 Définit une propriété d’automation OLE avec notification dans une table de dispatch.  
  
```   
DISP_PROPERTY_NOTIFY(
  theClass, 
  szExternalName, 
  memberName, 
  pfnAfterSet, 
  vtPropType)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Nom de la classe.  
  
 `szExternalName`  
 Nom externe de la propriété.  
  
 `memberName`  
 Nom de la variable de membre dans lequel la propriété est stockée.  
  
 `pfnAfterSet`  
 Nom de la fonction de notification pour `szExternalName`.  
  
 `vtPropType`  
 Valeur qui spécifie le type de propriété.  
  
### <a name="remarks"></a>Notes  
 Contrairement aux propriétés définies avec `DISP_PROPERTY`, une propriété définie avec `DISP_PROPERTY_NOTIFY` appelle automatiquement la fonction spécifiée par `pfnAfterSet` lorsque la propriété est modifiée.  
  
 Le `vtPropType` argument est de type **VARTYPE**. Les valeurs possibles pour cet argument sont tirées de la `VARENUM` énumération :  
  
|Symbole|**Type de propriété**|  
|------------|-----------------------|  
|`VT_I2`|**short**|  
|`VT_I4`|**long**|  
|`VT_R4`|**float**|  
|`VT_R8`|**double**|  
|`VT_CY`|**CY**|  
|`VT_DATE`|**DATE**|  
|`VT_BSTR`|`CString`|  
|**VT_DISPATCH**|`LPDISPATCH`|  
|`VT_ERROR`|`SCODE`|  
|`VT_BOOL`|**BOOL**|  
|**VT_VARIANT**|**VARIANT**|  
|**VT_UNKNOWN**|`LPUNKNOWN`|  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h 

##  <a name="disp_property_param"></a>  DISP_PROPERTY_PARAM  
 Définit une propriété accédée avec distinct **obtenir** et `Set` fonctions membres.  
  
```   
DISP_PROPERTY_PARAM(
  theClass, 
  pszExternalName, 
  pfnGet, 
  pfnSet, 
  vtPropType,
  vtsParams)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Nom de la classe.  
  
 *pszExternalName*  
 Nom externe de la propriété.  
  
 `pfnGet`  
 Nom de la fonction de membre utilisée pour obtenir la propriété.  
  
 `pfnSet`  
 Nom de la fonction membre permet de définir la propriété.  
  
 `vtPropType`  
 Valeur qui spécifie le type de propriété.  
  
 `vtsParams`  
 Une chaîne séparée par des espaces **VTS_** variant les types de paramètres, un pour chaque paramètre.  
  
### <a name="remarks"></a>Notes  
 Contrairement à la `DISP_PROPERTY_EX` macro, cette macro vous permet de spécifier une liste de paramètres pour la propriété. Cela est utile pour implémenter des propriétés qui sont indexées ou paramétrées.  
  
### <a name="example"></a>Exemple  
 Prenons la déclaration suivante d’obtenir et définir des fonctions qui permettent à l’utilisateur de demander une ligne spécifique et une colonne lors de l’accès à la propriété de membre :  
  
 [!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]  
  
 Ces éléments correspondent à ce qui suit `DISP_PROPERTY_PARAM` macro dans la table de dispatch de contrôle :  
  
 [!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]  
  
 Comme autre exemple, considérez la méthode get suivante et définir des fonctions de membre :  
  
 [!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]  
  
 Ces éléments correspondent à ce qui suit `DISP_PROPERTY_PARAM` macro dans la table de dispatch de contrôle :  
  
 [!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h 

##  <a name="disp_defvalue"></a>  DISP_DEFVALUE  
 Rend une propriété existante de la valeur par défaut d’un objet.  
  
```   
DISP_DEFVALUE(theClass, pszName)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Nom de la classe.  
  
 `pszName`  
 Nom externe de la propriété qui représente la « valeur » de l’objet.  
  
### <a name="remarks"></a>Notes  
 À l’aide de la valeur par défaut peut faire de la programmation de votre objet automation plus simple pour les applications Visual Basic.  
  
 La valeur « par défaut » de votre objet est la propriété qui est récupérée ou définie lorsqu’une référence à un objet ne spécifie pas une propriété ou une fonction membre.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h 

## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)

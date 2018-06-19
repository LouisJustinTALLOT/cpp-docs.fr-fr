---
title: Macros de catégorie | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
dev_langs:
- C++
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1eba97ef5253041752d4b8abfcd6ea7300b8492
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362308"
---
# <a name="category-macros"></a>Macros de catégorie
Ces macros définissent les mappages de catégorie.  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Marque le début de la carte de catégorie.|  
|[END_CATEGORY_MAP](#end_category_map)|Marque la fin de la carte de catégorie.|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|Indique les catégories qui sont implémentées par l’objet COM.|  
|[REQUIRED_CATEGORY](#required_category)|Indique les catégories qui sont requis par l’objet COM du conteneur.|  

## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP  
 Marque le début de la carte de catégorie.  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 [in] Le nom de la classe contenant le mappage de catégorie.  
  
### <a name="remarks"></a>Notes  
 Le mappage de catégorie est utilisé pour spécifier les catégories de composant, la classe COM doit implémenter et les catégories qui nécessite de son conteneur.  
  
 Ajouter un [IMPLEMENTED_CATEGORY](#implemented_category) entrée à la carte pour chaque catégorie implémenté par la classe COM. Ajouter un [REQUIRED_CATEGORY](#required_category) entrée à la carte pour chaque catégorie de la classe requiert ses clients à implémenter. Marquer la fin de la carte avec le [END_CATEGORY_MAP](#end_category_map) (macro).  
  
 Les catégories de composant répertoriés dans le mappage seront automatiquement inscrit lorsque le module est enregistré si la classe est associé à un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .  
  
> [!NOTE]
>  ATL utilise le Gestionnaire de catégories de composants standard pour inscrire les catégories de composants. Si le gestionnaire n’est pas présent sur le système lorsque le module est enregistré, l’inscription réussit, mais les catégories de composant ne seront pas enregistrées pour cette classe.  
  
 Pour plus d’informations sur les catégories de composants, consultez [quelles sont les catégories de composants et comment elles fonctionnent](http://msdn.microsoft.com/library/windows/desktop/ms694322) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="end_category_map"></a>  END_CATEGORY_MAP  
 Marque la fin de la carte de catégorie.  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [BEGIN_CATEGORY_MAP](#begin_category_map).  
  
##  <a name="implemented_category"></a>  IMPLEMENTED_CATEGORY  
 Ajouter un `IMPLEMENTED_CATEGORY` macro de votre composant [correspondance des catégories de](#begin_category_map) pour spécifier qu’il doit être enregistré en tant que la mise en œuvre de la catégorie identifiée par le `catID` paramètre.  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>Paramètres  
 `catID`  
 [in] A **CATID** constante ou variable qui contient l’identificateur global unique (GUID) pour la catégorie de mise en œuvre. L’adresse de `catID` sera effectuée et ajoutée à la carte. Consultez le tableau ci-dessous pour une sélection des catégories de stock.  
  
### <a name="remarks"></a>Notes  
 Les catégories de composant répertoriés dans le mappage seront automatiquement inscrit lorsque le module est enregistré si la classe est associé à un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) (macro).  
  
 Les clients peuvent utiliser les informations de catégorie inscrits pour la classe afin de déterminer ses exigences et des fonctions sans avoir à créer une instance de celui-ci.  
  
 Pour plus d’informations sur les catégories de composants, consultez [quelles sont les catégories de composants et comment elles fonctionnent](http://msdn.microsoft.com/library/windows/desktop/ms694322) dans le Kit de développement logiciel Windows.  
  
### <a name="a-selection-of-stock-categories"></a>Une sélection des catégories de Stock  
  
|Description|Symbole|GUID de Registre|  
|-----------------|------------|-------------------|  
|Sûrs pour l’écriture de scripts|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Sûr pour l’initialisation|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Relation contenant-contenu de cadre simple Site|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|liaison de données simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Liaison de données avancée|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Contrôles sans fenêtre|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Objets prenant en charge Internet|Consultez [objets prenant en charge Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) dans le Kit de développement pour un exemple de liste.||  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="required_category"></a>  REQUIRED_CATEGORY  
 Ajouter un `REQUIRED_CATEGORY` macro de votre composant [correspondance des catégories de](#begin_category_map) pour spécifier qu’il doit être enregistré comme nécessitant la catégorie identifiée par le `catID` paramètre.  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>Paramètres  
 `catID`  
 [in] A **CATID** constante ou variable qui contient l’identificateur global unique (GUID) pour la catégorie obligatoire. L’adresse de `catID` sera effectuée et ajoutée à la carte. Consultez le tableau ci-dessous pour une sélection des catégories de stock.  
  
### <a name="remarks"></a>Notes  
 Les catégories de composant répertoriés dans le mappage seront automatiquement inscrit lorsque le module est enregistré si la classe est associé à un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) ou [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) (macro).  
  
 Les clients peuvent utiliser les informations de catégorie inscrits pour la classe afin de déterminer ses exigences et des fonctions sans avoir à créer une instance de celui-ci. Par exemple, un contrôle peut exiger qu’un conteneur prend en charge la liaison de données. Le conteneur peut déterminer s’il possède les fonctionnalités nécessaires pour héberger le contrôle en interrogeant le Gestionnaire de catégorie pour les catégories requis par ce contrôle. Si le conteneur ne prend pas en charge une fonctionnalité requise, il peut refuser héberger l’objet COM.  
  
 Pour plus d’informations sur les catégories de composants, y compris une liste d’exemples, consultez [quelles sont les catégories de composants et comment elles fonctionnent](http://msdn.microsoft.com/library/windows/desktop/ms694322) dans le Kit de développement logiciel Windows.  
  
### <a name="a-selection-of-stock-categories"></a>Une sélection des catégories de Stock  
  
|Description|Symbole|GUID de Registre|  
|-----------------|------------|-------------------|  
|Sûrs pour l’écriture de scripts|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|Sûr pour l’initialisation|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|Relation contenant-contenu de cadre simple Site|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|liaison de données simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|Liaison de données avancée|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|Contrôles sans fenêtre|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|Objets prenant en charge Internet|Consultez [objets prenant en charge Internet](http://msdn.microsoft.com/library/windows/desktop/ms690561) dans le Kit de développement pour un exemple de liste.||  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>Voir aussi  
 [Macros](../../atl/reference/atl-macros.md)

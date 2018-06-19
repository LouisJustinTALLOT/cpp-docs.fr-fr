---
title: Macros de table de l’objet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
dev_langs:
- C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 671fd80bc2c4ad320efb282fd659899756c2ecbc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362941"
---
# <a name="object-map-macros"></a>Macros de mappage d’objet
Ces macros définissent les mappages d’objet et les entrées.  
  
|||  
|-|-|  
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Vous permet de spécifier la description textuelle de l’objet de la classe, qui sera entrée dans la table des objets.|  
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Insère un objet ATL dans la table des objets, met à jour le Registre et crée une instance de l’objet.|  
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Vous pouvez spécifier que l'objet doit être enregistré et initialisé, mais il ne doit pas pouvoir être créé en externe via `CoCreateInstance`.|  

## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
   
##  <a name="declare_object_description"></a>  DECLARE_OBJECT_DESCRIPTION  
 Vous permet de spécifier une description pour votre objet de classe.  
  
```
DECLARE_OBJECT_DESCRIPTION( x )
```  
  
### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Description de l’objet de la classe.  
  
### <a name="remarks"></a>Notes  
 ATL entre cette description dans la table d’objets via la [OBJECT_ENTRY](http://msdn.microsoft.com/en-us/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) (macro).  
  
 `DECLARE_OBJECT_DESCRIPTION` implémente un `GetObjectDescription` (fonction), qui vous permet de substituer le [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) (méthode).  

  
 Le `GetObjectDescription` fonction est appelée par **IComponentRegistrar::GetComponents**. **IComponentRegistrar** est une interface d’automatisation qui vous permet d’enregistrer et annuler l’inscription des composants individuels dans une DLL. Lorsque vous créez un objet de l’inscription de composants avec l’Assistant Projet ATL, l’Assistant appliquent automatiquement la **IComponentRegistrar** interface. **IComponentRegistrar** est généralement utilisée par Microsoft Transaction Server.  
  
 Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]  
  
##  <a name="object_entry_auto"></a>  OBJECT_ENTRY_AUTO  
 Insère un objet ATL dans la table des objets, met à jour le Registre et crée une instance de l’objet.  
  
```
OBJECT_ENTRY_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Paramètres  
 `clsid`  
 [in] CLSID d'une classe COM implémentée par la classe C++ nommée `class`.  
  
 `class`  
 [in] Nom de la classe C++ qui implémente la classe COM représentée par `clsid`.  
  
### <a name="remarks"></a>Notes  
 Les macros d'entrées d'objet sont placées au niveau de la portée globale dans le projet pour assurer la prise en charge de l'inscription, de l'initialisation et de la création d'une classe.  
  
 `OBJECT_ENTRY_AUTO` Insère les pointeurs de fonction de la classe de créateur et de la classe de fabrique de classe de créateur `CreateInstance` fonctions pour cet objet dans le mappage d’objets ATL généré automatiquement. Lorsque [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) est appelée, elle met à jour le Registre système pour chaque objet du mappage d’objets.  

  
 Le tableau ci-dessous décrit comment les informations ajoutées à la carte de l’objet sont obtenues à partir de la classe comme second paramètre de macro.  
  
|Pour plus d’informations|Obtenu à partir de|  
|---------------------|-------------------|  
|Inscription de COM|[Macros de Registre](../../atl/reference/registry-macros.md)|  
|Création de fabrique de classe|[Macros de fabrique de classe](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Création d’une instance|[Macros d’agrégation](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Enregistrement de catégorie de composant|[Macros de catégorie](../../atl/reference/category-macros.md)|  
|Le nettoyage et l’initialisation du niveau de la classe|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

  
##  <a name="object_entry_non_createable_ex_auto"></a>  OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO  
 Vous pouvez spécifier que l'objet doit être enregistré et initialisé, mais il ne doit pas pouvoir être créé en externe via `CoCreateInstance`.  
  
```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Paramètres  
 `clsid`  
 [in] CLSID d'une classe COM implémentée par la classe C++ nommée `class`.  
  
 `class`  
 [in] Nom de la classe C++ qui implémente la classe COM représentée par `clsid`.  
  
### <a name="remarks"></a>Notes  
 Les macros d'entrées d'objet sont placées au niveau de la portée globale dans le projet pour assurer la prise en charge de l'inscription, de l'initialisation et de la création d'une classe.  
  
 `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO` Vous pouvez spécifier qu’un objet doit être enregistré et initialisé (consultez [OBJECT_ENTRY_AUTO](#object_entry_auto) pour plus d’informations), mais il ne doit pas être créé via `CoCreateInstance`.  
  
## <a name="see-also"></a>Voir aussi  
 [Macros](../../atl/reference/atl-macros.md)

---
title: Macros de mappage d’objet
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 73dc924527bac8499adefab3d0d6b51afa500a5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197378"
---
# <a name="object-map-macros"></a>Macros de mappage d’objet

Ces macros définissent des mappages d’objet et les entrées.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Vous permet de spécifier la description textuelle de l’objet de la classe, qui sera entrée dans la table d’objets.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Insère un objet ATL dans la table d’objets, met à jour le Registre et crée une instance de l’objet.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Vous pouvez spécifier que l'objet doit être enregistré et initialisé, mais il ne doit pas pouvoir être créé en externe via `CoCreateInstance`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="declare_object_description"></a>  DECLARE_OBJECT_DESCRIPTION

Vous permet de spécifier une description pour votre objet de classe.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
[in] Description de l’objet de classe.

### <a name="remarks"></a>Notes

ATL entre cette description dans la table d’objets via le [OBJECT_ENTRY_AUTO](#object_entry_auto) macro.

DECLARE_OBJECT_DESCRIPTION implémente un `GetObjectDescription` (fonction), que vous pouvez utiliser pour remplacer le [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) (méthode).

Le `GetObjectDescription` fonction est appelée par `IComponentRegistrar::GetComponents`. `IComponentRegistrar` est une interface d’automatisation qui permet de vous inscrire et annuler l’inscription des composants individuels dans une DLL. Lorsque vous créez un objet de l’inscription de composants avec l’Assistant Projet ATL, l’Assistant implémentera automatiquement le `IComponentRegistrar` interface. `IComponentRegistrar` est généralement utilisé par Microsoft Transaction Server.

Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>  OBJECT_ENTRY_AUTO

Insère un objet ATL dans la table d’objets, met à jour le Registre et crée une instance de l’objet.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[in] Le CLSID d’une classe COM implémentée par le C++ classe nommée *classe*.

*class*<br/>
[in] Le nom de la C++ classe qui implémente la classe COM représentée par *clsid*.

### <a name="remarks"></a>Notes

Les macros d'entrées d'objet sont placées au niveau de la portée globale dans le projet pour assurer la prise en charge de l'inscription, de l'initialisation et de la création d'une classe.

OBJECT_ENTRY_AUTO saisit les pointeurs de fonction de la classe de créateur et de la classe de fabrique de classe de créateur `CreateInstance` fonctions pour cet objet dans le mappage d’objets ATL généré automatiquement. Lorsque [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) est appelée, elle met à jour le Registre système pour chaque objet du mappage d’objets.

Le tableau ci-dessous décrit la façon dont les informations ajoutées au mappage d’objets sont obtenues à partir de la classe donnée comme deuxième paramètre à cette macro.

|Pour plus d’informations|Obtenu à partir de|
|---------------------|-------------------|
|Inscription de COM|[Macros de Registre](../../atl/reference/registry-macros.md)|
|Création de fabriques de classe|[Macros de fabrique de classe](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Création d’une instance|[Macros d’agrégation](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Enregistrement de catégorie de composant|[Macros de catégorie](../../atl/reference/category-macros.md)|
|Le nettoyage et l’initialisation de niveau classe|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

##  <a name="object_entry_non_createable_ex_auto"></a>  OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Vous pouvez spécifier que l'objet doit être enregistré et initialisé, mais il ne doit pas pouvoir être créé en externe via `CoCreateInstance`.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[in] Le CLSID d’une classe COM implémentée par le C++ classe nommée *classe*.

*class*<br/>
[in] Le nom de la C++ classe qui implémente la classe COM représentée par *clsid*.

### <a name="remarks"></a>Notes

Les macros d'entrées d'objet sont placées au niveau de la portée globale dans le projet pour assurer la prise en charge de l'inscription, de l'initialisation et de la création d'une classe.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO vous permet de spécifier qu’un objet doit être enregistré et initialisé (consultez [OBJECT_ENTRY_AUTO](#object_entry_auto) pour plus d’informations), mais il ne doit pas être créé via `CoCreateInstance`.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)

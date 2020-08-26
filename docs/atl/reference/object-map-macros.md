---
title: Macros de mappage d’objets
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 2eb24914561a958a6d6d79dab6779e0ba0a70201
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835283"
---
# <a name="object-map-macros"></a>Macros de mappage d’objets

Ces macros définissent les entrées et les mappages d’objets.

|Nom|Description|
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Vous permet de spécifier la description du texte d’un objet de classe, qui sera entrée dans la table des objets.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Entre un objet ATL dans le mappage d’objet, met à jour le registre et crée une instance de l’objet.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Vous pouvez spécifier que l'objet doit être enregistré et initialisé, mais il ne doit pas pouvoir être créé en externe via `CoCreateInstance`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom. h

## <a name="declare_object_description"></a><a name="declare_object_description"></a> DECLARE_OBJECT_DESCRIPTION

Vous permet de spécifier une description textuelle pour votre objet de classe.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Description de l’objet de classe.

### <a name="remarks"></a>Notes

ATL entre cette description dans le mappage d’objets à l’aide de la macro [OBJECT_ENTRY_AUTO](#object_entry_auto) .

DECLARE_OBJECT_DESCRIPTION implémente une `GetObjectDescription` fonction, que vous pouvez utiliser pour substituer la méthode [CComCoClass :: GetObjectDescription](ccomcoclass-class.md#getobjectdescription) .

La `GetObjectDescription` fonction est appelée par `IComponentRegistrar::GetComponents` . `IComponentRegistrar` est une interface Automation qui vous permet d’inscrire et d’annuler l’enregistrement de composants individuels dans une DLL. Lorsque vous créez un objet d’inscription de composants à l’aide de l’Assistant Projet ATL, l’Assistant implémente automatiquement l' `IComponentRegistrar` interface. `IComponentRegistrar` est généralement utilisé par Microsoft Transaction Server.

Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a> OBJECT_ENTRY_AUTO

Entre un objet ATL dans le mappage d’objet, met à jour le registre et crée une instance de l’objet.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
dans CLSID d’une classe COM implémentée par la classe C++ nommée *Class*.

*class*<br/>
dans Nom de la classe C++ qui implémente la classe COM représentée par *CLSID*.

### <a name="remarks"></a>Notes

Les macros d'entrées d'objet sont placées au niveau de la portée globale dans le projet pour assurer la prise en charge de l'inscription, de l'initialisation et de la création d'une classe.

OBJECT_ENTRY_AUTO entre les pointeurs de fonction de la classe Creator et les fonctions de classe `CreateInstance` de créateur de fabrique de classe pour cet objet dans le mappage d’objet ATL généré automatiquement. Lorsque [CAtlComModule :: RegisterServer](catlcommodule-class.md#registerserver) est appelé, il met à jour le registre système pour chaque objet dans le mappage d’objets.

Le tableau ci-dessous décrit comment les informations ajoutées à la table d’objets sont obtenues à partir de la classe donnée comme deuxième paramètre de cette macro.

|Informations pour|Obtenu à partir de|
|---------------------|-------------------|
|Inscription COM|[Macros de Registre](../../atl/reference/registry-macros.md)|
|Création de la fabrique de classes|[Macros de fabrique de classes](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Création d’instance|[Macros d’agrégation](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Inscription de la catégorie de composant|[Macros de catégorie](../../atl/reference/category-macros.md)|
|Initialisation et nettoyage au niveau de la classe|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a> OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Vous pouvez spécifier que l'objet doit être enregistré et initialisé, mais il ne doit pas pouvoir être créé en externe via `CoCreateInstance`.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
dans CLSID d’une classe COM implémentée par la classe C++ nommée *Class*.

*class*<br/>
dans Nom de la classe C++ qui implémente la classe COM représentée par *CLSID*.

### <a name="remarks"></a>Notes

Les macros d'entrées d'objet sont placées au niveau de la portée globale dans le projet pour assurer la prise en charge de l'inscription, de l'initialisation et de la création d'une classe.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO vous permet de spécifier qu’un objet doit être enregistré et initialisé (consultez [OBJECT_ENTRY_AUTO](#object_entry_auto) pour plus d’informations), mais il ne doit pas pouvoir être créé via `CoCreateInstance` .

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)

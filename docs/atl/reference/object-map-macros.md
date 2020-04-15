---
title: Macros de carte d’objet
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 66a418019ba506a5832c8e3ad86a3764c1186df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326215"
---
# <a name="object-map-macros"></a>Macros de carte d’objet

Ces macros définissent les cartes et les entrées d’objets.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Vous permet de spécifier la description de texte d’un objet de classe, qui sera entré dans la carte de l’objet.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Entre un objet ATL dans la carte de l’objet, met à jour le registre et crée une instance de l’objet.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Vous pouvez spécifier que l'objet doit être enregistré et initialisé, mais il ne doit pas pouvoir être créé en externe via `CoCreateInstance`.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="declare_object_description"></a><a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

Vous permet de spécifier une description de texte pour votre objet de classe.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] La description de l’objet de classe.

### <a name="remarks"></a>Notes

ATL entre cette description dans la carte de l’objet à travers la macro [OBJECT_ENTRY_AUTO.](#object_entry_auto)

DECLARE_OBJECT_DESCRIPTION implémente `GetObjectDescription` une fonction que vous pouvez utiliser pour remplacer la méthode [CComCoClass::GetObjectDescription.](ccomcoclass-class.md#getobjectdescription)

La `GetObjectDescription` fonction est `IComponentRegistrar::GetComponents`appelée par . `IComponentRegistrar`est une interface Automation qui vous permet d’enregistrer et de dépoister des composants individuels dans un DLL. Lorsque vous créez un objet registraire de composant avec l’assistant de projet ATL, l’assistant implémente automatiquement l’interface. `IComponentRegistrar` `IComponentRegistrar`est généralement utilisé par Microsoft Transaction Server.

Pour plus d’informations sur le assistant de projet ATL, voir l’article [Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

Entre un objet ATL dans la carte de l’objet, met à jour le registre et crée une instance de l’objet.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[dans] Le CLSID d’une classe COM mis en œuvre par la classe Cmd nommée *classe*.

*class*<br/>
[dans] Le nom de la classe CMD mettant en œuvre la classe COM représentée par *clsid*.

### <a name="remarks"></a>Notes

Les macros d'entrées d'objet sont placées au niveau de la portée globale dans le projet pour assurer la prise en charge de l'inscription, de l'initialisation et de la création d'une classe.

OBJECT_ENTRY_AUTO entre dans les indications de fonction de la classe `CreateInstance` de créateur et des fonctions de classe-usine de classe de classe de classe de classe de classe de classe de classe de classe pour cet objet dans la carte automatique d’objet ATL. Lorsque [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) est appelé, il met à jour le registre du système pour chaque objet dans la carte de l’objet.

Le tableau ci-dessous décrit comment les informations ajoutées à la carte de l’objet sont obtenues à partir de la classe donnée comme deuxième paramètre à cette macro.

|Informations pour|Obtenu de|
|---------------------|-------------------|
|Inscription COM|[Macros de registre](../../atl/reference/registry-macros.md)|
|Création d’usine de classe|[Macros d’usine de classe](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Création d’instance|[Macros d’agrégation](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Enregistrement de la catégorie des composants|[Macros de catégorie](../../atl/reference/category-macros.md)|
|Initialisation et nettoyage au niveau de la classe|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Vous pouvez spécifier que l'objet doit être enregistré et initialisé, mais il ne doit pas pouvoir être créé en externe via `CoCreateInstance`.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[dans] Le CLSID d’une classe COM mis en œuvre par la classe Cmd nommée *classe*.

*class*<br/>
[dans] Le nom de la classe CMD mettant en œuvre la classe COM représentée par *clsid*.

### <a name="remarks"></a>Notes

Les macros d'entrées d'objet sont placées au niveau de la portée globale dans le projet pour assurer la prise en charge de l'inscription, de l'initialisation et de la création d'une classe.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO vous permet de spécifier qu’un objet [OBJECT_ENTRY_AUTO](#object_entry_auto) doit être enregistré et para initialisé (voir OBJECT_ENTRY_AUTO `CoCreateInstance`pour plus d’informations), mais il ne doit pas être créatable via .

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)

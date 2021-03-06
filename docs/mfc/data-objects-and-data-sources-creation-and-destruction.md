---
description: 'En savoir plus sur : objets de données et sources de données : création et destruction'
title: 'Objets de données et sources de données : création et destruction'
ms.date: 11/04/2016
helpviewer_keywords:
- destroying data objects [MFC]
- object creation [MFC], data source objects
- data sources [MFC], and data objects
- data source objects [MFC], creating
- destruction [MFC], data sources
- data source objects [MFC], destroying
- data objects [MFC], creating
- data objects [MFC], destroying
- data sources [MFC], role
- data sources [MFC], destroying
- destruction [MFC], data objects
- data sources [MFC], creating
ms.assetid: ac216d54-3ca5-4ce7-850d-cd1f6a90d4f1
ms.openlocfilehash: a19c7c2125c7d591bc4df4b3f01553a54de6a18b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206186"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Objets de données et sources de données : création et destruction

Comme expliqué dans l’article [objets de données et sources de données (OLE)](data-objects-and-data-sources-ole.md), les objets de données et les sources de données représentent les deux côtés d’un transfert de données. Cet article explique la création et la destruction des objets et sources pour effectuer les transferts de données correctement, notamment :

- [Création d’objets de données](#_core_creating_data_objects)

- [Destruction d’objets de données](#_core_destroying_data_objects)

- [Création de sources de données](#_core_creating_data_sources)

- [Destruction de sources de données](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a> Création d’objets de données

Les objets de données sont utilisés par l'application de destination : le client ou le serveur. Un objet de données dans l'application de destination est une extrémité d'une connexion entre l'application source et l'application de destination. Un objet de données dans l'application de destination permet d'accéder et d'interagir avec les données de la source de données.

Il existe deux cas fréquents où un objet de données est nécessaire. Lorsque les données sont déposées dans votre application à l’aide de la fonction Glisser-déposer représente le premier cas. Lorsque le collage ou le collage spécial est sélectionné dans le menu Edition représente le deuxième cas.

Dans le cas d’un glissement-dépôt, vous n’avez pas besoin de créer un objet de données. Un pointeur vers un objet de données existant est passé à votre fonction `OnDrop`. Cet objet de données est créé par le framework dans le cadre d'une opération Glisser-déplacer et sera également détruit par celui-ci. Ce n'est pas toujours le cas lorsque le collage est effectué par une autre méthode. Pour plus d’informations, consultez [destruction des objets de données](#_core_destroying_data_objects).

Si l'application effectue une opération de collage ou de collage spécial, vous devrez créer un objet `COleDataObject` et appeler ses fonctions membres `AttachClipboard`. Cette opération permet d'associer l'objet de données aux données dans le Presse-papiers. Vous pouvez ensuite utiliser cet objet de données dans votre fonction de collage.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a> Destruction d’objets de données

Si vous suivez le schéma décrit dans [création d’objets de données](#_core_creating_data_objects), la destruction des objets de données est un aspect trivial des transferts de données. L'objet de données créé dans votre fonction de collage est détruit par MFC lorsque votre fonction de collage retourne son résultat.

Si vous suivez une autre méthode de gestion d'opérations de collage, assurez-vous que l'objet de données est détruit une fois l'opération de collage terminée. Tant que l’objet de données est détruit, il est impossible pour toute application de copier avec succès des données dans le Presse-papiers.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a> Création de sources de données

Les sources de données sont utilisées par la source de transfert de données, qui peut être le côté client ou le côté serveur du transfert des données. Une source de données dans l'application source est une extrémité d'une connexion entre l'application source et l'application de destination. Un objet de données dans l'application de destination est utilisé pour interagir avec les données de la source de données.

Les sources de données sont créées lorsqu'une application doit copier des données dans le Presse-papiers. Un scénario fonctionne comme suit :

1. L'utilisateur sélectionne des données.

1. L’utilisateur choisit **copier** (ou **couper**) dans le menu **Edition** ou commence une opération de glisser-déplacer.

1. Selon la conception du programme, l'application crée un objet `COleDataSource` ou un objet d'une classe dérivée de `COleDataSource`.

1. Les données sélectionnées sont insérées dans la source de données en appelant l'une des fonctions dans les groupes `COleDataSource::CacheData` ou `COleDataSource::DelayRenderData`.

1. L'application appelle la fonction membre `SetClipboard` (ou la fonction membre `DoDragDrop` s'il s'agit d'une opération de type Glisser-déplacer) qui appartient à l'objet créé à l'étape 3.

1. S’il s’agit d’une opération **couper** ou `DoDragDrop` retourne **DROPEFFECT_MOVE**, les données sélectionnées à l’étape 1 sont supprimées du document.

Ce scénario est implémenté par les exemples OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md). Recherchez la source de la classe dérivée de `CView` de chaque application pour toutes les fonctions sauf `GetClipboardData` et `OnGetClipboardData`. Ces deux fonctions figurent dans les implémentations des classes dérivées de `COleClientItem` ou `COleServerItem`. Ces exemples de programmes montrent bien la manière d'implémenter ces concepts.

Une autre situation dans laquelle vous pouvez créer un objet `COleDataSource` se produit si vous modifiez le comportement par défaut d’une opération Glisser-déposer. Pour plus d’informations, consultez l’article [glisser-déplacer OLE : personnaliser l’article glisser-déplacer](drag-and-drop-ole.md#customize-drag-and-drop) .

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a> Destruction de sources de données

Les sources de données doivent être détruites par l’application actuellement chargée de ces derniers. Dans les situations où vous confiez la source de données à OLE, par exemple en appelant [COleDataSource ::D odragdrop](reference/coledatasource-class.md#dodragdrop), vous devez appeler `pDataSrc->InternalRelease` . Par exemple :

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Si vous n'avez pas remis votre source de données à OLE, vous êtes chargé de la détruire, comme pour tout objet C++ classique.

Pour plus d’informations, consultez [glisser-déplacer](drag-and-drop-ole.md), [presse-papiers](clipboard.md)et manipulation d' [objets de données et de sources de données](data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Voir aussi

[Objets de données et sources de données (OLE)](data-objects-and-data-sources-ole.md)<br/>
[COleDataObject, classe](reference/coledataobject-class.md)<br/>
[COleDataSource, classe](reference/coledatasource-class.md)

---
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
ms.openlocfilehash: 58b68ca9597fd2a03cffb2bbab327dbc72d09599
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371216"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Objets de données et sources de données : création et destruction

Comme expliqué dans l’article [Data Objects and Data Sources (OLE)](../mfc/data-objects-and-data-sources-ole.md), les objets de données et les sources de données représentent les deux côtés d’un transfert de données. Cet article explique la création et la destruction des objets et sources pour effectuer les transferts de données correctement, notamment :

- [Création d’objets de données](#_core_creating_data_objects)

- [Détruire les objets de données](#_core_destroying_data_objects)

- [Création de sources de données](#_core_creating_data_sources)

- [Détruire les sources de données](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a>Création d’objets de données

Les objets de données sont utilisés par l'application de destination : le client ou le serveur. Un objet de données dans l'application de destination est une extrémité d'une connexion entre l'application source et l'application de destination. Un objet de données dans l'application de destination permet d'accéder et d'interagir avec les données de la source de données.

Il existe deux cas fréquents où un objet de données est nécessaire. Lorsque les données sont déposées dans votre application à l’aide de la fonction Glisser-déposer représente le premier cas. Lorsque le collage ou le collage spécial est sélectionné dans le menu Edition représente le deuxième cas.

Dans le cas d’un glissement-dépôt, vous n’avez pas besoin de créer un objet de données. Un pointeur vers un objet de données existant est passé à votre fonction `OnDrop`. Cet objet de données est créé par le framework dans le cadre d'une opération Glisser-déplacer et sera également détruit par celui-ci. Ce n'est pas toujours le cas lorsque le collage est effectué par une autre méthode. Pour plus d’informations, voir [Destroying Data Objects](#_core_destroying_data_objects).

Si l'application effectue une opération de collage ou de collage spécial, vous devrez créer un objet `COleDataObject` et appeler ses fonctions membres `AttachClipboard`. Cette opération permet d'associer l'objet de données aux données dans le Presse-papiers. Vous pouvez ensuite utiliser cet objet de données dans votre fonction de collage.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a>Détruire les objets de données

Si vous suivez le schéma décrit dans [La création d’objets de données,](#_core_creating_data_objects)la destruction d’objets de données est un aspect trivial des transferts de données. L'objet de données créé dans votre fonction de collage est détruit par MFC lorsque votre fonction de collage retourne son résultat.

Si vous suivez une autre méthode de gestion d'opérations de collage, assurez-vous que l'objet de données est détruit une fois l'opération de collage terminée. Tant que l’objet de données est détruit, il est impossible pour toute application de copier avec succès des données dans le Presse-papiers.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a>Création de sources de données

Les sources de données sont utilisées par la source de transfert de données, qui peut être le côté client ou le côté serveur du transfert des données. Une source de données dans l'application source est une extrémité d'une connexion entre l'application source et l'application de destination. Un objet de données dans l'application de destination est utilisé pour interagir avec les données de la source de données.

Les sources de données sont créées lorsqu'une application doit copier des données dans le Presse-papiers. Un scénario fonctionne comme suit :

1. L'utilisateur sélectionne des données.

1. L’utilisateur choisit **Copy** (ou **Cut**) dans le menu **Edit** ou commence une opération de drag-and-drop.

1. Selon la conception du programme, l'application crée un objet `COleDataSource` ou un objet d'une classe dérivée de `COleDataSource`.

1. Les données sélectionnées sont insérées dans la source de données en appelant l'une des fonctions dans les groupes `COleDataSource::CacheData` ou `COleDataSource::DelayRenderData`.

1. L'application appelle la fonction membre `SetClipboard` (ou la fonction membre `DoDragDrop` s'il s'agit d'une opération de type Glisser-déplacer) qui appartient à l'objet créé à l'étape 3.

1. S’il s’agit `DoDragDrop` **d’une** opération Cut ou **qu’elle**renvoie DROPEFFECT_MOVE, les données sélectionnées dans l’étape 1 sont supprimées du document.

Ce scénario est mis en œuvre par les échantillons MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md). Recherchez la source de la classe dérivée de `CView` de chaque application pour toutes les fonctions sauf `GetClipboardData` et `OnGetClipboardData`. Ces deux fonctions figurent dans les implémentations des classes dérivées de `COleClientItem` ou `COleServerItem`. Ces exemples de programmes montrent bien la manière d'implémenter ces concepts.

Une autre situation dans laquelle vous pouvez créer un objet `COleDataSource` se produit si vous modifiez le comportement par défaut d’une opération Glisser-déposer. Pour plus d’informations, voir [l’article OLE Drag and drop: Customize drag and drop.](../mfc/drag-and-drop-ole.md#customize-drag-and-drop)

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a>Détruire les sources de données

Les sources de données doivent être détruites par l’application actuellement chargée de ces derniers. Dans les situations où vous remettez la source de données à OLE, comme appeler [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop), vous devez appeler `pDataSrc->InternalRelease`. Par exemple :

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Si vous n'avez pas remis votre source de données à OLE, vous êtes chargé de la détruire, comme pour tout objet C++ classique.

Pour plus d’informations, voir [Drag and Drop](../mfc/drag-and-drop-ole.md), [Clipboard](../mfc/clipboard.md), et [manipulating Data Objects and Data Sources](../mfc/data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Voir aussi

[Objets de données et sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject, classe](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource, classe](../mfc/reference/coledatasource-class.md)

---
title: 'Objets de données et sources de données : manipulation'
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], manipulating
- data sources [MFC], data operations
- data sources [MFC], inserting data
- Clipboard [MFC], determining available formats
- OLE [MFC], data objects
- Clipboard [MFC], passing format information
- data sources [MFC], determining available formats
- delayed rendering [MFC]
- OLE [MFC], data sources
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
ms.openlocfilehash: a08b6ff274c73d301c156d65aa56fbecca49128c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370551"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Objets de données et sources de données : manipulation

Une fois qu’un objet de données ou une source de données a été créé, vous pouvez effectuer un certain nombre d’opérations communes sur les données, telles que l’insertion et la suppression des données, énumérant les formats dans lequel se trouvent les données, et plus encore. Cet article décrit les techniques nécessaires pour terminer les opérations les plus courantes. Les sujets abordés sont les suivants :

- [Insérer des données dans une source de données](#_core_inserting_data_into_a_data_source)

- [Déterminer les formats disponibles dans un objet de données](#_core_determining_the_formats_available_in_a_data_object)

- [Récupération des données à partir d’un objet de données](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>Insérer des données dans une source de données

La façon dont les données sont insérées dans une source de données dépend de la suite de la 1900 fois ou de la demande, et du support dans lequel elles sont fournies. Les possibilités sont les suivantes.

### <a name="supplying-data-immediately-immediate-rendering"></a>Fournir des données immédiatement (rendu immédiat)

- Appelez `COleDataSource::CacheGlobalData` à plusieurs reprises pour chaque format Clipboard dans lequel vous fournissez des données. Passez le format Clipboard à utiliser, une poignée à la mémoire contenant les données et, en option, une structure **FORMATETC** décrivant les données.

     -ou-

- Si vous souhaitez travailler directement avec les structures `COleDataSource::CacheData` **STGMEDIUM,** vous appelez plutôt que dans l’option `COleDataSource::CacheGlobalData` ci-dessus.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Fournir des données à la demande (rendu retardé)

C’est un sujet avancé.

- Appelez `COleDataSource::DelayRenderData` à plusieurs reprises pour chaque format Clipboard dans lequel vous fournissez des données. Passez le format Clipboard à utiliser et, en option, une structure **FORMATETC** décrivant les données. Lorsque les données sont demandées, le cadre appelle, `COleDataSource::OnRenderData`que vous devez remplacer.

     -ou-

- Si vous `CFile` utilisez un objet pour `COleDataSource::DelayRenderFileData` fournir `COleDataSource::DelayRenderData` les données, appelez plutôt que dans l’option précédente. Lorsque les données sont demandées, le cadre appelle, `COleDataSource::OnRenderFileData`que vous devez remplacer.

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>Déterminer les formats disponibles dans un objet de données

Avant qu’une application permette à l’utilisateur de coller des données en elle, il doit savoir s’il existe des formats sur le Clipboard qu’il peut gérer. Pour ce faire, votre demande doit faire ce qui suit :

1. Créez `COleDataObject` un objet et une structure **FORMATETC.**

1. Appelez la fonction `AttachClipboard` membre de l’objet de données pour associer l’objet de données avec les données du Clipboard.

1. Effectuez l’une des actions suivantes :

   - Appelez la fonction `IsDataAvailable` de membre de l’objet de données s’il n’y a qu’un ou deux formats dont vous avez besoin. Cela vous fera gagner du temps dans les cas où les données sur le Clipboard prend en charge beaucoup plus de formats que votre application.

     \- ou -

   - Appelez la fonction `BeginEnumFormats` de membre de l’objet de données pour commencer à énumérer les formats disponibles sur le Clipboard. Appelez `GetNextFormat` ensuite jusqu’à ce que le Clipboard retourne un format que votre application prend en charge ou qu’il n’y ait plus de formats.

Si vous utilisez **ON_UPDATE_COMMAND_UI,** vous pouvez maintenant activer la pâte et, éventuellement, coller des éléments spéciaux sur le menu Edit. Pour ce faire, `CMenu::EnableMenuItem` `CCmdUI::Enable`appelez l’un ou l’autre ou . Pour plus d’informations sur les applications de conteneurs qui devraient faire avec les éléments du menu et quand, voir [Menus et ressources: Ajouts de conteneurs](../mfc/menus-and-resources-container-additions.md).

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>Récupération des données à partir d’un objet de données

Une fois que vous avez décidé d’un format de données, il ne reste plus qu’à récupérer les données de l’objet de données. Pour ce faire, l’utilisateur décide où mettre les données, et l’application appelle la fonction appropriée. Les données seront disponibles dans l’un des supports suivants :

|Moyenne|Fonction à appeler|
|------------|----------------------|
|Mémoire globale`HGLOBAL`( )|`COleDataObject::GetGlobalData`|
|Fichier`CFile`( )|`COleDataObject::GetFileData`|
|**STRUCTURE STGMEDIUM** (`IStorage`)|`COleDataObject::GetData`|

Généralement, le support sera spécifié avec son format Clipboard. Par exemple, un **objet CF_EMBEDDEDSTRUCT** est `IStorage` toujours dans un milieu qui nécessite une structure **STGMEDIUM.** Par conséquent, `GetData` vous utiliseriez parce que c’est la seule de ces fonctions qui peut accepter une structure **STGMEDIUM.**

Pour les cas où le `IStream` `HGLOBAL` format Clipboard est `CFile` dans un ou moyen, le cadre peut fournir un pointeur qui fait référence aux données. L’application peut ensuite utiliser la lecture de fichiers pour obtenir les données de la même manière qu’elle pourrait importer des données d’un fichier. Essentiellement, il s’agit de `OnRenderData` l’interface côté client de la et `OnRenderFileData` les routines dans la source de données.

L’utilisateur peut désormais insérer des données dans le document comme pour toutes les autres données du même format.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Faites glisser et baisser](../mfc/drag-and-drop-ole.md)

- [Presse-papiers](../mfc/clipboard.md)

## <a name="see-also"></a>Voir aussi

[Objets de données et sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject, classe](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource, classe](../mfc/reference/coledatasource-class.md)

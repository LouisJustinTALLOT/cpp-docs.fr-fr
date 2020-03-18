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
ms.openlocfilehash: adbe2a77fb0069e9874ab20a51b3ab08aabbe1f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447001"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Objets de données et sources de données : manipulation

Après avoir créé un objet de données ou une source de données, vous pouvez effectuer un certain nombre d’opérations courantes sur les données, telles que l’insertion et la suppression de données, l’énumération des formats des données et bien plus encore. Cet article décrit les techniques nécessaires pour effectuer les opérations les plus courantes. Les sujets abordés sont les suivants :

- [Insertion de données dans une source de données](#_core_inserting_data_into_a_data_source)

- [Détermination des formats disponibles dans un objet de données](#_core_determining_the_formats_available_in_a_data_object)

- [Récupération de données à partir d’un objet de données](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a>Insertion de données dans une source de données

La façon dont les données sont insérées dans une source de données varie selon que les données sont fournies immédiatement ou à la demande, et dans quelle moyenne elles sont fournies. Les possibilités sont les suivantes.

### <a name="supplying-data-immediately-immediate-rendering"></a>Fournir des données immédiatement (rendu immédiat)

- Appelez `COleDataSource::CacheGlobalData` à plusieurs reprises pour chaque format de presse-papiers dans lequel vous fournissez des données. Transmettez le format du presse-papiers à utiliser, un handle vers la mémoire qui contient les données et, éventuellement, une structure **FORMATETC** décrivant les données.

     -ou-

- Si vous souhaitez travailler directement avec les structures **STGMEDIUM** , vous appelez `COleDataSource::CacheData` au lieu de `COleDataSource::CacheGlobalData` dans l’option ci-dessus.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Fourniture de données à la demande (rendu retardé)

Il s’agit d’une rubrique avancée.

- Appelez `COleDataSource::DelayRenderData` à plusieurs reprises pour chaque format de presse-papiers dans lequel vous fournissez des données. Transmettez le format du presse-papiers à utiliser et, éventuellement, à une structure **FORMATETC** décrivant les données. Lorsque les données sont demandées, le Framework appelle `COleDataSource::OnRenderData`, que vous devez substituer.

     -ou-

- Si vous utilisez un objet `CFile` pour fournir les données, appelez `COleDataSource::DelayRenderFileData` au lieu de `COleDataSource::DelayRenderData` dans l’option précédente. Lorsque les données sont demandées, le Framework appelle `COleDataSource::OnRenderFileData`, que vous devez substituer.

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a>Détermination des formats disponibles dans un objet de données

Avant qu’une application autorise l’utilisateur à coller des données dans celle-ci, elle doit savoir s’il existe des formats dans le presse-papiers qu’elle peut gérer. Pour ce faire, votre application doit effectuer les opérations suivantes :

1. Créez un objet `COleDataObject` et une structure **FORMATETC** .

1. Appelez la fonction membre `AttachClipboard` de l’objet de données pour associer l’objet de données aux données du presse-papiers.

1. Effectuez l’une des actions suivantes :

   - Appelez la fonction membre `IsDataAvailable` de l’objet de données s’il n’existe qu’un ou deux formats dont vous avez besoin. Cela vous permettra de gagner du temps dans les cas où les données du presse-papiers prennent en charge beaucoup plus de formats que votre application.

     \- ou -

   - Appelez la fonction membre `BeginEnumFormats` de l’objet de données pour commencer à énumérer les formats disponibles dans le presse-papiers. Appelez ensuite `GetNextFormat` jusqu’à ce que le presse-papiers retourne un format pris en charge par votre application ou qu’il n’y ait plus de formats.

Si vous utilisez **ON_UPDATE_COMMAND_UI**, vous pouvez maintenant activer les éléments spéciaux coller et, éventuellement, coller dans le menu Edition. Pour ce faire, appelez `CMenu::EnableMenuItem` ou `CCmdUI::Enable`. Pour plus d’informations sur ce que les applications conteneur doivent faire avec les éléments de menu et le moment, consultez [menus et ressources : ajouts de conteneurs](../mfc/menus-and-resources-container-additions.md).

##  <a name="_core_retrieving_data_from_a_data_object"></a>Récupération de données à partir d’un objet de données

Une fois que vous avez choisi un format de données, il ne reste plus qu’à récupérer les données de l’objet de données. Pour ce faire, l’utilisateur décide où placer les données, et l’application appelle la fonction appropriée. Les données seront disponibles dans l’un des supports suivants :

|Moyenne|Fonction à appeler|
|------------|----------------------|
|Mémoire globale (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|Fichier (`CFile`)|`COleDataObject::GetFileData`|
|**STGMEDIUM** , structure (`IStorage`)|`COleDataObject::GetData`|

En règle générale, le support est spécifié en même temps que son format de presse-papiers. Par exemple, un objet **CF_EMBEDDEDSTRUCT** est toujours dans un support `IStorage` qui requiert une structure **STGMEDIUM** . Par conséquent, vous devez utiliser `GetData`, car il s’agit de l’une des seules fonctions qui peuvent accepter une structure **STGMEDIUM** .

Dans les cas où le format du presse-papiers se trouve dans un `IStream` ou `HGLOBAL` moyen, le Framework peut fournir un pointeur `CFile` qui référence les données. L’application peut ensuite utiliser la lecture de fichiers pour obtenir les données à peu près de la même façon qu’elles peuvent importer des données à partir d’un fichier. Pour l’essentiel, il s’agit de l’interface côté client pour les routines `OnRenderData` et `OnRenderFileData` dans la source de données.

L’utilisateur peut maintenant insérer des données dans le document comme pour toutes les autres données dans le même format.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Glisser-déplacer](../mfc/drag-and-drop-ole.md)

- [Presse-papiers](../mfc/clipboard.md)

## <a name="see-also"></a>Voir aussi

[Objets de données et sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject, classe](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource, classe](../mfc/reference/coledatasource-class.md)

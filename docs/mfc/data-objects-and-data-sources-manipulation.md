---
title: 'Objets de données et Sources de données : Manipulation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f276e85be33f3042b19ab7dc6158a4e9f856fb2e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929859"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Objets de données et sources de données : manipulation
Après avoir créé un objet de données ou d’une source de données, vous pouvez effectuer un nombre d’opérations courantes sur les données, telles que l’insertion et la suppression des données, énumérer les formats de données et bien plus encore. Cet article décrit les techniques nécessaires pour effectuer les opérations les plus courantes. Les rubriques traitées ici sont les suivantes :  
  
-   [Insertion de données dans une source de données](#_core_inserting_data_into_a_data_source)  
  
-   [Déterminer les formats disponibles dans un objet de données](#_core_determining_the_formats_available_in_a_data_object)  
  
-   [La récupération des données à partir d’un objet de données](#_core_retrieving_data_from_a_data_object)  
  
##  <a name="_core_inserting_data_into_a_data_source"></a> Insertion de données dans une Source de données  
 Comment les données sont insérées dans une source de données dépend de si les données sont fournies, immédiatement ou à la demande et du support par lequel il est fourni. Les possibilités sont les suivantes.  
  
### <a name="supplying-data-immediately-immediate-rendering"></a>Fourniture immédiate des données (rendu immédiat)  
  
-   Appelez `COleDataSource::CacheGlobalData` à plusieurs reprises pour chaque format de Presse-papiers dans lequel vous fournissez des données. Passez le format du Presse-papiers à utiliser, un handle vers la mémoire contenant les données et, éventuellement, un **FORMATETC** décrivant les données de structure.  
  
     - ou -  
  
-   Si vous souhaitez travailler directement avec **STGMEDIUM** structures, vous appelez `COleDataSource::CacheData` au lieu de `COleDataSource::CacheGlobalData` dans l’option ci-dessus.  
  
### <a name="supplying-data-on-demand-delayed-rendering"></a>En fournissant des données à la demande (rendu retardée)  
 Il s’agit d’une rubrique avancée.  
  
-   Appelez `COleDataSource::DelayRenderData` à plusieurs reprises pour chaque format de Presse-papiers dans lequel vous fournissez des données. Passez le format du Presse-papiers à utiliser et, éventuellement, un **FORMATETC** décrivant les données de structure. Lorsque les données sont demandées, l’infrastructure appellera `COleDataSource::OnRenderData`, que vous devez substituer.  
  
     - ou -  
  
-   Si vous utilisez un `CFile` objet pour fournir les données, appelez `COleDataSource::DelayRenderFileData` au lieu de `COleDataSource::DelayRenderData` dans l’option précédente. Lorsque les données sont demandées, l’infrastructure appellera `COleDataSource::OnRenderFileData`, que vous devez substituer.  
  
##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> Déterminer les Formats disponibles dans un objet de données  
 Avant une application permet à l’utilisateur coller des données, il doit savoir s’il existe des formats dans le Presse-papiers pour qu’il peut gérer. Pour ce faire, votre application doit effectuer le des opérations suivantes :  
  
1.  Créer un `COleDataObject` objet et un **FORMATETC** structure.  
  
2.  Appelez l’objet de données `AttachClipboard` fonction membre pour associer l’objet de données avec les données dans le Presse-papiers.  
  
3.  Effectuez l’une des opérations suivantes :  
  
    -   Appelez l’objet de données `IsDataAvailable` besoin de la fonction membre s’il existe uniquement une ou deux formats. Ce fait gagner du temps dans les cas où les données dans le Presse-papiers prend en charge plus de formats que votre application.  
  
         - ou -  
  
    -   Appelez l’objet de données `BeginEnumFormats` fonction membre à énumérer les formats disponibles dans le Presse-papiers. Appelez ensuite `GetNextFormat` jusqu'à ce que le Presse-papiers renvoie un format prend en charge par votre application, ou il n’existe aucun format plus.  
  
 Si vous utilisez **ON_UPDATE_COMMAND_UI**, vous pouvez désormais activer le collage et, éventuellement, des éléments de collage spécial dans le menu Edition. Pour ce faire, appelez `CMenu::EnableMenuItem` ou `CCmdUI::Enable`. Pour plus d’informations sur le conteneur d’applications doivent faire avec les éléments de menu et, consultez [Menus et ressources : ajouts de conteneurs](../mfc/menus-and-resources-container-additions.md).  
  
##  <a name="_core_retrieving_data_from_a_data_object"></a> La récupération des données à partir d’un objet de données  
 Une fois que vous avez choisi un format de données, il reste qu’à extraire les données de l’objet de données. Pour ce faire, l’utilisateur décide où placer les données, et l’application appelle la fonction appropriée. Les données seront disponibles dans un des supports suivants :  
  
|Moyenne|Fonction à appeler|  
|------------|----------------------|  
|Mémoire globale (`HGLOBAL`)|`COleDataObject::GetGlobalData`|  
|Fichier (`CFile`)|`COleDataObject::GetFileData`|  
|**STGMEDIUM** structure (`IStorage`)|`COleDataObject::GetData`|  
  
 En règle générale, le support sera spécifié, ainsi que son format de Presse-papiers. Par exemple, un **CF_EMBEDDEDSTRUCT** objet se trouve toujours dans un `IStorage` support nécessitant une **STGMEDIUM** structure. Par conséquent, vous utiliseriez `GetData` , car il est le seul de ces fonctions qui peuvent accepter un **STGMEDIUM** structure.  
  
 Pour les cas où le format de Presse-papiers est dans un `IStream` ou `HGLOBAL` moyennes, l’infrastructure peut fournir un `CFile` pointeur qui fait référence aux données. L’application peut utiliser ensuite pour obtenir les données à peu près la même façon qu’il peut importer des données à partir d’un fichier de lecture du fichier. Il s’agit essentiellement de l’interface côté client pour le `OnRenderData` et `OnRenderFileData` routines dans la source de données.  
  
 L’utilisateur peut insérer des données dans le document de la même façon que pour d’autres données dans le même format.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Glisser -déplacer](../mfc/drag-and-drop-ole.md)  
  
-   [Presse-papiers](../mfc/clipboard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objets de données et Sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md)   
 [Classe de COleDataObject](../mfc/reference/coledataobject-class.md)   
 [COleDataSource, classe](../mfc/reference/coledatasource-class.md)

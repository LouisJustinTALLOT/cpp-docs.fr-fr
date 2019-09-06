---
title: Questions relatives à la conception architecturale d'OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: b481d9948d3055247bd284ca794a0fa65905e21b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311867"
---
# <a name="ole-db-architectural-design-issues"></a>Questions relatives à la conception architecturale d'OLE DB

> [!NOTE]
> L’Assistant Consommateur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures. Vous pouvez toujours ajouter la fonctionnalité manuellement. Pour plus d’informations, consultez [Création d’un consommateur sans utiliser l’Assistant](creating-a-consumer-without-using-a-wizard.md).

Réfléchissez aux problèmes suivants avant de commencer la création de votre application OLE DB :

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>Quelle implémentation par programmation utiliserez-vous pour écrire votre application OLE DB ?

Microsoft propose plusieurs bibliothèques pour effectuer cette tâche : une bibliothèque de modèle OLE DB, des attributs OLE DB et les interfaces brutes OLE DB dans le kit de développement logiciel (SDK) OLE DB. Il existe en outre des Assistants pour vous aider à écrire votre programme. Ces implémentations sont décrites dans [Modèles, attributs et autres implémentations OLE DB](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).

## <a name="do-you-need-to-write-your-own-provider"></a>Devez-vous écrire votre propre fournisseur ?

La plupart des développeurs n’ont pas besoin d’écrire leur propre fournisseur. Microsoft propose plusieurs fournisseurs. Chaque fois que vous créez une connexion de données (par exemple, lorsque vous ajoutez un consommateur à votre projet en utilisant l’**Assistant Consommateur OLE DB ATL**), la boîte de dialogue **Propriétés Data Link** répertorie tous les fournisseurs disponibles inscrits sur votre système. Si un des fournisseurs est adapté à votre propre magasin de données et application d’accès aux données, le plus simple consiste à utiliser l’un d’eux. Toutefois, si votre magasin de données ne rentre pas dans une de ces catégories, vous devez créer votre propre fournisseur. Pour plus d’informations sur la création de fournisseurs, consultez [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>Quel est le niveau de prise en charge dont vous avez besoin pour votre consommateur ?

Certains consommateurs peuvent être basiques, tandis que d’autres peuvent être complexes. La fonctionnalité des objets OLE DB est spécifiée par les propriétés. Lorsque vous utilisez l’**Assistant Consommateur OLE DB ATL** pour créer un consommateur ou l’**Assistant Fournisseur de base de données** pour créer un fournisseur, vous définissez les propriétés d’objet appropriées qui vous permettront de fournir un ensemble standard de fonctionnalités. Toutefois, si les classes de consommateur ou fournisseur générées par l’Assistant ne prennent pas en charge tout ce dont vous avez besoin pour faire, vous devez faire référence aux interfaces de ces classes dans le [bibliothèque de modèles OLE DB](../../data/oledb/ole-db-templates.md). Ces interfaces englobent les interfaces brutes OLE DB, ce qui offre une implémentation supplémentaire pour rendre leur utilisation plus simple.

Par exemple, si vous souhaitez mettre à jour des données dans un ensemble de lignes, mais que vous avez oublié de le spécifier lors de la création du consommateur avec l’assistant, vous pouvez spécifier la fonctionnalité après le fait en définissant les propriétés `DBPROP_IRowsetChange` et `DBPROP_UPDATABILITY` sur l’objet de commande. Puis, lorsque l’ensemble de lignes est créé, il disposera de l’interface `IRowsetChange`.

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>Disposez-vous d’un code ancien utilisant une autre technologie d’accès aux données (ADO, ODBC ou DAO) ?

Étant donné les combinaisons possibles de technologies (par exemple, l’utilisation de composants ADO avec des composants OLE DB et la migration de code ODBC vers OLE DB), la documentation Visual C++ ne peut traiter de toutes les situations possibles. Toutefois, de nombreux articles traitant différents scénarios sont disponibles sur les sites web Microsoft suivants :

- [Aide et support Microsoft](https://support.microsoft.com/)

- [Présentation des articles techniques relatifs à Microsoft Data Access](/previous-versions/ms810811(v=msdn.10))

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)

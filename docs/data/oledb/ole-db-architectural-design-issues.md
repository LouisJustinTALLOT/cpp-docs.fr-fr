---
title: Questions relatives à la conception architecturale d'OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: 3e0175c6b554c319a662ffd726023caf7176d9fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461969"
---
# <a name="ole-db-architectural-design-issues"></a>Questions relatives à la conception architecturale d'OLE DB

Considérez les points suivants avant de commencer votre application OLE DB :

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>Quelle implémentation de programmation utiliserez-vous pour écrire votre application OLE DB ?

Microsoft offre plusieurs bibliothèques pour accomplir cette tâche : une bibliothèque de modèles OLE DB, des attributs OLE DB et les interfaces OLE DB brutes dans le SDK OLE DB. En outre, il existe les Assistants vous aident à écrire votre programme. Ces implémentations sont décrites dans [modèles OLE DB, attributs et autres implémentations](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).

## <a name="do-you-need-to-write-your-own-provider"></a>Vous devez écrire votre propre fournisseur ?

La plupart des développeurs n’avez pas besoin d’écrire leur propre fournisseur. Microsoft propose plusieurs fournisseurs. Chaque fois que vous créez une connexion de données (par exemple, lorsque vous ajoutez un consommateur à votre projet en utilisant le **Assistant Consommateur OLE DB ATL**), la **propriétés des liaisons de données** boîte de dialogue répertorie tous les fournisseurs disponibles inscrit sur votre système. Si un des fournisseurs est approprié pour votre propre application d’accès données stocker et les données, le plus simple consiste à faire consiste à utiliser un d’eux. Toutefois, si votre banque de données ne tient pas une de ces catégories, vous devez créer votre propre fournisseur. Pour plus d’informations sur la création de fournisseurs, consultez [les modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>Quel est le niveau de prise en charge avez-vous besoin pour votre consommateur ?

Certains consommateurs peuvent être de base ; tandis que d’autres peuvent être complexes. La fonctionnalité des objets OLE DB est spécifiée par les propriétés. Lorsque vous utilisez le **Assistant Consommateur OLE DB ATL** pour créer un consommateur ou le **Assistant fournisseur de base de données** pour créer un fournisseur, il définit les propriétés d’objet approprié pour vous permettre de vous fournir un ensemble standard de fonctionnalités. Toutefois, si les classes de consommateur ou fournisseur générées par l’Assistant ne prend en charge tout ce dont vous avez besoin pour faire, vous devez faire référence aux interfaces de ces classes dans le [bibliothèque de modèles OLE DB](../../data/oledb/ole-db-templates.md). Ces interfaces englobent les interfaces OLE DB brutes, offrant une implémentation supplémentaire afin de faciliter leur utilisation.

Par exemple, si vous souhaitez mettre à jour des données dans un ensemble de lignes, mais vous avez oublié de le spécifier lorsque vous avez créé le consommateur avec l’Assistant, vous pouvez spécifier les fonctionnalités après le fait en définissant le `DBPROP_IRowsetChange` et `DBPROP_UPDATABILITY` propriétés sur l’objet command. Ensuite, quand l’ensemble de lignes est créé, il a le `IRowsetChange` interface.

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>Avez-vous un code plus ancien à l’aide d’une autre technologie d’accès aux données (ADO, ODBC ou DAO) ?

Étant donné les combinaisons possibles des technologies (par exemple, à l’aide de composants d’ADO avec des composants OLE DB et la migration de code ODBC vers OLE DB), couvrant toutes les situations n’entre pas dans la portée de la documentation de Visual C++. Toutefois, de nombreux articles couvrant différents scénarios sont disponibles sur les sites web Microsoft suivants :

- [Aide et support Microsoft](https://support.microsoft.com/)

- [Vue d’ensemble des articles techniques sur Microsoft Data Access](https://msdn.microsoft.com/library/ms810811.aspx)

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)

---
title: Vue d'ensemble de la programmation OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: d19e98d7c5743207dba224214b0d9a0e9f308e81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608922"
---
# <a name="ole-db-programming-overview"></a>Vue d'ensemble de la programmation OLE DB

OLE DB est une technologie de base de données hautes performances, basé sur COM. Il fournit une méthode courante pour accéder aux données indépendantes de l’écran dans lequel il est stocké. Dans une situation d’entreprise classique, une grande quantité d’informations n’est pas stockée dans des bases de données d’entreprise. Ces informations se trouve dans les systèmes de fichiers (FAT ou NTFS), fichiers à accès séquentiel indexé, bases de données personnelles (par exemple, accès), des feuilles de calcul (par exemple, Excel), applications de planification de projet (par exemple, le projet) et messagerie (par exemple, Outlook). OLE DB vous permet d’accéder à n’importe quel type de magasin de données de la même manière, tant que le magasin de données a un fournisseur OLE DB.

OLE DB permet de développer des applications qui accèdent à diverses sources de données, qu’ils soient SGBD ou non. OLE DB rend possible l’accès universel à l’aide des interfaces COM qui prennent en charge la fonctionnalité SGBD appropriée pour une source de données. COM réduit la duplication inutile des services et agrandie d’interopérabilité non seulement entre les sources de données, mais également entre d’autres applications.

## <a name="benefits-of-com"></a>Avantages de COM

Il s’agit là qu’intervient COM. OLE DB est un ensemble d’interfaces COM. En accédant aux données via un ensemble uniform d’interfaces, vous pouvez organiser une base de données dans une matrice de composants coopératifs.

Selon la spécification COM, OLE DB définit une collection extensible et facile à gérer des interfaces qui facteur et encapsulent des portions cohérentes et réutilisables de SGBD. Ces interfaces définissent les limites des composants de SGBD tels que les conteneurs de ligne, des processeurs de requête et les coordinateurs de transactions, qui permettent l’accès transactionnel uniforme à diverses sources d’informations.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Modèles OLE DB](../../data/oledb/ole-db-templates.md)
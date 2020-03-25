---
title: Vue d'ensemble de la programmation OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
ms.openlocfilehash: 2b855e0917ba9cdbdaa38a92473d7bddb4279101
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210066"
---
# <a name="ole-db-programming-overview"></a>Vue d'ensemble de la programmation OLE DB

OLE DB est une technologie de base de données basée sur COM, hautes performances. Il fournit une méthode courante pour accéder aux données indépendamment du format dans lequel elles sont stockées. Dans une situation professionnelle type, une grande quantité d’informations n’est pas stockée dans les bases de données d’entreprise. Ces informations se trouvent dans les systèmes de fichiers (FAT ou NTFS), les fichiers séquentiels indexés, les bases de données personnelles (par exemple, Access), les feuilles de calcul (comme Excel), les applications de planification de projet (par exemple, Project) et la messagerie électronique (par exemple, Outlook). OLE DB vous permet d’accéder à tout type de magasin de données de la même manière, tant que le magasin de données a un fournisseur de OLE DB.

OLE DB vous permet de développer des applications qui accèdent à diverses sources de données, qu’elles soient SGBD ou non. OLE DB rend possible l’accès universel à l’aide d’interfaces COM qui prennent en charge les fonctionnalités SGBD appropriées pour une source de données donnée. COM réduit la duplication inutile des services et l’interopérabilité optimisée, non seulement parmi les sources de données, mais également entre les autres applications.

## <a name="benefits-of-com"></a>Avantages de COM

C’est là qu’intervient COM. OLE DB est un ensemble d’interfaces COM. En accédant aux données via un ensemble uniforme d’interfaces, vous pouvez organiser une base de données dans une matrice de composants coopérants.

En fonction de la spécification COM, OLE DB définit une collection extensible et gérable d’interfaces qui factoriser et encapsulent des parties cohérentes et réutilisables des fonctionnalités SGBD. Ces interfaces définissent les limites des composants SGBD tels que les conteneurs de lignes, les processeurs de requêtes et les coordinateurs de transactions, qui permettent un accès transactionnel uniforme à diverses sources d’informations.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Modèles OLE DB](../../data/oledb/ole-db-templates.md)

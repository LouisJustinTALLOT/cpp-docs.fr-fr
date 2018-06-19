---
title: Vue d’ensemble de la programmation OLE DB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Universal Data Access
- OLE DB, about OLE DB
ms.assetid: a5a69730-2793-4277-a67d-6f3c8edab6df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fdeca20ad97a09f9d5862fa43be680a2f907405f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106191"
---
# <a name="ole-db-programming-overview"></a>Vue d'ensemble de la programmation OLE DB
OLE DB est une technologie de base de données hautes performances, basé sur COM. Il fournit une méthode courante pour accéder aux données, quel que soit le formulaire dans lequel il est stocké. Dans une situation d’entreprise classique, une grande quantité d’informations est stockée en dehors des bases de données d’entreprise. Ces informations se trouve dans les systèmes de fichiers (tel que FAT ou NTFS), des fichiers séquentiels indexés, des bases de données personnelles (tels que l’accès), des feuilles de calcul (par exemple, Excel), applications de planification de projet (par exemple, le projet) et messagerie (par exemple, Outlook). OLE DB permet d’accéder à n’importe quel type de magasin de données de la même manière, tant que le magasin de données a un fournisseur OLE DB.
  
 OLE DB permet de développer des applications qui accèdent à diverses sources de données, qu’ils soient SGBD ou non. OLE DB rend possible l’accès universel à l’aide des interfaces COM qui prennent en charge la fonctionnalité SGBD appropriée pour une source de données. COM réduit la duplication inutile des services et agrandi l’interopérabilité entre les sources de données mais aussi entre d’autres applications.  
  
## <a name="benefits-of-com"></a>Avantages de COM  
 Il s’agit là qu’intervient COM. OLE DB est un ensemble d’interfaces COM. En accédant aux données via un ensemble uniform d’interfaces, vous pouvez organiser une base de données dans une matrice de composants qui coopèrent.  
  
 Selon la spécification COM, OLE DB définit une collection extensible et facile à gérer des interfaces facteur qui encapsulent des portions cohérentes et réutilisables de fonctions SGBD. Ces interfaces définissent les limites des composants SGBD tels que les conteneurs de lignes, des processeurs de requête et les coordinateurs de transactions, qui permettent l’accès transactionnel uniforme à diverses sources d’informations.  
 
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB](../../data/oledb/ole-db-programming.md)   
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Modèles OLE DB](../../data/oledb/ole-db-templates.md)
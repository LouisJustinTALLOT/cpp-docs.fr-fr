---
title: Fournisseurs et consommateurs OLE DB | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4f0a0ee77b13d6e5231d002cb444ac5a7847f3d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-consumers-and-providers"></a>Fournisseurs et consommateurs OLE DB
L’architecture OLE DB utilise le modèle de fournisseurs et consommateurs. Un consommateur envoie des demandes pour les données. Un fournisseur répond à ces demandes en plaçant des données dans un format tabulaire et retourner au consommateur. N’importe quel appel que le consommateur doit être implémenté dans le fournisseur.  
  
 Techniquement, un consommateur représente n’importe quel code (pas nécessairement un composant OLE DB) système ou une application qui accède aux données via des interfaces OLE DB. Les interfaces sont implémentées dans un fournisseur. Par conséquent, un fournisseur est un composant logiciel qui implémente les interfaces OLE DB pour encapsuler l’accès aux données et l’exposer à d’autres objets (autrement dit, les consommateurs).  
  
 En termes de rôles, un consommateur appelle les méthodes sur des interfaces OLE DB ; un fournisseur OLE DB implémente les interfaces OLE DB requises.  
  
 OLE DB évite les termes du contrat client et serveur, car ces rôles ne sont pas toujours justifiés, en particulier dans une situation multicouche. Étant donné que le consommateur peut être un composant sur une couche qui prend en charge un autre composant, pour appeler un client composant serait à confusion. En outre, un fournisseur parfois agit plus comme un pilote de base de données à un serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB](../../data/oledb/ole-db-programming.md)   
 [Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)
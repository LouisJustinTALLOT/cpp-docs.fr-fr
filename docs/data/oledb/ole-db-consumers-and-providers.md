---
title: Fournisseurs et consommateurs OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b37a06ec89f0e2e21c4332a480e58c605f0d161f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110716"
---
# <a name="ole-db-consumers-and-providers"></a>Fournisseurs et consommateurs OLE DB

L’architecture OLE DB utilise le modèle des consommateurs et des fournisseurs. Un consommateur fait des demandes de données. Un fournisseur répond à ces demandes en plaçant des données dans un format tabulaire et retourner au consommateur. Tout appel au consommateur doit être implémentée dans le fournisseur.  
  
Techniquement, un consommateur représente n’importe quel code (pas nécessairement un composant OLE DB) système ou une application qui accède aux données via des interfaces OLE DB. Les interfaces sont implémentées dans un fournisseur. Par conséquent, un fournisseur est un composant logiciel qui implémente les interfaces OLE DB pour encapsuler l’accès aux données et l’exposer à d’autres objets (autrement dit, les consommateurs).  
  
En termes de rôles, un consommateur appelle les méthodes sur des interfaces OLE DB ; un fournisseur OLE DB implémente les interfaces OLE DB requises.  
  
OLE DB évite les termes du contrat client et serveur, car ces rôles ne sont pas toujours justifiés, en particulier dans une situation d’applications multicouches. Comme un consommateur peut être un composant sur une couche qui prend en charge un autre composant, pour appeler un client composant devrait être déroutant. En outre, un fournisseur parfois agit plus comme un pilote de base de données qu’un serveur.  
  
## <a name="see-also"></a>Voir aussi  

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)
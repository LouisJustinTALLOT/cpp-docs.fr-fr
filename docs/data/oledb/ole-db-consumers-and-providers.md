---
title: Fournisseurs et consommateurs OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
ms.openlocfilehash: f5940ca65e42787c3156a9537cb3f3f6694339c0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031311"
---
# <a name="ole-db-consumers-and-providers"></a>Fournisseurs et consommateurs OLE DB

L’architecture OLE DB utilise le modèle des consommateurs et des fournisseurs. Un consommateur fait des demandes de données. Un fournisseur répond à ces demandes en plaçant des données dans un format tabulaire et retourner au consommateur. Tout appel au consommateur doit être implémentée dans le fournisseur.

Techniquement, un consommateur représente n’importe quel code (pas nécessairement un composant OLE DB) système ou une application qui accède aux données via des interfaces OLE DB. Les interfaces sont implémentées dans un fournisseur. Par conséquent, un fournisseur est un composant logiciel qui implémente les interfaces OLE DB pour encapsuler l’accès aux données et l’exposer à d’autres objets (autrement dit, les consommateurs).

Pour les rôles, un consommateur appelle les méthodes sur des interfaces OLE DB ; un fournisseur OLE DB implémente les interfaces OLE DB requises.

OLE DB évite les termes du contrat client et serveur, car ces rôles ne pas toujours judicieux, en particulier dans une situation d’applications multicouches. Comme un consommateur peut être un composant sur une couche qui prend en charge un autre composant, pour appeler un client composant devrait être déroutant. En outre, un fournisseur parfois agit plus comme un pilote de base de données qu’un serveur.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d'ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)
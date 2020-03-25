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
ms.openlocfilehash: d57ded9d084971c3562fc7f22e6a1a12a4e3368d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210074"
---
# <a name="ole-db-consumers-and-providers"></a>Fournisseurs et consommateurs OLE DB

L’architecture OLE DB utilise le modèle des consommateurs et des fournisseurs. Un consommateur effectue des demandes de données. Un fournisseur répond à ces requêtes en plaçant des données dans un format tabulaire et en les renvoyant au consommateur. Tout appel que le consommateur peut effectuer doit être implémenté dans le fournisseur.

Techniquement défini, un consommateur est tout code système ou d’application (pas nécessairement un composant OLE DB) qui accède aux données via des interfaces OLE DB. Les interfaces sont implémentées dans un fournisseur. Par conséquent, un fournisseur est un composant logiciel qui implémente des interfaces OLE DB pour encapsuler l’accès aux données et les exposer à d’autres objets (autrement dit, aux consommateurs).

Pour les rôles, un consommateur appelle des méthodes sur des interfaces OLE DB ; un fournisseur de OLE DB implémente les interfaces OLE DB nécessaires.

OLE DB évite les termes client et serveur, car ces rôles n’ont pas toujours de sens, surtout dans une situation à plusieurs niveaux. Dans la mesure où un consommateur peut être un composant d’un niveau qui sert un autre composant, l’appel d’un composant client peut prêter à confusion. En outre, un fournisseur agit parfois plus comme un pilote de base de données qu’un serveur.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)

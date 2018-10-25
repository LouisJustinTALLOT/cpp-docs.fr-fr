---
title: Fournisseurs et consommateurs OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
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
ms.openlocfilehash: 4f52177e5fcb34470e606497297985d805a151f6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077593"
---
# <a name="ole-db-consumers-and-providers"></a>Fournisseurs et consommateurs OLE DB

L’architecture OLE DB utilise le modèle des consommateurs et des fournisseurs. Un consommateur fait des demandes de données. Un fournisseur répond à ces demandes en plaçant des données dans un format tabulaire et retourner au consommateur. Tout appel au consommateur doit être implémentée dans le fournisseur.

Techniquement, un consommateur représente n’importe quel code (pas nécessairement un composant OLE DB) système ou une application qui accède aux données via des interfaces OLE DB. Les interfaces sont implémentées dans un fournisseur. Par conséquent, un fournisseur est un composant logiciel qui implémente les interfaces OLE DB pour encapsuler l’accès aux données et l’exposer à d’autres objets (autrement dit, les consommateurs).

Pour les rôles, un consommateur appelle les méthodes sur des interfaces OLE DB ; un fournisseur OLE DB implémente les interfaces OLE DB requises.

OLE DB évite les termes du contrat client et serveur, car ces rôles ne pas toujours judicieux, en particulier dans une situation d’applications multicouches. Comme un consommateur peut être un composant sur une couche qui prend en charge un autre composant, pour appeler un client composant devrait être déroutant. En outre, un fournisseur parfois agit plus comme un pilote de base de données qu’un serveur.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)
---
title: Modèles du fournisseur OLE DB (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a331e72433ca25d280d35edfd33a56402675aea9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112743"
---
# <a name="ole-db-provider-templates-c"></a>Modèles du fournisseur OLE DB (C++)
OLE DB est une partie importante de la stratégie Microsoft Universal Data Access. L’architecture OLE DB permet l’accès de données hautes performances à partir de n’importe quelle source de données. Les données sous forme de tableau sont visibles via OLE DB, qu’elles proviennent d’une base de données. La possibilité de vous donne une quantité considérable d’énergie.  
  
 Comme expliqué dans [fournisseurs et consommateurs OLE DB](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB utilise le concept de fournisseurs et consommateurs. Le consommateur effectue des demandes de données ; le fournisseur retourne des données dans un format tabulaire au consommateur. Du point de vue de la programmation, l’implication la plus importante de ce modèle est que le fournisseur doit implémenter n’importe quel appel qu'au consommateur.  
  
## <a name="what-is-a-provider"></a>Qu’est un fournisseur ?  
 Un fournisseur OLE DB est un ensemble d’objets COM qui servent d’interface appelle à partir d’un objet consommateur, de transfert de données dans un format tabulaire à partir d’une source fiable (appelée magasin de données) pour le consommateur.  
  
 Fournisseurs peuvent être simples ou complexes. Le fournisseur peut prendre en charge une quantité minimale de fonctionnalité ou d’un fournisseur de qualité production complet en implémentant des interfaces supplémentaires. Un fournisseur peut retourner une table, permettre au client de déterminer le format de la table et effectuer des opérations sur ces données.  
  
 Chaque fournisseur implémente un jeu standard d’objets COM pour traiter les demandes du client, avec une signification standard que tout consommateur OLE DB peut accéder aux données à partir de n’importe quel fournisseur, quel que soit le langage (tels que C++ et de base).  
  
 Chaque objet COM contient plusieurs interfaces, dont certains sont requis et certains d'entre eux sont facultatifs. En implémentant les interfaces obligatoires, un fournisseur garantit un niveau minimal de fonctionnalités (appelé conformité) que tout client doit être en mesure d’utiliser. Un fournisseur peut implémenter des interfaces facultatives pour fournir des fonctionnalités supplémentaires. [L’Architecture des modèles OLE DB fournisseur](../../data/oledb/ole-db-provider-template-architecture.md) décrit ces interfaces en détail. Le client doit toujours appeler `QueryInterface` pour déterminer si un fournisseur prend en charge une interface donnée.  
  
## <a name="ole-db-specification-level-support"></a>Prise en charge du niveau de la spécification OLE DB  
 Les modèles du fournisseur OLE DB prend en charge la spécification OLE DB de la version 2.7. À l’aide des modèles du fournisseur OLE DB, vous pouvez implémenter un fournisseur conforme au niveau 0. L’exemple de fournisseur utilise, par exemple, les modèles pour implémenter un serveur de commande non-MS-DOS qui exécute la commande DOS DIR pour interroger le système de fichiers. L’exemple de fournisseur retourne les informations de répertoire dans un ensemble de lignes, qui est le mécanisme OLE DB standard pour retourner des données tabulaires.  
  
 Le type le plus simple de fournisseur de prise en charge par les modèles OLE DB est un fournisseur en lecture seule sans commande. Fournisseurs avec des commandes sont également prises en charge, sont en lecture/écriture et la création des signets la capacité. Vous pouvez implémenter un fournisseur de lecture/écriture en écrivant du code supplémentaire. Les transactions et les ensembles de lignes dynamiques ne sont pas pris en charge par la version actuelle, mais vous pouvez les ajouter si vous le souhaitez.  
  
## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>Lorsque vous avez besoin créer un fournisseur OLE DB ?  
 Vous n’avez pas toujours besoin créer votre propre fournisseur ; Microsoft propose plusieurs fournisseurs standards intégrées dans les **propriétés des liaisons de données** boîte de dialogue dans Visual C++. La raison principale pour créer un fournisseur OLE DB est pour tirer parti de la stratégie de Universal Data Access. Certains des avantages de cette opération sont donc :  
  
-   L’accès aux données via n’importe quel langage tel que C++, Basic et Visual Basic Scripting Edition. Elle permet à différents programmeurs de votre organisation pour accéder aux mêmes données de la même façon, quel que soit de langage qu’ils utilisent.  
  
-   Exposition de vos données à d’autres données sources telles que SQL Server, Excel et Access. Cela peut être très utile si vous souhaitez transférer des données entre différents formats.  
  
-   Participe aux opérations de la source de données croisées (hétérogènes). Cela peut être un moyen très efficace de l’entrepôt de données. À l’aide de fournisseurs OLE DB, vous pouvez conserver les données dans son format natif et toujours être en mesure d’y accéder par une opération simple.  
  
-   Ajout de fonctionnalités supplémentaires à vos données, telles que le traitement des requêtes.  
  
-   Augmente la performance de l’accès aux données en contrôlant la façon dont il est manipulé.  
  
-   Amélioration de la robustesse. Si vous utilisez un format de données propriétaires ce qu’un seul programmeur peut accéder, vous êtes exposés. À l’aide de fournisseurs OLE DB, vous pouvez ouvrir ce format propriétaire à tous vos programmeurs.  
  
## <a name="read-only-and-updatable-providers"></a>Fournisseurs de mettre à jour et en lecture seule  
 Les fournisseurs peuvent varier considérablement la complexité et des fonctionnalités. Il est utile de classer les fournisseurs dans les fournisseurs en lecture seule et les fournisseurs actualisables :  
  
-   Visual C++ 6.0 pris en charge uniquement les fournisseurs en lecture seule. [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md) explique comment créer un fournisseur en lecture seule.  
  
-   Visual C++ prend en charge les fournisseurs actualisables, qui peuvent mettre à jour (modifier) le magasin de données. Pour plus d’informations sur les fournisseurs actualisables, consultez [création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md); le [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) est un exemple d’un fournisseur actualisable.  
  
 Pour plus d'informations, voir :  
  
-   [L’Architecture de modèle du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [Programmation OLE DB](../../data/oledb/ole-db-programming.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données](../data-access-in-cpp.md)   
 [Documentation du Kit de développement OLE DB](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [Référence du programmeur OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx)
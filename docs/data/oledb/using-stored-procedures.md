---
title: À l’aide de procédures stockées | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e5b49daa44fc8c88316134915945ad7ee01bb81a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="using-stored-procedures"></a>Utilisation des procédures stockées
Une procédure stockée est un objet exécutable stocké dans une base de données. Appel d’une procédure stockée est similaire à l’appel d’une commande SQL. À l’aide de procédures stockées sur la source de données (au lieu d’exécuter ou de préparation d’une instruction dans l’application cliente) peut fournir plusieurs avantages, notamment des performances accrues, une charge réseau réduite et améliorer la cohérence et la précision.  
  
 Une procédure stockée peut avoir un nombre quelconque de (y compris zéro) d’entrée ou de paramètres de sortie et pouvez passer une valeur de retour. Vous pouvez soit coder en dur les valeurs de paramètre comme valeurs de données spécifiques ou utilisent un marqueur de paramètre (un point d’interrogation « ? »).  
  
> [!NOTE]
>  CLR SQL Server et les procédures stockées créées à l’aide de Visual C++ doivent être compilés avec les **/CLR : safe** option du compilateur.  
  
 Le fournisseur OLE DB pour SQL Server (SQLOLEDB) prend en charge les mécanismes suivants, que les procédures stockées utilisent pour retourner des données :  
  
-   Chaque instruction SELECT dans la procédure génère un jeu de résultats.  
  
-   La procédure peut retourner des données via des paramètres de sortie.  
  
-   La procédure peut avoir un nombre entier de code de retour.  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser les procédures stockées avec le fournisseur OLE DB pour Jet car ce fournisseur ne prend pas en charge les procédures stockées ; Seules des constantes sont autorisées dans les chaînes de requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
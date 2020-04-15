---
title: Utilisation des procédures stockées
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: 436c796b24b0fa498f2b3f45e848392635b22a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376042"
---
# <a name="using-stored-procedures"></a>Utilisation des procédures stockées

Une procédure stockée est un objet exécutable stocké dans une base de données. Appeler une procédure stockée est similaire à l’invocation d’une commande SQL. L’utilisation de procédures stockées sur la source de données (au lieu d’exécuter ou de préparer une déclaration dans l’application client) peut fournir plusieurs avantages, y compris des performances plus élevées, des frais généraux de réseau réduits et une meilleure cohérence et précision.

Une procédure stockée peut avoir n’importe quel nombre de paramètres d’entrée ou de sortie (y compris zéro) et peut passer une valeur de retour. Vous pouvez soit les valeurs de paramètres de code dur en tant que valeurs de données spécifiques ou utiliser un marqueur de paramètres (un point d’interrogation '?').

> [!NOTE]
> Les procédures stockées CLR SQL Server créées à `/clr:safe` l’aide de Visual CMD doivent être compilées avec l’option compilateur.

Le fournisseur OLE DB de SQL Server (SQLOLEDB) prend en charge les mécanismes suivants que les procédures stockées utilisent pour retourner les données :

- Chaque relevé **SELECT** de la procédure génère un ensemble de résultats.

- La procédure peut retourner des données par l'intermédiaire de paramètres de sortie.

- La procédure peut avoir un code de retour de type entier.

> [!NOTE]
> Vous ne pouvez pas utiliser les procédures stockées avec le fournisseur OLE DB pour Jet parce que ce fournisseur ne prend pas en charge les procédures stockées; seules les constantes sont autorisées dans les cordes de requête.

## <a name="see-also"></a>Voir aussi

[Travailler avec OLE DB Consumer Templates](../../data/oledb/working-with-ole-db-consumer-templates.md)

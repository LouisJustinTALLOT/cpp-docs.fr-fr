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
ms.openlocfilehash: a7e97781d245e236c57942db15d61080d6418cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209272"
---
# <a name="using-stored-procedures"></a>Utilisation des procédures stockées

Une procédure stockée est un objet exécutable stocké dans une base de données. L’appel d’une procédure stockée est similaire à l’appel d’une commande SQL. L’utilisation de procédures stockées sur la source de données (au lieu d’exécuter ou de préparer une instruction dans l’application cliente) peut offrir plusieurs avantages, notamment des performances supérieures, une surcharge réseau réduite et une cohérence et une précision améliorées.

Une procédure stockée peut avoir n’importe quel nombre de paramètres d’entrée ou de sortie (y compris zéro) et peut passer une valeur de retour. Vous pouvez soit coder en dur des valeurs de paramètre en tant que valeurs de données spécifiques, soit utiliser un marqueur de paramètre (un point d’interrogation «  ? »).

> [!NOTE]
>  Les procédures stockées de SQL Server CLR créées C++ à l’aide de Visual doivent être compilées avec l’option de compilateur `/clr:safe`.

Le fournisseur OLE DB pour SQL Server (SQLOLEDB) prend en charge les mécanismes suivants utilisés par les procédures stockées pour retourner des données :

- Chaque instruction **Select** de la procédure génère un jeu de résultats.

- La procédure peut retourner des données par l'intermédiaire de paramètres de sortie.

- La procédure peut avoir un code de retour de type entier.

> [!NOTE]
> Vous ne pouvez pas utiliser de procédures stockées avec le fournisseur de OLE DB pour jet, car ce fournisseur ne prend pas en charge les procédures stockées. seules les constantes sont autorisées dans les chaînes de requête.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)

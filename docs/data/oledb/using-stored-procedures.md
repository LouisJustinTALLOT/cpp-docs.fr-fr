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
ms.openlocfilehash: 7ace43283c56c0c859b193f63e8ca104f6b52a31
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041174"
---
# <a name="using-stored-procedures"></a>Utilisation des procédures stockées

Une procédure stockée est un objet exécutable stocké dans une base de données. Appel d’une procédure stockée est similaire à l’appel d’une commande SQL. À l’aide de procédures stockées sur la source de données (au lieu d’exécuter ou de préparation d’une instruction dans l’application cliente) peut offrir plusieurs avantages, notamment des performances plus élevées, une charge réseau réduite et la précision et cohérence améliorée.

Une procédure stockée peut avoir un nombre quelconque de (zéro compris) d’entrée ou de paramètres de sortie et pouvez passer une valeur de retour. Vous pouvez soit coder en dur de valeurs de paramètre comme valeurs de données spécifiques, soit utilisent un marqueur de paramètre (un point d’interrogation « ? »).

> [!NOTE]
>  Les procédures stockées créées à l’aide de Visual C++ doivent être compilés avec CLR SQL Server la `/clr:safe` option du compilateur.

Le fournisseur OLE DB pour SQL Server (SQLOLEDB) prend en charge les mécanismes suivants, que les procédures stockées utilisent pour retourner des données :

- Chaque **sélectionnez** instruction dans la procédure génère un jeu de résultats.

- La procédure peut retourner des données via des paramètres de sortie.

- La procédure peut avoir un nombre entier de code de retour.

> [!NOTE]
> Vous ne pouvez pas utiliser les procédures stockées avec le fournisseur OLE DB pour Jet, car ce fournisseur ne prend pas en charge les procédures stockées ; Seules les constantes sont autorisées dans les chaînes de requête.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
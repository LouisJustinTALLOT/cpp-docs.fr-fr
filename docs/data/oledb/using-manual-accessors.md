---
title: Utilisation des accesseurs manuels
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: 4a7e2dcde20cdb06a2f4e708149e24ee7144597c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028332"
---
# <a name="using-manual-accessors"></a>Utilisation des accesseurs manuels

Il existe quatre opérations lors du traitement d’une commande inconnue :

- Déterminer les paramètres

- Exécutez la commande

- Déterminer les colonnes de sortie

- S’il existe plusieurs ensembles de lignes de retour

Pour effectuer les opérations suivantes avec les modèles du consommateur OLE DB, utilisez la `CManualAccessor` classe et procédez comme suit :

1. Ouvrir un `CCommand` avec l’objet `CManualAccessor` comme paramètre de modèle.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Interrogez la session pour le `IDBSchemaRowset` interface et utiliser l’ensemble de lignes de paramètres de procédure. Si le `IDBSchemaRowset` interface n’est pas disponible, recherchez le `ICommandWithParameters` interface. Appelez `GetParameterInfo` pour plus d’informations. Si aucune interface n’est disponible, vous pouvez supposer qu'aucun paramètre.

1. Pour chaque paramètre, appelez `AddParameterEntry` pour ajouter les paramètres et les définir.

1. Ouvrez l’ensemble de lignes, mais la valeur est le paramètre de liaison **false**.

1. Appelez `GetColumnInfo` pour récupérer les colonnes de sortie. Utilisez `AddBindEntry` pour ajouter la colonne de sortie à la liaison.

1. Appelez `GetNextResult` pour déterminer si plusieurs ensembles de lignes sont disponibles. Répétez les étapes 2 à 5.

Pour obtenir un exemple d’accesseur manuel, consultez `CDBListView::CallProcedure` dans le [DBVIEWER](https://github.com/Microsoft/VCSamples) exemple.

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)
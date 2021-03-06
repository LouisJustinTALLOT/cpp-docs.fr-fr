---
description: 'En savoir plus sur : utilisation des accesseurs manuels'
title: Utilisation des accesseurs manuels
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: 73363be83e06a3eeced114dc90c65f82601a4a16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332476"
---
# <a name="using-manual-accessors"></a>Utilisation des accesseurs manuels

Il y a quatre choses à faire lors du traitement d’une commande inconnue :

- Déterminer les paramètres

- Exécuter la commande

- Déterminer les colonnes de sortie

- Vérifier s’il existe plusieurs ensembles de lignes de retour

Pour effectuer ces opérations avec les modèles de consommateur OLE DB, utilisez la `CManualAccessor` classe et procédez comme suit :

1. Ouvrez un `CCommand` objet avec `CManualAccessor` comme paramètre de modèle.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Interrogez la session de l' `IDBSchemaRowset` interface et utilisez l’ensemble de lignes de paramètres de procédure. Si l' `IDBSchemaRowset` interface n’est pas disponible, recherchez l' `ICommandWithParameters` interface. Appelez `GetParameterInfo` pour obtenir des informations. Si aucune interface n’est disponible, vous pouvez supposer qu’il n’y a aucun paramètre.

1. Pour chaque paramètre, appelez `AddParameterEntry` pour ajouter les paramètres et les définir.

1. Ouvrez l’ensemble de lignes, mais définissez le paramètre de liaison sur **`false`** .

1. Appelez `GetColumnInfo` pour récupérer les colonnes de sortie. Utilisez `AddBindEntry` pour ajouter la colonne de sortie à la liaison.

1. Appelez `GetNextResult` pour déterminer si d’autres ensembles de lignes sont disponibles. Répétez les étapes 2 à 5.

Pour obtenir un exemple d’accesseur manuel, consultez `CDBListView::CallProcedure` dans l’exemple [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)

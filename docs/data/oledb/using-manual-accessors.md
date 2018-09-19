---
title: Utilisation des accesseurs manuels | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5aa7f72cc76f80e2304faf93ca0c6198c505e88a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101640"
---
# <a name="using-manual-accessors"></a>Utilisation des accesseurs manuels

Il existe quatre opérations lors du traitement d’une commande inconnue :  
  
- Déterminer les paramètres  
  
- Exécutez la commande  
  
- Déterminer les colonnes de sortie  
  
- S’il existe plusieurs ensembles de lignes de retour  
  
Pour ce faire, avec les modèles du consommateur OLE DB, utilisez la `CManualAccessor` classe et procédez comme suit :  
  
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
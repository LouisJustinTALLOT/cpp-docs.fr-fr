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
ms.openlocfilehash: c732bcf45f2dfbd4927366670aed6bfbdcfb4721
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679985"
---
# <a name="using-manual-accessors"></a>Utilisation des accesseurs manuels
Il existe quatre opérations lors du traitement d’une commande inconnue :  
  
-   Déterminer les paramètres  
  
-   Exécutez la commande  
  
-   Déterminer les colonnes de sortie  
  
-   S’il existe plusieurs ensembles de lignes de retour  
  
 Pour ce faire, avec les modèles du consommateur OLE DB, utilisez la `CManualAccessor` classe et procédez comme suit :  
  
1.  Ouvrir un `CCommand` avec l’objet `CManualAccessor` comme paramètre de modèle.  
  
    ```cpp  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  Interrogez la session pour le `IDBSchemaRowset` interface et utiliser l’ensemble de lignes de paramètres de procédure. Si le `IDBSchemaRowset` interface n’est pas disponible, recherchez le `ICommandWithParameters` interface. Appelez `GetParameterInfo` pour plus d’informations. Si aucune interface n’est disponible, vous pouvez supposer qu'aucun paramètre.  
  
3.  Pour chaque paramètre, appelez `AddParameterEntry` pour ajouter les paramètres et les définir.  
  
4.  Ouvrez l’ensemble de lignes, mais la valeur est le paramètre de liaison **false**.  
  
5.  Appelez `GetColumnInfo` pour récupérer les colonnes de sortie. Utilisez `AddBindEntry` pour ajouter la colonne de sortie à la liaison.  
  
6.  Appelez `GetNextResult` pour déterminer si plusieurs ensembles de lignes sont disponibles. Répétez les étapes 2 à 5.  
  
 Pour obtenir un exemple d’accesseur manuel, consultez `CDBListView::CallProcedure` dans le [DBVIEWER](https://github.com/Microsoft/VCSamples) exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des accesseurs](../../data/oledb/using-accessors.md)
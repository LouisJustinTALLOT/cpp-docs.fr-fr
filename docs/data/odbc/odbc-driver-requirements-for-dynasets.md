---
title: Pilote ODBC requis pour les Dynasets | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f6c7a9282ce1516ae3410307b74a66ba34adbcea
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082707"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Pilote ODBC requis pour les feuilles de réponse dynamiques

Dans les classes de base de données ODBC MFC, feuilles de réponse dynamiques sont des jeux d’enregistrements avec des propriétés dynamiques ; ils restent synchronisés avec la source de données d’une certaine façon. Feuilles de réponse dynamiques MFC (mais pas avant uniquement de recordsets) nécessitent un pilote ODBC conforme au niveau 2 API. Si le pilote pour votre [source de données](../../data/odbc/data-source-odbc.md) est conforme à l’API de 1 niveau ensemble, vous pouvez toujours utiliser les instantanés modifiables et en lecture seule et recordsets avant uniquement, mais pas les dynasets. Toutefois, un pilote de niveau 1 peut prendre en charge les dynasets si elle prend en charge l’extraction étendue et les curseurs.  
  
Dans la terminologie ODBC, feuilles de réponse dynamiques et les instantanés sont appelés curseurs. Un curseur est un mécanisme utilisé pour assurer le suivi de sa position dans un jeu d’enregistrements. Pour plus d’informations sur la configuration requise des pilotes pour les dynasets, consultez [Dynaset](../../data/odbc/dynaset.md). Pour plus d’informations sur les curseurs, consultez le [Open Database Connectivity (ODBC)](/previous-versions/windows/desktop/ms710252) SDK dans la documentation MSDN.  
  
> [!NOTE]
>  Pour les jeux d’enregistrements modifiables, votre pilote ODBC doit prendre en charge les deux instructions de mise à jour positionnée ou `::SQLSetPos` fonction API ODBC. Si les deux sont pris en charge, MFC utilise `::SQLSetPos` pour plus d’efficacité. Pour les instantanés, vous pouvez également utiliser la bibliothèque de curseurs, qui fournit la prise en charge requis pour les instantanés (curseurs statiques et les instructions de mise à jour positionnée).  
  
## <a name="see-also"></a>Voir aussi  

[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)
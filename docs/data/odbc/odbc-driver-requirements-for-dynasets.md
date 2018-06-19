---
title: Pilote ODBC requis pour les Dynasets | Documents Microsoft
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
ms.openlocfilehash: d9fad26440cea2c8ec2efd7d07dacb83547252e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089231"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Pilote ODBC requis pour les feuilles de réponse dynamiques
Dans les classes de base de données ODBC MFC, feuilles de réponse dynamiques sont des jeux d’enregistrements avec des propriétés dynamiques ; ils restent synchronisés avec la source de données de certaines façons. Feuilles de réponse dynamiques MFC (mais pas avant uniquement des recordsets) nécessitent un pilote ODBC conforme au niveau 2 d’API. Si le pilote pour votre [source de données](../../data/odbc/data-source-odbc.md) est conforme à l’API de 1 au niveau de la valeur, vous pouvez toujours utiliser les instantanés modifiables et en lecture seule et recordsets avant uniquement, mais pas les dynasets. Toutefois, un pilote de niveau 1 peut prendre en charge les dynasets si elle prend en charge extraction étendue et les curseurs pilotés par jeu de clés.  
  
 Dans la terminologie ODBC, feuilles de réponse dynamiques et les instantanés sont appelés curseurs. Un curseur est un mécanisme utilisé pour assurer le suivi de sa position dans un jeu d’enregistrements. Pour plus d’informations sur les pilotes requis pour les feuilles de réponse dynamiques, consultez [Dynaset](../../data/odbc/dynaset.md). Pour plus d’informations sur les curseurs, consultez le [connectivité ODBC (Open Database)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK dans la documentation MSDN.  
  
> [!NOTE]
>  Pour les recordsets modifiables, votre pilote ODBC doit prendre en charge les deux instructions de mise à jour positionnée ou **:: SQLSetPos** fonction d’API ODBC. Si les deux sont pris en charge, MFC utilise **:: SQLSetPos** par souci d’efficacité. Pour les instantanés, vous pouvez également utiliser la bibliothèque de curseurs, qui fournit la prise en charge requise pour les instantanés (curseurs statiques et les instructions de mise à jour positionnée).  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)
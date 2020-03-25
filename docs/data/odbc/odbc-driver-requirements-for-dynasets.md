---
title: Pilote ODBC requis pour les feuilles de réponse dynamiques
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: 3507a5ee7dcfb8bf4f4eee12ef9264c16ad904c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213107"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Pilote ODBC requis pour les feuilles de réponse dynamiques

Dans les classes de base de données ODBC MFC, les feuilles de réponse dynamiques sont des jeux d’enregistrements avec des propriétés dynamiques. elles restent synchronisées avec la source de données de certaines façons. Les feuilles de réponse dynamiques MFC (mais pas les recordsets avant uniquement) requièrent un pilote ODBC avec la conformité de l’API de niveau 2. Si le pilote de votre [source de données](../../data/odbc/data-source-odbc.md) est conforme à l’ensemble d’API de niveau 1, vous pouvez toujours utiliser les instantanés mis à jour et en lecture seule et les recordsets avant uniquement, mais pas les feuilles de réponse dynamiques. Toutefois, un pilote de niveau 1 peut prendre en charge les feuilles de réponse dynamiques s’il prend en charge l’extraction étendue et les curseurs pilotés par jeu de clés.

Dans la terminologie ODBC, les feuilles de réponse dynamiques et les instantanés sont appelés curseurs. Un curseur est un mécanisme utilisé pour assurer le suivi de sa position dans un jeu d’enregistrements. Pour plus d’informations sur la configuration requise des pilotes pour les feuilles de réponse dynamiques, consultez [feuille de réponse dynamique](../../data/odbc/dynaset.md). Pour plus d’informations sur les curseurs, consultez le kit de développement logiciel [(SDK) Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) dans la documentation MSDN.

> [!NOTE]
>  Pour les jeux d’enregistrements modifiables, votre pilote ODBC doit prendre en charge les instructions de mise à jour positionnée ou la fonction API ODBC `::SQLSetPos`. Si les deux sont pris en charge, MFC utilise `::SQLSetPos` pour plus d’efficacité. Pour les instantanés, vous pouvez également utiliser la bibliothèque de curseurs, qui fournit la prise en charge requise pour les instantanés pouvant être mis à jour (les curseurs statiques et les instructions de mise à jour positionnée).

## <a name="see-also"></a>Voir aussi

[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)

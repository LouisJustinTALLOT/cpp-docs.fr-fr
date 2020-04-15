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
ms.openlocfilehash: c612e8ea91882a6e744a8f47afe0decbeba85358
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367213"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Pilote ODBC requis pour les feuilles de réponse dynamiques

Dans les classes de base de données MFC ODBC, les dynasets sont des enregistrements avec des propriétés dynamiques; ils restent synchronisés avec la source de données de certaines façons. Les dynasets MFC (mais pas les enregistrements avant seulement) nécessitent un pilote ODBC avec la conformité API de niveau 2. Si le pilote de votre [source de données](../../data/odbc/data-source-odbc.md) est conforme à l’ensemble API de niveau 1, vous pouvez toujours utiliser des instantanés mis à jour et uniquement lisibles et des enregistrements avant seulement, mais pas des colorants. Cependant, un pilote de niveau 1 peut prendre en charge les dynasets s’il prend en charge les curseurs d’aller chercher et les curseurs à clé.

Dans la terminologie de l’ODBC, les dynasets et les instantanés sont appelés curseurs. Un curseur est un mécanisme utilisé pour garder une trace de sa position dans un jeu d’enregistrement. Pour plus d’informations sur les exigences du conducteur pour les dynasets, voir [Dynaset](../../data/odbc/dynaset.md). Pour plus d’informations sur les curseurs, consultez le [SDK de connectivité à base de données ouverte (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) dans la documentation MSDN.

> [!NOTE]
> Pour les enregistrements à jour, votre pilote ODBC doit `::SQLSetPos` prendre en charge les instructions de mise à jour positionnées ou la fonction API ODBC. Si les deux sont `::SQLSetPos` pris en charge, MFC utilise pour l’efficacité. Alternativement, pour les instantanés, vous pouvez utiliser la bibliothèque de curseurs, qui fournit le support requis pour les instantanés actualisés (curseurs statiques et instructions de mise à jour positionnées).

## <a name="see-also"></a>Voir aussi

[ODBC Basics](../../data/odbc/odbc-basics.md)

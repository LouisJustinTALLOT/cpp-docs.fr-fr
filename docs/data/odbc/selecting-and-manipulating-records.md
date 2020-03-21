---
title: Sélection et manipulation d'enregistrements
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 8388cd5c8c53a4595dc9b44430077421ee8680bf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079796"
---
# <a name="selecting-and-manipulating-records"></a>Sélection et manipulation d'enregistrements

> [!NOTE]
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez quand même créer un consommateur manuellement.

Normalement, quand vous sélectionnez des enregistrements d’une source de données à l’aide d’une instruction SQL **SELECT**, vous obtenez un jeu de résultats, qui est un jeu d’enregistrements issus d’une table ou d’une requête. Avec les classes de base de données, vous utilisez un objet recordset pour sélectionner le jeu de résultats et y accéder. Il s’agit d’un objet d’une classe propre à l’application que vous dérivez de la classe [CRecordset](../../mfc/reference/crecordset-class.md). Quand vous définissez une classe recordset, vous spécifiez la source de données à lui associer, la table à utiliser et les colonnes de la table. L’Assistant Application MFC ou **Ajouter une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) crée une classe avec une connexion à une source de données spécifique. Les Assistants écrivent la fonction membre [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) de la classe `CRecordset` pour retourner le nom de table.

À l’aide d’un objet [CRecordset](../../mfc/reference/crecordset-class.md) au moment de l’exécution, vous pouvez :

- Examiner les champs de données de l’enregistrement actuel.

- Filtrer ou trier le recordset.

- Personnaliser l’instruction SQL **SELECT** par défaut.

- Faire défiler les enregistrements sélectionnés.

- Ajouter, mettre à jour ou supprimer des enregistrements (si la source de données et le recordset sont modifiables).

- Tester si le recordset permet de réinterroger et d’actualiser son contenu.

Quand vous avez fini d’utiliser l’objet recordset, vous le fermez et le détruisez. Pour plus d’informations sur les recordsets, consultez [Recordset (ODBC)](../../data/odbc/recordset-odbc.md).

## <a name="see-also"></a>Voir aussi

[ODBC et MFC](../../data/odbc/odbc-and-mfc.md)
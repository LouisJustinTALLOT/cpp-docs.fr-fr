---
title: Modifications possibles dans le code par défaut (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: fc448ae1e13025a83b33386c2845bdf7bb4d5eec
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038633"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Modifications possibles dans le code par défaut (Accès aux données MFC)

Le [Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md) écrit une classe de recordset qui sélectionne tous les enregistrements dans une table unique. Vous souhaiterez souvent modifier ce comportement d'une plusieurs des manières suivantes :

- Définir un filtre ou un ordre de tri pour le recordset. Effectuer cette opération dans `OnInitialUpdate` une fois que l’objet recordset construit mais avant son `Open` fonction membre est appelée. Pour plus d’informations, consultez [jeu d’enregistrements : Filtrage d’enregistrements (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) et [jeu d’enregistrements : Tri d’enregistrements (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).

- Paramétrer le recordset. Spécifiez la valeur réelle du paramètre au moment de l'exécution après le filtre. Pour plus d’informations, consultez [jeu d’enregistrements : Paramétrage d’un Recordset (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- Passez la chaîne SQL personnalisée à la [Open](../mfc/reference/crecordset-class.md#open) fonction membre. Pour une description de ce que vous pouvez accomplir avec cette technique, consultez [SQL : Personnalisation de l’instruction SQL du Recordset (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Voir aussi

[À l’aide d’une vue d’enregistrement](../data/using-a-record-view-mfc-data-access.md)
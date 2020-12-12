---
description: En savoir plus sur les modifications que vous pouvez apporter au code par défaut (accès aux données MFC)
title: Modifications possibles dans le code par défaut (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: 431144eeaf7ef0a2413e4d9e3931016c2505d338
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181447"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Modifications possibles dans le code par défaut (Accès aux données MFC)

L' [Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md) écrit une classe de Recordset qui sélectionne tous les enregistrements dans une table unique. Vous souhaiterez souvent modifier ce comportement d'une plusieurs des manières suivantes :

- Définir un filtre ou un ordre de tri pour le recordset. Procédez ainsi dans `OnInitialUpdate` après la construction de l’objet Recordset mais avant l’appel de la `Open` fonction membre. Pour plus d’informations, consultez [Recordset : filtrage d’enregistrements (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) et [Recordset : tri d’enregistrements (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).

- Paramétrer le recordset. Spécifiez la valeur réelle du paramètre au moment de l'exécution après le filtre. Pour plus d’informations, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- Transmettez une chaîne SQL personnalisée à la fonction membre [Open](../mfc/reference/crecordset-class.md#open) . Pour plus d’informations sur ce que vous pouvez accomplir avec cette technique, consultez [SQL : personnalisation de l’instruction SQL du recordset (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Voir aussi

[Utilisation d'une vue de l'enregistrement](../data/using-a-record-view-mfc-data-access.md)

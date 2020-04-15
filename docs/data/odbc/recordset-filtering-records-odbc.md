---
title: "Recordset : filtrage d'enregistrements (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 56b8c4f52ec294f58a760e1309d32aa81286ddec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367019"
---
# <a name="recordset-filtering-records-odbc"></a>Recordset : filtrage d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Ce sujet explique comment filtrer un ensemble d’enregistrements afin qu’il ne sélectionne qu’un sous-ensemble particulier des enregistrements disponibles. Par exemple, vous pouvez sélectionner uniquement les sections de classe pour un cours particulier, comme MATH101. Un filtre est une condition de recherche définie par le contenu d’une clause SQL **WHERE.** Lorsque le cadre l’annexe à la déclaration SQL du dossier, la clause **WHERE** limite la sélection.

Vous devez établir le filtre d’un objet de recordet `Open` après avoir construit l’objet, mais avant d’appeler sa fonction de membre (ou avant d’appeler la `Requery` fonction membre pour un objet enregistreur existant dont `Open` la fonction de membre a été appelée précédemment).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Pour spécifier un filtre pour un objet de recordet

1. Construire un nouvel objet de la `Requery` composition des enregistrements (ou préparer à appeler pour un objet existant).

1. Définissez la valeur du membre [des données m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) de l’objet.

   Le filtre est une chaîne à durée nulle qui contient le contenu de la clause SQL **WHERE,** mais pas le mot clé **Où**. Par exemple, utilisez :

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  La chaîne littérale "MATH101" est montrée avec des guillemets uniques ci-dessus. Dans la spécification ODBC SQL, des citations simples sont utilisées pour désigner une chaîne de caractère littérale. Vérifiez la documentation de votre chauffeur ODBC pour les exigences de citation de votre DBMS dans cette situation. Cette syntaxe est également discutée plus loin vers la fin de ce sujet.

1. Définissez toutes les autres options dont vous avez besoin, comme l’ordre de tri, le mode de verrouillage ou les paramètres. Spécifier un paramètre est particulièrement utile. Pour plus d’informations sur la paramétrisation de votre filtre, voir [Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Appelez `Open` pour le nouvel `Requery` objet (ou pour un objet précédemment ouvert).

> [!TIP]
> L’utilisation de paramètres dans votre filtre est potentiellement la méthode la plus efficace pour récupérer les enregistrements.

> [!TIP]
> Les filtres Recordset sont utiles pour [joindre les](../../data/odbc/recordset-performing-a-join-odbc.md) tables et pour l’utilisation de paramètres basés sur les informations [obtenues](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) ou calculées au moment de l’exécution.

Le dossier ne sélectionne que les enregistrements qui répondent à l’état de recherche que vous avez spécifié. Par exemple, pour spécifier le `strCourseID` filtre de cours décrit ci-dessus (en supposant qu’une variable actuellement définie, par exemple, à "MATH101"), faire ce qui suit:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Le recordet contient des enregistrements pour toutes les sections de classe pour MATH101.

Remarquez comment la chaîne de filtre a été définie dans l’exemple ci-dessus, à l’aide d’une variable de chaîne. C’est l’usage typique. Mais supposons que vous vouliez spécifier la valeur littérale 100 pour l’ID de cours. Le code suivant montre comment définir correctement la chaîne de filtre avec une valeur littérale :

```
m_strFilter = "StudentID = '100'";   // correct
```

Notez l’utilisation de caractères de citation unique; si vous définissez la chaîne de filtre directement, la chaîne de filtre **n’est pas**:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

La citation ci-dessus est conforme aux spécifications de l’ODBC, mais certains DBMS peuvent nécessiter d’autres caractères de citation. Pour plus d’informations, voir [SQL: Customizing Your Recordset’s SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
> Si vous choisissez de remplacer la chaîne SQL par défaut du `Open`recordet en passant votre propre chaîne SQL à , vous ne devriez pas définir un filtre si votre chaîne personnalisée a une clause **WHERE.** Pour plus d’informations sur la suppression de la SQL par défaut, voir [SQL: Customizing Your Recordset’s SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : tri d'enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Recordset : sélection d'enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Recordset : modification des enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Recordset : verrouillage d'enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

---
description: 'En savoir plus sur : Recordset : filtrage d’enregistrements (ODBC)'
title: "Recordset : filtrage d'enregistrements (ODBC)"
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 15cf191f7a5a037c032726bc4f16a5774fb2857b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322336"
---
# <a name="recordset-filtering-records-odbc"></a>Recordset : filtrage d'enregistrements (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique comment filtrer un jeu d’enregistrements afin qu’il ne sélectionne qu’un sous-ensemble particulier des enregistrements disponibles. Par exemple, vous souhaiterez peut-être sélectionner uniquement les sections de classe pour un cours particulier, par exemple MATH101. Un filtre est une condition de recherche définie par le contenu d’une clause SQL **Where** . Lorsque le Framework l’ajoute à l’instruction SQL de l’ensemble d’enregistrements, la clause **Where** limite la sélection.

Vous devez établir un filtre d’objet Recordset après avoir construit l’objet, mais avant d’appeler `Open` la fonction membre (ou avant d’appeler la `Requery` fonction membre pour un objet Recordset existant dont la `Open` fonction membre a été appelée précédemment).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Pour spécifier un filtre pour un objet Recordset

1. Construisez un nouvel objet Recordset (ou préparez `Requery` l’appel d’un objet existant).

1. Définissez la valeur du membre de données [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) de l’objet.

   Le filtre est une chaîne se terminant par un caractère null qui contient le contenu de la clause SQL **Where** , mais pas le mot clé **Where**. Par exemple, utilisez :

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  La chaîne littérale « MATH101 » est indiquée par des guillemets simples ci-dessus. Dans la spécification ODBC SQL, les guillemets simples sont utilisés pour désigner un littéral de chaîne de caractères. Dans ce cas, consultez la documentation de votre pilote ODBC pour obtenir les spécifications relatives aux devis de votre SGBD. Cette syntaxe est également abordée plus loin à la fin de cette rubrique.

1. Définissez les autres options dont vous avez besoin, telles que l’ordre de tri, le mode de verrouillage ou les paramètres. La spécification d’un paramètre est particulièrement utile. Pour plus d’informations sur le paramétrage de votre filtre, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Appelez `Open` pour le nouvel objet (ou `Requery` pour un objet précédemment ouvert).

> [!TIP]
> L’utilisation de paramètres dans votre filtre est potentiellement la méthode la plus efficace pour récupérer des enregistrements.

> [!TIP]
> Les filtres d’ensemble d’enregistrements sont utiles pour [joindre](../../data/odbc/recordset-performing-a-join-odbc.md) des tables et pour utiliser des [paramètres](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) basés sur des informations obtenues ou calculées au moment de l’exécution.

Le jeu d’enregistrements sélectionne uniquement les enregistrements qui répondent aux critères de recherche que vous avez spécifiés. Par exemple, pour spécifier le filtre de cours décrit ci-dessus (en supposant qu’une variable `strCourseID` est actuellement définie, par exemple, sur « MATH101 »), procédez comme suit :

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Le jeu d’enregistrements contient les enregistrements de toutes les sections de classe pour MATH101.

Notez que la chaîne de filtrage a été définie dans l’exemple ci-dessus, à l’aide d’une variable de chaîne. Il s’agit de l’utilisation courante. Mais supposons que vous souhaitiez spécifier la valeur littérale 100 pour l’ID de cours. Le code suivant montre comment définir correctement la chaîne de filtrage avec une valeur littérale :

```
m_strFilter = "StudentID = '100'";   // correct
```

Notez l’utilisation de guillemets simples ; Si vous définissez la chaîne de filtre directement, la chaîne de filtrage n’est **pas**:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

Le devis indiqué ci-dessus est conforme à la spécification ODBC, mais certains SGBD peuvent nécessiter d’autres guillemets. Pour plus d’informations, consultez [SQL : personnalisation de l’instruction SQL du recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
> Si vous choisissez de remplacer la chaîne SQL par défaut du Recordset en passant votre propre chaîne SQL à `Open` , vous ne devez pas définir de filtre si votre chaîne personnalisée contient une clause **Where** . Pour plus d’informations sur le remplacement de l’instruction SQL par défaut, consultez [SQL : personnalisation de l’instruction SQL du recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Recordset : sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Recordset : modification des enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

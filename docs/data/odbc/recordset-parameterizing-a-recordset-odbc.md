---
title: 'Recordset : Paramétrage d’un recordset (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: 499741693009fb27df58f0ed3cde046d5e6b8c2d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707787"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Recordset : Paramétrage d’un recordset (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Vous souhaiterez peut-être parfois pouvoir sélectionner des enregistrements au moment de l’exécution, en utilisant les informations que vous avez calculées ou fournies par votre utilisateur final. Les paramètres de recordset vous permettent d’atteindre cet objectif.

Cette rubrique explique :

- [L’objectif d’un recordset paramétré](#_core_parameterized_recordsets).

- [Quand et pourquoi vous pouvez souhaiter paramétrer un recordset](#_core_when_to_use_parameters).

- [Comment déclarer des membres de données de paramètre dans votre classe de recordset](#_core_parameterizing_your_recordset_class).

- [Comment passer des informations sur les paramètres à un objet recordset au moment de l’exécution](#_core_passing_parameter_values_at_run_time).

##  <a name="_core_parameterized_recordsets"></a> Recordsets paramétrés

Un recordset paramétré vous permet de passer des informations sur les paramètres au moment de l’exécution. Cette fonctionnalité a deux effets utiles :

- Cela peut entraîner une meilleure vitesse d’exécution.

- Cela vous permet de générer une requête au moment de l’exécution en fonction des informations qui ne sont pas à votre disposition au moment du design, comme les informations fournies par votre utilisateur ou calculées au moment de l’exécution.

Quand vous appelez `Open` pour exécuter la requête, le recordset utilise les informations sur les paramètres pour compléter son instruction **SQL SELECT**. Vous pouvez paramétrer n’importe quel recordset.

##  <a name="_core_when_to_use_parameters"></a> Quand utiliser des paramètres

Les utilisations courantes de paramètres sont notamment les suivantes :

- Passage d’arguments d’exécution à une requête prédéfinie.

   Pour passer des paramètres à une procédure stockée, vous devez spécifier une instruction **CALL** ODBC personnalisée complète (avec des espaces réservés de paramètres) quand vous appelez `Open`, en remplaçant l’instruction SQL par défaut du recordset. Pour plus d’informations, consultez [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) dans les *informations de référence sur la bibliothèque de classes*, ainsi que les articles [SQL : Personnalisation de l’instruction SQL du recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) et [Recordset : Déclaration de la classe d’une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

- Exécution efficace de nombreuses nouvelles interrogations avec des informations sur les paramètres différentes.

   Par exemple, chaque fois que votre utilisateur final recherche des informations sur un élève particulier dans la base de données d’inscription des élèves, vous pouvez spécifier le nom ou l’ID de l’élève comme paramètre fourni par l’utilisateur. Ensuite, quand vous appelez la fonction membre `Requery` de votre recordset, la requête sélectionne uniquement l’enregistrement de cet élève.

   La chaîne de filtre de votre recordset, stockée dans `m_strFilter`, pourrait se présenter comme suit :

    ```cpp
    "StudentID = ?"
    ```

   Supposons que vous obtenez l’ID d’élève dans la variable `strInputID`. Quand vous définissez un paramètre sur `strInputID` (par exemple, l’ID d’élève 100), la valeur de la variable est liée à l’espace réservé de paramètre représenté par le « ? » dans la chaîne de filtre.

   Affectez la valeur du paramètre comme suit :

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   Vous ne voulez pas configurer une chaîne de filtre de la manière suivante :

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   Pour savoir comment utiliser des guillemets de façon appropriée pour les chaînes de filtre, consultez [Recordset : Filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

   La valeur du paramètre est différente chaque fois que vous réinterrogez le recordset pour un nouvel ID d’élève.

   > [!TIP]
   > L’utilisation d’un paramètre est plus efficace que simplement un filtre. Pour un recordset paramétré, la base de données doit traiter une seule fois une instruction SQL **SELECT**. Pour un recordset filtré sans paramètres, l’instruction **SELECT** doit être traitée chaque fois que vous effectuez une nouvelle interrogation (`Requery`) avec une nouvelle valeur de filtre.

Pour plus d’informations sur les filtres, consultez [Recordset : Filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

##  <a name="_core_parameterizing_your_recordset_class"></a> Paramétrage de votre classe de recordset

> [!NOTE]
> Cette section s’applique aux objets dérivés de `CRecordset` où la récupération de lignes en bloc n’a pas été implémentée. Si vous utilisez la récupération de lignes en bloc, l’implémentation de paramètres est un processus similaire. Pour plus d’informations, consultez [Recordset : récupération d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Avant de créer votre classe de recordset, déterminez les paramètres dont vous avez besoin, leurs types de données et la façon dont le recordset les utilise.

#### <a name="to-parameterize-a-recordset-class"></a>Pour paramétrer une classe de recordset

> [!NOTE] 
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez toujours créer cette fonctionnalité manuellement.

1. Exécutez l’[Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) à partir de l’option **Ajouter une classe** pour créer la classe.

1. Spécifiez des membres de données de champ pour les colonnes du recordset.

1. Une fois que l’Assistant a écrit la classe dans un fichier de votre projet, accédez au fichier .h et ajoutez manuellement un ou plusieurs membres de données de paramètre à la déclaration de classe. Cet ajout pourrait ressembler à l’exemple suivant, représentant une partie d’un instantané de la classe conçue pour répondre à la requête « Quels élèves sont en terminale ? ».

    ```cpp
    class CStudentSet : public CRecordset
    {
    // Field/Param Data
        CString m_strFirstName;
        CString m_strLastName;
        CString m_strStudentID;
        CString m_strGradYear;

        CString m_strGradYrParam;
    };
    ```

   Ajoutez vos membres de données de paramètre après les membres de données de champ générés par l’Assistant. La convention est d’ajouter le mot « Param » à chaque nom de paramètre défini par l’utilisateur.

1. Modifiez la définition de fonction membre [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) dans le fichier .cpp. Ajoutez un appel de fonction RFX pour chaque membre de données de paramètre que vous avez ajouté à la classe. Pour plus d’informations sur l’écriture de vos fonctions RFX, consultez [Record Field Exchange : Fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Faites précéder les appels de fonction RFX pour les paramètres d’un appel unique à :

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. Dans le constructeur de votre classe de recordset, incrémentez le nombre de paramètres, `m_nParams`.

   Pour plus d’informations, consultez [Record Field Exchange : Utilisation du code de l’Assistant](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).

1. Quand vous écrivez le code qui crée un objet de recordset de cette classe, placez un symbole « ? » (point d’interrogation) à chaque endroit de l’instruction SQL où un paramètre doit être remplacé.

   Au moment de l’exécution, les espaces réservés « ? » sont remplis, dans l’ordre, par les valeurs de paramètre que vous passez. Le premier membre de données de paramètre défini après l’appel à [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) remplace le premier « ? » dans la chaîne SQL, le deuxième membre de données de paramètre remplace le deuxième « ? », etc.

> [!NOTE]
> L’ordre des paramètres est important : l’ordre des appels de fonction RFX pour les paramètres dans votre fonction `DoFieldExchange` doit correspondre à l’ordre des espaces réservés de paramètres dans votre chaîne SQL.

> [!TIP]
> La chaîne avec laquelle vous travaillerez est très probablement celle que vous spécifiez (le cas échéant) pour le membre de données [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) de la classe, mais certains pilotes ODBC peuvent autoriser des paramètres dans d’autres clauses SQL.

##  <a name="_core_passing_parameter_values_at_run_time"></a> Passage de valeurs de paramètre au moment de l’exécution

Vous devez spécifier des valeurs de paramètre avant d’appeler `Open` (pour un nouvel objet recordset) ou `Requery` (pour un objet recordset existant).

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Pour passer des valeurs de paramètre à un objet recordset au moment de l’exécution

1. Construisez l’objet recordset.

1. Préparez une ou plusieurs chaînes, comme la chaîne `m_strFilter`, contenant l’instruction SQL ou des parties de celle-ci. Mettez des espaces réservés « ? » aux endroits où les informations sur les paramètres doivent être placées.

1. Affectez une valeur de paramètre d’exécution à chaque membre de données de paramètre de l’objet.

1. Appelez la fonction membre `Open` (ou `Requery` pour un recordset existant).

Par exemple, supposons que vous voulez spécifier une chaîne de filtre pour votre recordset en utilisant des informations obtenues au moment de l’exécution. Partons du principe que vous avez précédemment construit un recordset de la classe `CStudentSet`, appelé `rsStudents`, et que vous voulez maintenant le réinterroger pour un type particulier d’informations sur les élèves.

```cpp
// Set up a filter string with
// parameter placeholders
rsStudents.m_strFilter = "GradYear <= ?";

// Obtain or calculate parameter values
// to pass--simply assigned here
CString strGradYear = GetCurrentAcademicYear( );

// Assign the values to parameter data members
rsStudents.m_strGradYrParam = strGradYear;

// Run the query
if( !rsStudents.Requery( ) )
    return FALSE;
```

Le recordset contient les enregistrements des élèves dont les enregistrements remplissent les conditions spécifiées par le filtre, lequel a été construit à partir de paramètres d’exécution. Dans le cas présent, le recordset contient les enregistrements de tous les élèves en classe de terminale.

> [!NOTE]
>  Si nécessaire, vous pouvez définir la valeur d’un membre de données de paramètre sur Null à l’aide de [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). De même, vous pouvez vérifier si un membre de données de paramètre a la valeur Null à l’aide de [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : Ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Recordset : Sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
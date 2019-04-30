---
title: 'Recordset : Paramétrage d’un Recordset (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: df67256c54cae3e2adb054d653d3e58bb91dd631
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397755"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Recordset : Paramétrage d’un Recordset (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Vous pouvez parfois être en mesure de sélectionner des enregistrements en cours d’exécution, à l’aide des informations que vous avez calculé ou obtenu à partir de votre utilisateur final. Les paramètres vous permettent d’atteindre cet objectif.

Cette rubrique explique :

- [L’objectif d’un recordset paramétré](#_core_parameterized_recordsets).

- [Quand et pourquoi vous souhaiterez peut-être paramétrer un jeu d’enregistrements](#_core_when_to_use_parameters).

- [Comment déclarer des membres de données dans votre classe de jeu d’enregistrements de paramètre](#_core_parameterizing_your_recordset_class).

- [Comment passer des informations sur les paramètres à un objet recordset en cours d’exécution](#_core_passing_parameter_values_at_run_time).

##  <a name="_core_parameterized_recordsets"></a> Jeux d’enregistrements paramétrés

Un jeu d’enregistrements paramétrable vous permet de passer des informations sur les paramètres en cours d’exécution. Cela a deux effets utiles :

- Elle peut entraîner une meilleure vitesse d’exécution.

- Il vous permet de créer une requête en cours d’exécution, en fonction des informations non disponibles pour vous au moment du design, telles que les informations obtenues à partir de votre utilisateur ou calculée au moment de l’exécution.

Lorsque vous appelez `Open` pour exécuter la requête, le jeu d’enregistrements utilise les informations de paramètre pour effectuer son **SQL SELECT** instruction. Vous pouvez paramétrer n’importe quel jeu d’enregistrements.

##  <a name="_core_when_to_use_parameters"></a> Quand utiliser les paramètres

Utilisations courantes de paramètres sont les suivantes :

- Passage des arguments d’exécution pour une requête prédéfinie.

   Pour passer des paramètres à une procédure stockée, vous devez spécifier un ODBC personnalisée complète **appeler** instruction — avec des espaces réservés de paramètre, lorsque vous appelez `Open`, remplaçant l’instruction SQL de jeu d’enregistrements par défaut. Pour plus d’informations, consultez [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) dans le *Class Library Reference* et [SQL : Personnalisation de l’instruction SQL du Recordset (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) et [jeu d’enregistrements : Déclaration de la classe d’une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

- Exécution efficace de nombreuses requêtes comportant des informations sur les différents paramètres.

   Par exemple, chaque fois que votre utilisateur final recherche des informations sur un étudiant dans la base de données d’inscription de student, vous pouvez spécifier nom ou l’ID de l’étudiant en tant que paramètre fourni par l’utilisateur. Ensuite, lorsque vous appelez votre jeu d’enregistrements `Requery` fonction membre, la requête sélectionne uniquement l’enregistrement de cet étudiant.

   Chaîne de filtre du recordset, stockée dans `m_strFilter`, peut se présenter comme suit :

    ```cpp
    "StudentID = ?"
    ```

   Supposons que vous obtenez l’ID d’étudiant dans la variable `strInputID`. Lorsque vous définissez un paramètre `strInputID` (par exemple, l’ID étudiant 100) la valeur de la variable est liée à l’espace réservé de paramètre représenté par le « ? » dans la chaîne de filtrage.

   Attribuez la valeur du paramètre comme suit :

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   Vous ne serez pas que vous souhaitez configurer une chaîne de filtrage de cette façon :

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   Pour plus d’informations sur l’utilisation appropriée des guillemets pour les chaînes de filtre, consultez [jeu d’enregistrements : Filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

   La valeur du paramètre diffère à chaque fois que vous actualisez le jeu d’enregistrements pour un nouvel ID d’étudiant.

   > [!TIP]
   > À l’aide d’un paramètre est plus efficace que simplement un filtre. Pour un jeu d’enregistrements paramétré, la base de données doit traiter une SQL **sélectionnez** instruction qu’une seule fois. Pour un jeu d’enregistrements filtré sans paramètres, le **sélectionnez** instruction doit être exécutée chaque fois que vous `Requery` avec une nouvelle valeur de filtre.

Pour plus d’informations sur les filtres, consultez [jeu d’enregistrements : Filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

##  <a name="_core_parameterizing_your_recordset_class"></a> Paramétrage de la classe de votre jeu d’enregistrements

> [!NOTE]
> Cette section s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction, l’implémentation des paramètres de lignes en bloc est un processus similaire. Pour plus d’informations, consultez [jeu d’enregistrements : Extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Avant de créer votre classe de jeu d’enregistrements, déterminez les paramètres vous avez besoin, leurs types de données, et comment le jeu d’enregistrements les utilise.

#### <a name="to-parameterize-a-recordset-class"></a>Pour paramétrer une classe de jeu d’enregistrements

1. Exécutez le [Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) de **ajouter une classe** pour créer la classe.

1. Spécifier des membres de données de champ pour les colonnes du jeu d’enregistrements.

1. Une fois que l’Assistant écrit la classe dans un fichier dans votre projet, accédez au fichier .h et ajouter manuellement un ou plusieurs membres de données de paramètre à la déclaration de classe. L’ajout peut ressembler à l’exemple suivant, la partie d’une classe de l’instantané est conçu pour répondre à la requête « les étudiants dans la classe senior ? »

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

   Ajoutez les membres de données de paramètre après les membres de données de champ généré par l’Assistant. La convention consiste à ajouter le mot « Param » pour chaque nom de paramètre défini par l’utilisateur.

1. Modifier le [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) définition de fonction membre dans le fichier .cpp. Ajoutez un appel de fonctions RFX pour chaque membre de données de paramètre ajouté à la classe. Pour plus d’informations sur l’écriture de fonctions RFX, consultez [Record Field Exchange : Fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Faites précéder les appels RFX pour les paramètres avec un seul appel à :

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. Dans le constructeur de votre classe de jeu d’enregistrements, incrémentez le nombre de paramètres, `m_nParams`.

   Pour plus d’informations, consultez [Record Field Exchange : Utilisation de l’Assistant Code](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).

1. Lorsque vous écrivez le code qui crée un objet de jeu d’enregistrements de cette classe, placez un « ? » symbole (point d’interrogation) dans chaque endroit dans l’instruction SQL où un paramètre à remplacer.

   Au moment de l’exécution, « ? » des espaces réservés sont remplis, dans l’ordre, par les valeurs de paramètre que vous passez. Le premier membre de données de paramètre définie après la [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) appel remplace le premier « ? « dans la chaîne SQL, le deuxième membre de données de paramètre remplace le deuxième » ? », et ainsi de suite.

> [!NOTE]
> Ordre des paramètres est important : l’ordre des appels RFX des paramètres dans votre `DoFieldExchange` fonction doit correspondre à l’ordre des espaces réservés de paramètre dans la chaîne SQL.

> [!TIP]
> La chaîne probablement de fonctionner avec est la chaîne que vous spécifiez (le cas échéant) de la classe [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) membre de données, mais certains pilotes ODBC autorisent des paramètres dans d’autres clauses SQL.

##  <a name="_core_passing_parameter_values_at_run_time"></a> Transmission de valeurs de paramètre en cours d’exécution

Vous devez spécifier des valeurs de paramètre avant d’appeler `Open` (pour un nouvel objet recordset) ou `Requery` (pour un).

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Pour passer des valeurs de paramètre à un objet de jeu d’enregistrements en cours d’exécution

1. Construire l’objet recordset.

1. Préparer un ou plusieurs chaînes, comme le `m_strFilter` chaîne, qui contient l’instruction SQL ou des parties de celui-ci. Placer « ? » des espaces réservés dans lequel les informations de paramètre consiste à accéder.

1. Affecter une valeur de paramètre d’exécution à chaque membre de données de paramètre de l’objet.

1. Appelez le `Open` fonction membre (ou `Requery`, pour un jeu d’enregistrements existant).

Par exemple, supposons que vous souhaitez spécifier une chaîne de filtrage pour votre jeu d’enregistrements à l’aide des informations obtenues au moment de l’exécution. Supposons que vous avez construit un jeu d’enregistrements de la classe `CStudentSet` précédemment, appelé `rsStudents` et que vous souhaitez maintenant lancer une nouvelle requête pour un type particulier d’informations sur les étudiants.

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

Le jeu d’enregistrements contient les enregistrements pour les étudiants dont les enregistrements remplissent les conditions spécifiées par le filtre, ce qui a été construit à partir des paramètres d’exécution. Dans ce cas, le jeu d’enregistrements contient les enregistrements de tous les étudiants seniors.

> [!NOTE]
>  Si nécessaire, vous pouvez définir la valeur d’un membre de données de paramètre avec la valeur Null, à l’aide de [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Vous pouvez même vérifier si un membre de données de paramètre est Null, à l’aide de [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : Ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Recordset : Sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
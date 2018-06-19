---
title: 'Recordset : Paramétrage d’un Recordset (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 275cd9d2ee7ccbd4c9972c00ae6fbb8f33166a0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098548"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Recordset : paramétrage d'un recordset (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Vous pouvez parfois être en mesure de sélectionner des enregistrements en cours d’exécution, à l’aide des informations que vous avez calculé ou obtenu à partir de votre utilisateur final. Les paramètres vous permettent d’atteindre cet objectif.  
  
 Cette rubrique explique :  
  
-   [L’objectif d’un recordset paramétré](#_core_parameterized_recordsets).  
  
-   [Quand et pourquoi vous souhaiterez peut-être paramétrer un jeu d’enregistrements](#_core_when_to_use_parameters).  
  
-   [Comment déclarer des membres de données dans votre classe de recordset paramètre](#_core_parameterizing_your_recordset_class).  
  
-   [Comment transmettre des informations sur les paramètres à un objet recordset en cours d’exécution](#_core_passing_parameter_values_at_run_time).  
  
##  <a name="_core_parameterized_recordsets"></a> Jeux d’enregistrements paramétrés  
 Un jeu d’enregistrements paramétré permet de transmettre des informations de paramètre au moment de l’exécution. Cela a deux conséquences appréciables :  
  
-   Cela peut entraîner une meilleure vitesse d’exécution.  
  
-   Il vous permet de générer une requête en cours d’exécution, en fonction des informations non disponibles au moment du design, telles que les informations fournies par l’utilisateur ou calculée au moment de l’exécution.  
  
 Lorsque vous appelez **ouvrir** pour exécuter la requête, le jeu d’enregistrements utilise les informations de paramètre pour terminer son **SQL SELECT** instruction. Vous pouvez paramétrer un jeu d’enregistrements.  
  
##  <a name="_core_when_to_use_parameters"></a> Quand utiliser les paramètres  
 Utilisations courantes des paramètres sont les suivantes :  
  
-   Passage des arguments d’exécution pour une requête prédéfinie.  
  
     Pour passer des paramètres à une procédure stockée, vous devez spécifier un ODBC personnalisé complète **appeler** instruction, avec des espaces réservés de paramètre, lorsque vous appelez **ouvrir**, remplaçant l’instruction SQL de valeur par défaut du jeu d’enregistrements. Pour plus d’informations, consultez [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) dans les *Class Library Reference* et [SQL : personnalisation du Recordset SQL instruction (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) et [ Recordset : Déclaration de la classe d’une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  

  
-   Exécution efficace de nombreuses requêtes comportant des informations sur les différents paramètres.  
  
     Par exemple, chaque fois que l’utilisateur final recherche des informations sur un étudiant dans la base de données d’inscription étudiant, vous pouvez spécifier nom ou ID de l’étudiant en tant que paramètre obtenu à partir de l’utilisateur. Ensuite, lorsque vous appelez votre jeu d’enregistrements **Requery** fonction membre, la requête sélectionne uniquement que l’enregistrement étudiant.  
  
     Chaîne de filtre du recordset, stockée dans **m_strFilter**, peut ressembler à ceci :  
  
    ```  
    "StudentID = ?"  
    ```  
  
     Imaginons que l’ID de l’étudiant dans la variable `strInputID`. Lorsque vous définissez un paramètre pour `strInputID` (par exemple, l’ID étudiant 100) la valeur de la variable est liée à l’espace réservé de paramètre représenté par le « ? » dans la chaîne de filtre.  
  
     Affectez la valeur du paramètre comme suit :  
  
    ```  
    strInputID = "100";  
    ...  
    m_strParam = strInputID;  
    ```  
  
     Vous ne souhaitez pas configurer une chaîne de filtrage de cette façon :  
  
    ```  
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted  
                                       // for some drivers  
    ```  
  
     Pour plus d’informations sur l’utilisation de guillemets correctement pour les chaînes de filtre, consultez [Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
     La valeur du paramètre est différente à chaque fois que vous actualisez le jeu d’enregistrements pour un nouvel ID étudiant.  
  
    > [!TIP]
    >  À l’aide d’un paramètre est plus efficace que simplement un filtre. Pour un jeu d’enregistrements paramétré, la base de données doit traiter une SQL **sélectionnez** instruction qu’une seule fois. Pour un jeu d’enregistrements filtré sans paramètres, le **sélectionnez** instruction doit être exécutée chaque fois que vous **Requery** avec une nouvelle valeur de filtre.  
  
 Pour plus d’informations sur les filtres, consultez [Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
##  <a name="_core_parameterizing_your_recordset_class"></a> Paramétrage de la classe de votre jeu d’enregistrements  
  
> [!NOTE]
>  Cette section s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction, l’implémentation des paramètres de lignes en bloc est un processus similaire. Pour plus d’informations, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Avant de créer la classe de recordset, déterminez les paramètres vous avez besoin, leurs types de données, et comment le recordset les utilise.  
  
#### <a name="to-parameterize-a-recordset-class"></a>Pour paramétrer une classe de recordset  
  
1.  Exécutez le [Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) de **ajouter une classe** pour créer la classe.  
  
2.  Spécifier les données membres de champ pour les colonnes du jeu d’enregistrements.  
  
3.  Une fois que l’Assistant écrit la classe dans un fichier dans votre projet, accédez au fichier .h et ajouter manuellement un ou plusieurs membres de données de paramètre à la déclaration de classe. L’ajout peut ressembler à l’exemple suivant, la partie d’une classe de l’instantané est conçu pour répondre à la requête « qui les étudiants sont dans la classe parent ? »  
  
    ```  
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
  
     Ajouter les membres de données de paramètre après les membres de données générées par l’Assistant de champ. La convention consiste à ajouter le mot « Param » pour chaque nom de paramètre défini par l’utilisateur.  
  
4.  Modifier la [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) définition de fonction membre dans le fichier .cpp. Ajoutez un appel de fonctions RFX pour chaque membre de données paramètre que vous avez ajouté à la classe. Pour plus d’informations sur l’écriture de fonctions RFX, consultez [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Faites précéder les appels RFX pour les paramètres avec un seul appel à :  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
5.  Dans le constructeur de la classe de recordset, incrémente le nombre de paramètres, `m_nParams`.  
  
     Pour plus d’informations, consultez [Record Field Exchange : utilisation du Code de l’Assistant](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).  
  
6.  Lorsque vous écrivez le code qui crée un objet de jeu d’enregistrements de cette classe, placez un « ? » symbole (point d’interrogation) à chaque endroit dans l’instruction SQL où un paramètre doit être remplacé.  
  
     Au moment de l’exécution, « ? » des espaces réservés sont remplis, dans l’ordre, par les valeurs de paramètre que vous passez. Le premier membre de données de paramètre définie après la [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) appel remplace le premier « ? « dans la chaîne SQL, le deuxième membre de données de paramètre remplace le deuxième » ? », et ainsi de suite.  
  
> [!NOTE]
>  L’ordre des paramètres est important : l’ordre des appels RFX des paramètres dans votre `DoFieldExchange` fonction doit correspondre à l’ordre des espaces réservés de paramètre dans la chaîne SQL.  
  
> [!TIP]

>  La chaîne la plus probable pour travailler avec est la chaîne que vous spécifiez (le cas échéant) pour la classe [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) membre de données, mais certains pilotes ODBC autorisent des paramètres dans d’autres clauses SQL.  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a> Passage de valeurs de paramètre au moment de l’exécution  
 Vous devez spécifier des valeurs de paramètre avant d’appeler **ouvrir** (pour un nouvel objet recordset) ou **Requery** (pour un type existant).  
  
#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Pour passer des valeurs de paramètre à un objet recordset en cours d’exécution  
  
1.  Construisez l’objet recordset.  
  
2.  Préparation d’une ou plusieurs chaînes, telles que la **m_strFilter** chaîne, qui contient l’instruction SQL ou des parties de celui-ci. Placez « ? » des espaces réservés dans lequel les informations de paramètre sont d’accéder.  
  
3.  Affecter une valeur de paramètre d’exécution à chaque membre de données de paramètre de l’objet.  
  
4.  Appelez le **ouvrir** fonction membre (ou **Requery**, pour un objet recordset existant).  
  
 Par exemple, supposons que vous souhaitez spécifier une chaîne de filtre pour le jeu d’enregistrements à l’aide des informations obtenues au moment de l’exécution. Supposons que vous avez construit un jeu d’enregistrements de la classe `CStudentSet` précédemment, appelé `rsStudents` et que vous souhaitez maintenant lancer une nouvelle requête pour un type particulier d’informations sur les étudiants.  
  
```  
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
  
 Le jeu d’enregistrements contient des enregistrements pour les étudiants dont les enregistrements remplissent les conditions spécifiées par le filtre, ce qui a été construit à partir des paramètres d’exécution. Dans ce cas, le jeu d’enregistrements contient les enregistrements pour tous les étudiants seniors.  
  
> [!NOTE]
>  Si nécessaire, vous pouvez définir la valeur d’un membre de données de paramètre avec la valeur Null, à l’aide de [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Vous pouvez également vérifier si un membre de données du paramètre est Null, à l’aide de [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Recordset : sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
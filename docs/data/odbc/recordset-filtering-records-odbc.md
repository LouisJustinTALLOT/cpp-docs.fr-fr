---
title: 'Recordset : Filtrage d’enregistrements (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1196bc41022a3202a55ad1ba5c208b8a8fdbbcc5
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340610"
---
# <a name="recordset-filtering-records-odbc"></a>Recordset : filtrage d'enregistrements (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique explique comment filtrer un jeu d’enregistrements afin qu’elle sélectionne uniquement un sous-ensemble particulier d’enregistrements disponibles. Par exemple, vous pouvez souhaiter sélectionner uniquement les sections de classe pour un cours particulier, tel que MATH101. Un filtre est une condition de recherche définie par le contenu d’un SQL **où** clause. Quand le framework ajoute à l’instruction SQL du recordset le **où** clause limite la sélection.  
  
 Vous devez établir le filtre d’un objet recordset après avoir construit l’objet mais avant d’appeler ses `Open` fonction membre (ou avant d’appeler le `Requery` fonction membre pour un jeu d’enregistrements existant de l’objet dont la propriété `Open` a de la fonction membre été appelé précédemment).  
  
#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Pour spécifier un filtre pour un objet recordset  
  
1.  Construisez un nouvel objet recordset (ou préparez l’appel `Requery` pour un objet existant).  
  
2.  Définissez la valeur de l’objet [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) membre de données.  
  
     Le filtre est une chaîne se terminant par null qui contient le contenu de l’instruction SQL **où** clause, mais pas le mot clé **où**. Par exemple, utilisez :  
  
    ```  
    m_pSet->m_strFilter = "CourseID = 'MATH101'";  
    ```  
  
     not  
  
    ```  
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";  
    ```  
  
    > [!NOTE]
    >  La chaîne littérale « MATH101 » est indiquée par des apostrophes ci-dessus. Dans la spécification SQL ODBC, les guillemets simples sont utilisés pour désigner un littéral de chaîne de caractères. Vérifiez la documentation du pilote ODBC pour les exigences d’indentation de SGBD dans cette situation. Cette syntaxe est également traité plus loin dans la fin de cette rubrique.  
  
3.  Définissez les autres options que vous avez besoin, telles que l’ordre de tri, le mode de verrouillage ou des paramètres. Spécification d’un paramètre est particulièrement utile. Pour plus d’informations sur le paramétrage de votre filtre, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
4.  Appelez `Open` pour le nouvel objet (ou `Requery` pour un objet précédemment ouvert).  
  
> [!TIP]
>  Utilisation de paramètres dans votre filtre est potentiellement la méthode la plus efficace pour récupérer les enregistrements.  
  
> [!TIP]
>  Les filtres de jeu d’enregistrements sont utiles pour [rejoindre](../../data/odbc/recordset-performing-a-join-odbc.md) tables et d’utilisation de [paramètres](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) selon les informations fournies ou calculées au moment de l’exécution.  
  
 Le jeu d’enregistrements sélectionne uniquement les enregistrements qui répondent à la condition de recherche que vous avez spécifié. Par exemple, pour spécifier le filtre sur les cours ci-dessus (en supposant que la variable `strCourseID` actuellement la valeur est, par exemple, « MATH101 »), procédez comme suit :  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
 Le jeu d’enregistrements contient les enregistrements pour toutes les sections de la classe de MATH101.  
  
 Notez comment la chaîne de filtre a été définie dans l’exemple ci-dessus, à l’aide d’une variable de chaîne. Il s’agit de l’utilisation classique. Mais supposons que vous souhaitiez attribuer la valeur littérale 100 pour l’ID de cours. Le code suivant montre comment définir la chaîne de filtre correctement avec une valeur littérale :  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
 Notez l’utilisation de guillemets simples ; Si vous définissez directement la chaîne de filtrage, la chaîne de filtrage est **pas**:  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
 L’utilisation des guillemets ci-dessus est conforme à la spécification ODBC, mais certains SGBD requièrent d’autres types de guillemets. Pour plus d’informations, consultez [SQL : personnalisation du Recordset SQL instruction (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
> [!NOTE]
>  Si vous choisissez de remplacer la chaîne SQL par défaut du jeu d’enregistrements en passant votre propre chaîne SQL à `Open`, vous ne devez pas définir un filtre si votre chaîne personnalisée contient une **où** clause. Pour plus d’informations sur la substitution de la valeur par défaut SQL, consultez [SQL : personnalisation du Recordset SQL instruction (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)   
 [Recordset : Comment Recordsets sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [Recordset : Modification des jeux d’enregistrements enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
---
title: 'Recordset : Architecture (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5be3ec16ec01a6c6db2e24b1b6a6260f3a44bfec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092208"
---
# <a name="recordset-architecture-odbc"></a>Recordset : architecture (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique décrit les membres de données qui composent l’architecture d’un objet recordset :  
  
-   [Données membres de champ](#_core_field_data_members)  
  
-   [Membres de données de paramètre](#_core_parameter_data_members)  
  
-   [À l’aide des membres de données m_nFields et m_nParams](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si l’extraction de lignes en bloc est implémentée, l’architecture est similaire. Pour comprendre les différences, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_a_sample_class"></a> Exemple de classe  
 Lorsque vous utilisez la [Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) de **ajouter une classe** dérivé de l’Assistant pour déclarer une classe de recordset `CRecordset`, la classe obtenue possède la structure générale illustrée dans l’exemple suivant simple classe :  
  
```  
class CCourse : public CRecordset  
{  
public:  
   CCourse(CDatabase* pDatabase = NULL);  
   ...  
   CString m_strCourseID;  
   CString m_strCourseTitle;  
   CString m_strIDParam;  
};  
```  
  
 Au début de la classe, l’Assistant écrit un ensemble de [données membres de champ](#_core_field_data_members). Lorsque vous créez la classe, vous devez spécifier un ou plusieurs membres de données de champ. Si la classe est paramétrée, comme l’exemple de classe est (avec le membre de données `m_strIDParam`), vous devez ajouter manuellement [les membres de données de paramètre](#_core_parameter_data_members). L’Assistant ne prend pas en charge l’ajout de paramètres à une classe.  
  
##  <a name="_core_field_data_members"></a> Données membres de champ  
 Membres les plus importants de votre classe de recordset sont les membres de données de champ. Pour chaque colonne que vous sélectionnez à partir de la source de données, la classe contient un membre de données de type de données approprié pour cette colonne. Par exemple, le [exemple de classe](#_core_a_sample_class) présenté au début de cette rubrique a deux membres de données de champ, les deux de type `CString`, appelé `m_strCourseID` et `m_strCourseTitle`.  
  
 Lorsque le jeu d’enregistrements sélectionne un ensemble d’enregistrements, la structure lie automatiquement les colonnes de l’enregistrement actuel (après le **ouvrir** appel, le premier enregistrement est en cours) aux données membres de champ de l’objet. Autrement dit, l’infrastructure utilise le membre de données de champ approprié en tant qu’une mémoire tampon dans lequel stocker le contenu d’une colonne de l’enregistrement.  
  
 Quand l’utilisateur passe à un nouvel enregistrement, l’infrastructure utilise les données membres de champ pour représenter l’enregistrement actif. L’infrastructure actualise les données membres de champ, en remplaçant les valeurs de l’enregistrement précédent. Données membres de champ sont également utilisés pour mettre à jour l’enregistrement en cours et pour ajouter de nouveaux enregistrements. Dans le cadre du processus de mise à jour un enregistrement, vous spécifiez les valeurs de mise à jour en assignant des valeurs directement au membre de données de champ approprié ou de membres.  
  
##  <a name="_core_parameter_data_members"></a> Membres de données de paramètre  
 Si la classe est paramétrée, elle a un ou plusieurs membres de données de paramètre. Une classe paramétrée vous permet de baser une requête de jeu d’enregistrements sur les informations obtenues ou calculées au moment de l’exécution.  
  
 En règle générale, le paramètre permet d’affiner la sélection, comme dans l’exemple suivant. Selon le [exemple de classe](#_core_a_sample_class) au début de cette rubrique, l’objet recordset susceptible d’exécuter l’instruction SQL suivante :  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 Le « ? » est un espace réservé pour une valeur de paramètre que vous fournissez au moment de l’exécution. Lorsque vous construisez le jeu d’enregistrements et définissez son `m_strIDParam` membre de données sur MATH101, l’instruction SQL effective pour le recordset devient :  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 En définissant les membres de données de paramètre, vous indiquez à l’infrastructure sur les paramètres dans la chaîne SQL. La structure lie le paramètre, ce qui permet à ODBC de savoir où obtenir les valeurs de substitution de l’espace réservé. Dans l’exemple, le jeu d’enregistrements qui en résulte contient uniquement l’enregistrement de la table Course avec une colonne CourseID dont la valeur est MATH101. Toutes les colonnes spécifiées de cet enregistrement sont sélectionnées. Vous pouvez spécifier des paramètres (et des espaces réservés) autant que nécessaire.  
  
> [!NOTE]
>  MFC n’utilise pas les paramètres, en particulier, il n’effectue pas de substitution de texte. À la place, MFC indique à ODBC où rechercher le paramètre ; ODBC extrait les données et effectue l’opération de paramétrage nécessaire.  
  
> [!NOTE]
>  L’ordre des paramètres est important. Pour plus d’informations à ce sujet et plus d’informations sur les paramètres, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> Utilisation de m_nFields et m_nParams  

 Quand un Assistant écrit un constructeur pour votre classe, il initialise aussi la [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) membre de données, qui spécifie le nombre de [données membres de champ](#_core_field_data_members) dans la classe. Si vous ajoutez un [paramètres](#_core_parameter_data_members) à votre classe, vous devez également ajouter une initialisation pour le [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) membre de données, qui spécifie le nombre de membres de données de paramètre. L’infrastructure utilise ces valeurs pour travailler avec les membres de données.  
  
 Pour plus d’informations et d’exemples, consultez [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Déclaration de la classe d’une Table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)
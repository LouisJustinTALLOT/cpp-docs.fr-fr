---
title: 'Recordset : architecture (ODBC)'
ms.date: 11/04/2016
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
ms.openlocfilehash: 0edde640e0eebaf21216fc9ef37a8e31e2c1a210
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707975"
---
# <a name="recordset-architecture-odbc"></a>Recordset : architecture (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique décrit les membres de données qui composent l’architecture d’un objet recordset :

- [Membre de données de champ](#_core_field_data_members)

- [Membres de données de paramètre](#_core_parameter_data_members)

- [Utilisation des membres de données m_nFields et m_nParams](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si l’extraction de lignes en bloc est implémentée, l’architecture est similaire. Pour comprendre les différences, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_a_sample_class"></a> Exemple de classe

> [!NOTE] 
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez toujours créer un consommateur manuellement.

Quand vous utilisez l’[Assistant Consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) de l’Assistant **Ajout d’une classe** pour déclarer une classe recordset dérivée de `CRecordset`, la classe obtenue présente la structure générale illustrée dans l’exemple de classe simple suivant :

```cpp
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

Au début de la classe, l’Assistant écrit un ensemble de [membres de données de champ](#_core_field_data_members). Quand vous créez la classe, vous devez spécifier un ou plusieurs membres de données de champ. Si la classe est paramétrable, comme l’est l’exemple de classe (avec le membre de données `m_strIDParam`), vous devez ajouter manuellement les [membres de données de paramètre](#_core_parameter_data_members). L’Assistant ne prend pas en charge l’ajout de paramètres à une classe.

##  <a name="_core_field_data_members"></a> Membre de données de champ

Les membres les plus importants de votre classe recordset sont les membres de données de champ. Pour chaque colonne que vous sélectionnez à partir de la source de données, la classe contient un membre de données du type de données approprié pour cette colonne. Ainsi, l’[exemple de classe](#_core_a_sample_class) illustré au début de cette rubrique a deux membres de données de champ, tous deux de type `CString`, appelés `m_strCourseID` et `m_strCourseTitle`.

Quand le recordset sélectionne un ensemble d’enregistrements, le framework lie automatiquement les colonnes de l’enregistrement actuel (après l’appel `Open`, le premier enregistrement est l’enregistrement actuel) aux membres de données de champ de l’objet. Autrement dit, le framework utilise le membre de données de champ approprié comme mémoire tampon dans laquelle stocker le contenu d’une colonne d’enregistrement.

Quand l’utilisateur passe à un nouvel enregistrement, le framework utilise les membres de données de champ pour représenter l’enregistrement actuel. Le framework actualise les membres de données de champ, en remplaçant les valeurs de l’enregistrement précédent. Les membres de données de champ servent également à mettre à jour l’enregistrement actuel et à ajouter de nouveaux enregistrements. Dans le cadre du processus de mise à jour d’un enregistrement, vous spécifiez les valeurs de mise à jour en les attribuant directement au(x) membre(s) de données de champ approprié(s).

##  <a name="_core_parameter_data_members"></a> Membres de données de paramètre

Si la classe est paramétrable, elle a un ou plusieurs membres de données de paramètre. Une classe paramétrable vous permet de baser une requête de recordset sur les informations obtenues ou calculées au moment de l’exécution.

En règle générale, le paramètre permet d’affiner la sélection, comme dans l’exemple suivant. D’après l’[exemple de classe](#_core_a_sample_class) au début de cette rubrique, l’objet recordset peut exécuter l’instruction SQL suivante :

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

Le caractère « ? » est un espace réservé pour une valeur de paramètre que vous fournissez au moment de l’exécution. Quand vous construisez le recordset et définissez son membre de données `m_strIDParam` sur MATH101, l’instruction SQL effective pour le recordset devient :

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

En définissant des membres de données de paramètre, vous indiquez au framework que la chaîne SQL contient des paramètres. Le framework lie les paramètres, ce qui permet à ODBC de savoir où obtenir les valeurs de substitution des espaces réservés. Dans l’exemple, le recordset obtenu contient uniquement l’enregistrement de la table Course dont la colonne CourseID a pour valeur MATH101. Toutes les colonnes spécifiées de cet enregistrement sont sélectionnées. Vous pouvez spécifier autant de paramètres (et d’espaces réservés) que nécessaire.

> [!NOTE]
>  MFC n’effectue aucune opération sur les paramètres ; en particulier, il ne procède pas à une substitution de texte. Au lieu de cela, MFC indique à ODBC où obtenir le paramètre ; ODBC extrait les données et effectue le paramétrage nécessaire.

> [!NOTE]
>  L’ordre des paramètres est important. Pour plus d’informations à ce sujet et sur les paramètres, consultez [Recordset : paramétrage d’un recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

##  <a name="_core_using_m_nfields_and_m_nparams"></a> Utilisation de m_nFields et m_nParams

Quand un Assistant écrit un constructeur pour votre classe, il initialise également le membre de données [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields), qui spécifie le nombre de [membres de données de champ](#_core_field_data_members) dans la classe. Si vous ajoutez des [paramètres](#_core_parameter_data_members) à votre classe, vous devez également ajouter une initialisation pour le membre de données [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams), qui spécifie le nombre de membres de données de paramètre. Le framework utilise ces valeurs pour exploiter les membres de données.

Pour obtenir plus d’informations et des exemples, consultez [Record Field Exchange : utilisation de RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : Déclaration de la classe d’une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)
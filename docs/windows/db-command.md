---
title: db_command | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_command
dev_langs:
- C++
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e0fe3f712566345bb069b798207cfdb10a0aa636
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33886409"
---
# <a name="dbcommand"></a>db_command
Crée une commande OLE DB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_command(   
   command,   
   name,   
   source_name,   
   hresult,   
   bindings,   
   bulk_fetch)  
]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `command`  
 Chaîne de commande contenant le texte d’une commande OLE DB. Voici un exemple simple :  
  
```  
[ db_command ( command = "Select * from Products" ) ]  
```  
  
 La syntaxe de *command* est la suivante :  
  
```  
binding parameter block 1  
   OLE DB command  
binding parameter block 2  
   continuation of OLE DB command  
binding parameter block 3  
...  
```  
  
 Un *bloc de paramètres de liaison* est défini comme suit :  
  
 **([** `bindtype` **]** *szVar1* [*, szVar2* [, *nVar3* [, ...]]] **)**  
  
 où :  
  
 **(** marque le début du bloc de liaison de données.  
  
 **[** `bindtype` **]** est l’une des chaînes suivantes qui ne respectent pas la casse :  
  
-   **[db_column]** lie chacune des variables de membres à une colonne dans un ensemble de lignes.  
  
-   **[bindto]** (identique à **[db_column]**).  
  
-   **[in]** lie les variables de membres en tant que paramètres d’entrée.  
  
-   **[out]** lie les variables de membres en tant que paramètres de sortie.  
  
-   **[in, out]** lie les variables de membres en tant que paramètres d’entrée/sortie.  
  
 *SzVarX* correspond à une variable de membre dans la portée actuelle.  
  
 **)** marque la fin du bloc de liaison de données.  
  
 Si la chaîne de commande contient un ou plusieurs spécificateurs tels que [in], [out] ou [in/out], **db_command** génère un mappage de paramètres.  
  
 Si la chaîne de commande contient un ou plusieurs paramètres, tels que [db_column] ou [bindto], **db_command** génère un ensemble de lignes et une table d’accesseurs pour traiter ces variables liées. Pour plus d’informations, consultez [db_accessor](../windows/db-accessor.md) .  
  
> [!NOTE]
>  La syntaxe de [`bindtype`] et le paramètre `bindings` ne sont pas valides lors de l’utilisation de **db_command** au niveau de la classe.  
  
 Voici quelques exemples de blocs de paramètres de liaison. L’exemple suivant lie les membres de données `m_au_fname` et `m_au_lname` respectivement aux colonnes `au_fname` et `au_lname` de la table authors dans la base de données pubs :  
  
```  
TCHAR m_au_fname[21];  
TCHAR m_au_lname[41];  
TCHAR m_state[3] = 'CA';  
  
[db_command (  
   command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \  
   "FROM dbo.authors " \  
   "WHERE state = ?([in]m_state)")  
```  
  
 ]  
  
 *name* (facultatif)  
 Nom du handle que vous utilisez pour travailler avec l’ensemble de lignes. Si vous spécifiez *name*, **db_command** génère une classe avec l’objet *name*spécifié, qui peut être utilisée pour parcourir l’ensemble de lignes ou pour exécuter plusieurs requêtes d’action. Si vous ne spécifiez pas *name*, vous ne pouvez pas retourner plusieurs lignes de résultats à l’utilisateur.  
  
 *source_name* (facultatif)  
 Variable `CSession` ou instance d’une classe à laquelle l’attribut `db_source` est appliqué et sur laquelle la commande est exécutée. Voir [db_source](../windows/db-source.md).  
  
 **db_command** vérifie que la variable utilisée pour *source_name* est valide. La variable spécifiée doit donc être dans la portée globale ou dans la portée de fonction.  
  
 `hresult` (facultatif)  
 Identifie la variable qui reçoit le `HRESULT` de cette commande de base de données. Si la variable n’existe pas, elle est injectée automatiquement par l’attribut.  
  
 *bindings* (facultatif)  
 Vous permet de séparer les paramètres de liaison de la commande OLE DB.  
  
 Si vous spécifiez une valeur pour `bindings`, **db_command** analyse la valeur associée et n’analyse pas le paramètre [`bindtype`]. Cette utilisation vous permet d’utiliser la syntaxe du fournisseur OLE DB. Pour désactiver l’analyse, sans paramètres de liaison, spécifiez **Bindings=""**.  
  
 Si vous ne spécifiez pas de valeur pour `bindings`, **db_command** analyse le bloc de paramètres de liaison, à la recherche de '**(**', suivi de **[**`bindtype`**]** entre crochets, suivi d’une ou plusieurs variables membres C++ déclarées précédemment, suivi de '**)**'. Tout le texte entre parenthèses est supprimé de la commande obtenue, et ces paramètres sont utilisés pour construire des liaisons de colonnes et de paramètres pour cette commande.  
  
 *bulk_fetch*(facultatif)  
 Valeur d’entier qui spécifie le nombre de lignes à extraire.  
  
 La valeur par défaut est 1. Elle spécifie l’extraction d’une seule ligne (l’ensemble de lignes sera de type [CRowset](../data/oledb/crowset-class.md)).  
  
 Une valeur supérieure à 1 spécifie l’extraction de lignes en bloc. L’extraction de lignes en bloc fait référence à la capacité des ensembles de lignes en bloc à extraire plusieurs handles de ligne (l’ensemble de lignes sera de type [CBulkRowset](../data/oledb/cbulkrowset-class.md) et appellera `SetRows` avec le nombre de lignes spécifié).  
  
 Si *bulk_fetch* est inférieur à 1, `SetRows` retourne la valeur zéro.  
  
## <a name="remarks"></a>Notes  
 **db_command** crée un objet [CCommand](../data/oledb/ccommand-class.md) , qui est utilisé par un consommateur OLE DB pour exécuter une commande.  
  
 Vous pouvez utiliser **db_command** avec une portée de classe ou de fonction. La principale différence est la portée de l’objet `CCommand` . Avec la portée de fonction, les données telles que les liaisons se terminent à la fin de la fonction. Utilisations de portée de classe et de fonction impliquent la classe de modèles du consommateur OLE DB **CCommand <>**, mais les arguments template diffèrent selon les cas de fonction et de classe. Dans le cas d’une fonction, des liaisons à un **Accessor** qui comprend des variables locales sont effectuées, alors que pour une classe une classe dérivée de `CAccessor`sera déduite comme argument. En cas d’utilisation comme attribut de classe, **db_command** fonctionne conjointement avec **db_column**.  
  
 Vous pouvez utiliser**db_command** pour exécuter des commandes qui ne retournent pas de jeu de résultats.  
  
 Lorsque le fournisseur de consommateur d’attribut s’applique à cet attribut à une classe, le compilateur attribue la classe à \_ *YourClassName*accesseur, où *YourClassName* est le nom que vous avez donné à la classe et le compilateur crée également une classe appelée *YourClassName*, lequel dérive \_ *YourClassName*accesseur.  Dans l’affichage de classes, vous verrez les deux classes.  
  
## <a name="example"></a>Exemple  
 Cet exemple définit une commande qui sélectionne le prénom et le nom dans une table où la colonne d’état correspond à « CA ». **db_command** crée et lit un ensemble de lignes sur lequel vous pouvez appeler des fonctions générées par un Assistant, telles que [OpenAll et CloseAll](../data/oledb/consumer-wizard-generated-methods.md), ainsi que des fonctions membres `CRowset` telles que [MoveNext](../data/oledb/crowset-movenext.md).  
  
 Notez que ce code vous oblige à fournir votre propre chaîne de connexion qui se connecte à la base de données pubs. Pour plus d’informations sur la façon de procéder dans l’environnement de développement, consultez [How to: Connect to a Database from Server Explorer](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74) et [How to: Add New Data Connections in Server Explorer/Database Explorer](http://msdn.microsoft.com/en-us/fb2f513b-ddad-4142-911e-856bba0054c8).  
  
```  
// db_command.h  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
#pragma once  
  
[  db_source(L"your connection string"),  
   db_command(L" \  
      SELECT au_lname, au_fname \  
      FROM dbo.authors \  
      WHERE state = 'CA'")  ]  
  
struct CAuthors {  
   // In order to fix several issues with some providers, the code below may bind  
   // columns in a different order than reported by the provider  
  
   DBSTATUS m_dwau_lnameStatus;  
   DBSTATUS m_dwau_fnameStatus;  
   DBLENGTH m_dwau_lnameLength;  
   DBLENGTH m_dwau_fnameLength;  
  
   [ db_column("au_lname", status="m_dwau_lnameStatus", length="m_dwau_lnameLength") ] TCHAR m_au_lname[41];  
   [ db_column("au_fname", status="m_dwau_fnameStatus", length="m_dwau_fnameLength") ] TCHAR m_au_fname[21];  
  
   [ db_param("7", paramtype="DBPARAMIO_INPUT") ] TCHAR m_state[3];  
  
   void GetRowsetProperties(CDBPropSet* pPropSet) {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   }  
};  
```  
  
## <a name="example"></a>Exemple  
  
```  
// db_command.cpp  
// compile with: /c  
#include "db_command.h"  
  
int main(int argc, _TCHAR* argv[]) {  
   HRESULT hr = CoInitialize(NULL);  
  
   // Instantiate rowset  
   CAuthors rs;  
  
   // Open rowset and move to first row  
   strcpy_s(rs.m_state, sizeof(rs.m_state), _T("CA"));  
   hr = rs.OpenAll();  
   hr = rs.MoveFirst();  
  
   // Iterate through the rowset  
   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET ) {  
      // Print out the column information for each row  
      printf("First Name: %s, Last Name: %s\n", rs.m_au_fname, rs.m_au_lname);  
      hr = rs.MoveNext();  
   }  
  
   rs.CloseAll();  
   CoUninitialize();  
}  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise `db_source` sur une classe de source de données `CMySource`, et `db_command` sur les classes de commande `CCommand1` et `CCommand2`.  
  
```  
// db_command_2.cpp  
// compile with: /c  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
// class usage for both db_source and db_command  
  
[  db_source(L"your connection string"),  
   db_command(L" \  
      SELECT au_lname, au_fname \  
      FROM dbo.authors \  
      WHERE state = 'CA'")  ]  
struct CMySource {  
   HRESULT OpenDataSource() {  
      return S_OK;  
   }  
};  
  
[db_command(command = "SELECT * FROM Products")]  
class CCommand1 {};  
  
[db_command(command = "SELECT FNAME, LNAME FROM Customers")]  
class CCommand2 {};  
  
int main() {  
   CMySource s;  
   HRESULT hr = s.OpenDataSource();  
   if (SUCCEEDED(hr)) {  
      CCommand1 c1;  
      hr = c1.Open(s);  
  
      CCommand2 c2;  
      hr = c2.Open(s);  
   }  
  
   s.CloseDataSource();  
}  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**class**, `struct`, member, method, local|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs du consommateur OLE DB](../windows/ole-db-consumer-attributes.md)   
 [Attributs autonomes](../windows/stand-alone-attributes.md)   

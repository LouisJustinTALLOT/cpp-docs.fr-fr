---
title: Champ d’état des membres de données dans les accesseurs générés par l’Assistant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e289e2f40326142894894dad1bfe34c801889bb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066854"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Données membres de l’état des champs dans les accesseurs générés par l’Assistant

Lorsque vous utilisez l’Assistant Consommateur OLE DB ATL pour créer un consommateur, l’Assistant génère un membre de données dans la classe d’enregistrement utilisateur pour chaque champ que vous spécifiez dans le mappage de colonnes. Chaque membre de données est de type `DWORD` et contient une valeur d’état correspondant à son champ respectif.  
  
Par exemple, pour un membre de données *m_OwnerID*, l’Assistant génère un membre de données supplémentaires pour l’état du champ (*dwOwnerIDStatus*) et une autre pour la longueur de champ (*dwOwnerIDLength*). Il génère également un mappage de colonnes avec des entrées COLUMN_ENTRY_LENGTH_STATUS.  
  
Ceci est illustré dans le code suivant :  
  
```cpp  
[db_source("insert connection string")]  
[db_command(" \  
   SELECT \  
      Au_ID, \  
      Author, \  
      `Year Born`, \  
      FROM Authors")]  
  
class CAuthors  
{  
public:  
  
   // The following wizard-generated data members contain status   
   // values for the corresponding fields in the column map. You   
   // can use these values to hold NULL values that the database   
   // returns or to hold error information when the compiler returns   
   // errors. See "Field Status Data Members in Wizard-Generated   
   // Accessors" in the Visual C++ documentation for more information   
   // on using these fields.  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
  
   // The following wizard-generated data members contain length  
   // values for the corresponding fields in the column map.  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
  
BEGIN_COLUMN_MAP(CAuthorsAccessor)  
   COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)  
END_COLUMN_MAP()  
  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
      pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
   }  
};  
```  
  
> [!NOTE]
>  Si vous modifiez la classe d’enregistrement utilisateur ou écrivez votre propre consommateur, les variables de données doivent précéder les variables d’état et de longueur.  
  
Vous pouvez utiliser les valeurs d’état pour le débogage. Si le code généré par l’Assistant Consommateur OLE DB ATL génère des erreurs de compilation telles que DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED, vous devez tout d’abord examiner les valeurs actuelles des membres de données du champ État. Celles qui ont des valeurs différentes de zéro correspondent aux colonnes incriminés.  
  
Vous pouvez également utiliser les valeurs d’état pour définir une valeur NULL pour un champ particulier. Cela est utile dans lequel vous voulez distinguer une valeur de champ en tant que valeur NULL au lieu de zéro. Il vous incombe de déterminer si NULL est une valeur valide ou une valeur spéciale et décider comment votre application doit la gérer. OLE DB définit DBSTATUS_S_ISNULL comme le moyen correct pour spécifier une valeur NULL générique. Si le consommateur lit les données et la valeur est null, le champ d’état a la valeur DBSTATUS_S_ISNULL. Si le consommateur souhaite définir une valeur NULL, le consommateur définit la valeur d’état DBSTATUS_S_ISNULL avant d’appeler le fournisseur.  
  
Ensuite, ouvrez Oledb.h et recherchez `DBSTATUSENUM`. Vous pouvez ensuite faire correspondre la valeur numérique de l’état différent de zéro la `DBSTATUSENUM` valeurs d’énumération. Si le nom de l’énumération n’est pas suffisant pour vous indiquer quel est le problème, consultez la rubrique « État » dans la section « Liaison de valeurs de données » de la [Guide du programmeur OLE DB](/previous-versions/windows/desktop/ms713643\(v=vs.85\)). Cette rubrique contient des tableaux de valeurs d’état utilisés durant l’obtention ou définition de données. Pour plus d’informations sur les valeurs de longueur, consultez la rubrique « Longueur » dans la même section.  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>Récupération de la longueur ou l’état d’une colonne  

Vous pouvez récupérer la longueur d’une colonne de longueur variable ou l’état d’une colonne (pour rechercher DBSTATUS_S_ISNULL, par exemple) :  
  
- Pour obtenir la longueur, utilisez la macro COLUMN_ENTRY_LENGTH.  
  
- Pour obtenir l’état, utilisez la macro COLUMN_ENTRY_STATUS.  
  
- Pour obtenir les deux, utilisez COLUMN_ENTRY_LENGTH_STATUS, comme indiqué ci-dessous.  
  
```cpp  
class CProducts  
{  
public:  
   char      szName[40];  
   long      nNameLength;  
   DBSTATUS   nNameStatus;  
  
BEGIN_COLUMN_MAP(CProducts)  
// Bind the column to CProducts.m_ProductName.  
// nOrdinal is zero-based, so the column number of m_ProductName is 1.  
   COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CProducts >> product;  
  
product.Open(session, "Product");  

while (product.MoveNext() == S_OK)  
{  
   // Check the product name isn't NULL before tracing it  
   if (product.nNameStatus == DBSTATUS_S_OK)  
      ATLTRACE("%s is %d characters\n", szName, nNameLength);  
}  
```  
  
Lorsque vous utilisez `CDynamicAccessor`, la longueur et l’état sont liés automatiquement. Pour récupérer les valeurs de longueur et l’état, utilisez la `GetLength` et `GetStatus` fonctions membres.  
  
## <a name="see-also"></a>Voir aussi  

[Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
---
title: Données membres de l'état des champs dans les accesseurs générés par l'Assistant
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: 476c91f55071f6d1c7f243257273a32798813cae
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924635"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Données membres de l'état des champs dans les accesseurs générés par l'Assistant

::: moniker range="msvc-160"

L’Assistant Consommateur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures. Vous pouvez toujours ajouter la fonctionnalité manuellement. Pour plus d’informations, consultez [Création d’un consommateur sans utiliser l’Assistant](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=msvc-150"

Lorsque vous utilisez l’ **Assistant Consommateur OLE DB ATL** pour créer un consommateur, l’Assistant génère un membre de données dans la classe d’enregistrement utilisateur pour chaque champ que vous spécifiez dans le mappage de colonnes. Chaque membre de données est de type `DWORD` et contient une valeur d’état correspondant à son champ respectif.

Par exemple, pour un membre de données *m_OwnerID* , l’Assistant génère un membre de données supplémentaire pour l’état du champ ( *dwOwnerIDStatus* ) et un autre pour la longueur de champ ( *dwOwnerIDLength* ). Il génère également un mappage de colonnes avec des entrées COLUMN_ENTRY_LENGTH_STATUS.

Ceci est illustré dans le code suivant :

```cpp
class CAuthorsAccessor
{
public:
   LONG m_AuID;
   TCHAR m_Author[53];
   LONG m_YearBorn;

   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;

   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;

   DEFINE_COMMAND_EX(CAuthorsAccessor, L" \
   SELECT \
      AuID, \
      Author, \
      YearBorn \
      FROM dbo.Authors")

   BEGIN_COLUMN_MAP(CAuthorsAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)
   END_COLUMN_MAP()
...
```

> [!NOTE]
> Si vous modifiez la classe d’enregistrement utilisateur ou écrivez votre propre consommateur, les variables de données doivent précéder les variables d’état et de longueur.

Vous pouvez utiliser les valeurs d’état pour le débogage. Si le code généré par l’ **Assistant Consommateur OLE DB ATL** génère des erreurs de compilation telles que DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED, vous devez tout d’abord examiner les valeurs actuelles des membre de données d’état des champs. Celles qui ont des valeurs différentes de zéro correspondent aux colonnes incriminées.

Vous pouvez également utiliser les valeurs d’état pour définir une valeur NULL pour un champ particulier. Ainsi, vous pourrez distinguer une valeur de champ comme étant NULL au lieu de zéro si nécessaire. Il vous incombe de déterminer si NULL constitue une valeur valide ou une valeur spéciale, puis de décider comment votre application doit la gérer. OLE DB définit DBSTATUS_S_ISNULL comme la manière correcte pour spécifier une valeur NULL générique. Si le consommateur lit les données et que la valeur est NULL, le champ d’état est défini sur DBSTATUS_S_ISNULL. Si le consommateur souhaite définir une valeur NULL, il définit la valeur d’état sur DBSTATUS_S_ISNULL avant d’appeler le fournisseur.

Ensuite, ouvrez Oledb.h et recherchez DBSTATUSENUM. Vous pouvez alors faire correspondre la valeur numérique de l’état différent de zéro avec les valeurs d’énumération DBSTATUSENUM. Si le nom de l’énumération ne suffit pas pour vous indiquer le problème, consultez la rubrique **État** dans la section **Valeurs de liaison de données** du [Guide du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Cette rubrique contient des tableaux de valeurs d’état utilisés pour obtenir ou définir des données. Pour plus d’informations sur les valeurs de longueur, consultez la rubrique **Longueur** dans la même section.

## <a name="retrieving-the-length-or-status-of-a-column"></a>Récupération de la longueur ou l’état d’une colonne

Vous pouvez récupérer la longueur d’une colonne de longueur variable, ou l’état d’une colonne (pour rechercher DBSTATUS_S_ISNULL, par exemple) :

- Pour connaître la longueur, utilisez la macro COLUMN_ENTRY_LENGTH.

- Pour connaître l’état, utilisez la macro COLUMN_ENTRY_LENGTH.

- Pour connaître les deux, utilisez COLUMN_ENTRY_LENGTH_STATUS, comme indiqué :

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
    ```

- Ensuite, procédez comme suit pour accéder à la longueur et/ou à l’état :

    ```cpp
    CTable<CAccessor<CProducts >> product;
    CSession session;

    product.Open(session, "Product");

    while (product.MoveNext() == S_OK)
    {
       // Check the product name isn't NULL before tracing it
       if (product.nNameStatus == DBSTATUS_S_OK)
          ATLTRACE("%s is %d characters\n", product.szName, product.nNameLength);
    }
    ```

Lorsque vous utilisez `CDynamicAccessor`, la longueur et l’état sont liés automatiquement. Pour récupérer les valeurs de longueur et d’état, utilisez les fonctions de membre `GetLength` et `GetStatus`.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de consommateurs OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)

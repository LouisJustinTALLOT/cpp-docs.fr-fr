---
title: Données membres de l'état des champs dans les accesseurs générés par l'Assistant
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: dd650b7cafef78e23c23ddfef791c88b6b93727f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409003"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Données membres de l'état des champs dans les accesseurs générés par l'Assistant

Lorsque vous utilisez le **Assistant Consommateur OLE DB ATL** pour créer un consommateur, l’Assistant génère un membre de données dans la classe d’enregistrement utilisateur pour chaque champ que vous spécifiez dans le mappage de colonnes. Chaque membre de données est de type `DWORD` et contient une valeur d’état correspondant à son champ respectif.

Par exemple, pour un membre de données *m_OwnerID*, l’Assistant génère un membre de données supplémentaires pour l’état du champ (*dwOwnerIDStatus*) et une autre pour la longueur de champ (*dwOwnerIDLength*). Il génère également un mappage de colonnes avec des entrées COLUMN_ENTRY_LENGTH_STATUS.

Ceci est illustré dans le code suivant :

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

Vous pouvez utiliser les valeurs d’état pour le débogage. Si le code généré par le **Assistant Consommateur OLE DB ATL** génère des erreurs de compilation telles que DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED, vous devez tout d’abord examiner les valeurs actuelles des membres de données du champ État. Celles qui ont des valeurs différentes de zéro correspondent aux colonnes incriminés.

Vous pouvez également utiliser les valeurs d’état pour définir une valeur NULL pour un champ particulier. Cela est utile dans lequel vous voulez distinguer une valeur de champ en tant que valeur NULL au lieu de zéro. Il vous incombe de déterminer si NULL est une valeur valide ou une valeur spéciale et décider comment votre application doit la gérer. OLE DB définit DBSTATUS_S_ISNULL comme le moyen correct pour spécifier une valeur NULL générique. Si le consommateur lit les données et la valeur est null, le champ d’état a la valeur DBSTATUS_S_ISNULL. Si le consommateur souhaite définir une valeur NULL, le consommateur définit la valeur d’état DBSTATUS_S_ISNULL avant d’appeler le fournisseur.

Ensuite, ouvrez Oledb.h et recherchez DBSTATUSENUM. Vous pouvez ensuite faire correspondre la valeur numérique de l’état différent de zéro aux valeurs d’énumération DBSTATUSENUM. Si le nom de l’énumération n’est pas suffisant pour vous indiquer quel est le problème, consultez le **état** rubrique dans le **liaison de valeurs de données** section de la [Guide du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Cette rubrique contient des tableaux de valeurs d’état utilisés durant l’obtention ou définition de données. Pour plus d’informations sur les valeurs de longueur, consultez le **longueur** rubrique dans la même section.

## <a name="retrieving-the-length-or-status-of-a-column"></a>Récupération de la longueur ou l’état d’une colonne

Vous pouvez récupérer la longueur d’une colonne de longueur variable ou l’état d’une colonne (pour rechercher DBSTATUS_S_ISNULL, par exemple) :

- Pour obtenir la longueur, utilisez la macro COLUMN_ENTRY_LENGTH.

- Pour obtenir l’état, utilisez la macro COLUMN_ENTRY_STATUS.

- Pour obtenir les deux, utilisez COLUMN_ENTRY_LENGTH_STATUS, comme indiqué :

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

- Ensuite, accéder à la longueur et/ou d’état comme indiqué :

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

Lorsque vous utilisez `CDynamicAccessor`, la longueur et l’état sont liés automatiquement. Pour récupérer les valeurs de longueur et l’état, utilisez la `GetLength` et `GetStatus` fonctions membres.

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
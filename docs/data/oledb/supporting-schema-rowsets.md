---
title: Prise en charge des ensembles de lignes de schéma
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: 09af59d97ab87c66a0a7096e72cc7b92bc3a5dbf
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525267"
---
# <a name="supporting-schema-rowsets"></a>Prise en charge des ensembles de lignes de schéma

Les ensembles de lignes de schéma permettent au consommateur d’obtenir des informations sur une banque de données sans connaître sa structure sous-jacente ou son schéma. Par exemple, une banque de données peut contenir des tableaux organisés selon une hiérarchie définie par l’utilisateur, il n’y aurait donc aucun moyen de connaître le schéma à moins de le lire. (Pour prendre un autre exemple, les Assistants Visual C++ utilisent des ensembles de lignes de schéma afin de générer des accesseurs pour le consommateur.) Pour permettre au consommateur de faire ceci, l’objet de session du fournisseur expose des méthodes sur l’interface [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)). Dans les applications Visual C++, vous utilisez la classe [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) pour implémenter `IDBSchemaRowset`.

`IDBSchemaRowsetImpl` prend en charge les méthodes suivantes :

- [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) vérifie la validité des restrictions par rapport à un ensemble de lignes de schéma.

- [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implémente une fonction de créateur d’objet COM pour l’objet spécifié par le paramètre du modèle.

- [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) spécifie les restrictions prises en charge sur un ensemble de lignes de schéma en particulier.

- [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) retourne un ensemble de lignes de schéma (hérité de l’interface).

- [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) retourne une liste d’ensembles de lignes de schéma accessibles par `IDBSchemaRowsetImpl::GetRowset` (héritée de l’interface).

## <a name="atl-ole-db-provider-wizard-support"></a>Prise en charge de l’Assistant Fournisseur OLE DB ATL

::: moniker range="vs-2019"

L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures.

::: moniker-end

::: moniker range="vs-2017"

L’**Assistant Fournisseur OLE DB ATL** crée trois classes de schéma dans le fichier d’en-tête de session :

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

Ces classes répondent aux requêtes de consommateur concernant les informations sur le schéma. Notez que la spécification OLE DB requiert que ces trois ensembles de lignes de schéma soient pris en charge :

- **C**<em>ShortName</em>**SessionTRSchemaRowset** gère les requêtes d’informations sur les tableaux (l’ensemble de lignes de schéma DBSCHEMA_TABLES).

- **C**<em>ShortName</em>**SessionTRSchemaRowset** gère les requêtes d’informations sur les tableaux (l’ensemble de lignes de schéma DBSCHEMA_TABLES). L’Assistant fournit des exemples d’implémentation de ces classes, qui retournent des informations de schéma pour un fournisseur de DOS.

- **C**<em>ShortName</em>**SessionPTSchemaRowset** gère les demandes d’informations de schéma sur le type de fournisseur (l’ensemble de lignes du schéma DBSCHEMA_PROVIDER_TYPES). L’implémentation par défaut fournie par l’Assistant retourne S_OK.

Vous pouvez personnaliser ces classes pour gérer les informations de schéma adaptées à votre fournisseur :

- Dans **C**<em>ShortName</em>**SessionTRSchemaRowset**, vous devez remplir les champs du catalogue, du tableau et de la description (`trData.m_szType`, `trData.m_szTable`, et `trData.m_szDesc`). L’exemple généré par l’Assistant n’utilise qu’une seule ligne (tableau). D’autres fournisseurs peuvent retourner plusieurs tableaux.

- Dans **C**<em>ShortName</em>**SessionColSchemaRowset**, vous passez le nom du tableau en tant que `DBID`.

::: moniker-end

## <a name="setting-restrictions"></a>Définition des restrictions

La définition des restrictions est un concept important dans la prise en charge des ensembles de lignes de schéma. Vous l’effectuez à l’aide de `SetRestrictions`. Les restrictions permettent aux consommateurs de récupérer uniquement les lignes correspondantes (par exemple, toutes les colonnes de la table « MaTable »). Les restrictions sont facultatives, et dans le cas où aucune n’est prise en charge (par défaut), toutes les données sont systématiquement retournées. Pour obtenir un exemple de fournisseur qui prend en charge les restrictions, consultez l’exemple [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV).

## <a name="setting-up-the-schema-map"></a>Configuration du mappage de schéma

Configurez un mappage de schéma similaire à celui-ci dans Session.h dans UpdatePV :

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

Pour prendre en charge `IDBSchemaRowset`, vous devez prendre en charge DBSCHEMA_TABLES, DBSCHEMA_COLUMNS et DBSCHEMA_PROVIDER_TYPES. Vous pouvez ajouter des ensembles de lignes de schéma supplémentaires comme bon vous semble.

Déclarez une classe d’ensemble de lignes de schéma avec une méthode `Execute` telle que `CUpdateSessionTRSchemaRowset` dans `UpdatePV`:

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` hérite de `IDBSchemaRowsetImpl` et dispose donc de toutes les méthodes de gestion des restrictions. À l’aide de `CSchemaRowsetImpl`, déclarez les trois classes enfants (répertoriées dans le mappage du schéma ci-dessus) : `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, et `CUpdateSessionPTSchemaRowset`. Chacune de ces classes enfants dispose d’une méthode `Execute` qui gère son ensemble de restrictions (critères de recherche) respectif. Chaque méthode `Execute` compare les valeurs des paramètres *cRestrictions* et *rgRestrictions*. Consultez la description de ces paramètres dans [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).

Pour plus d’informations sur les restrictions correspondant à un ensemble de lignes de schéma spécifique, consultez le tableau des GUID d’ensemble de lignes de schéma dans [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) dans les **Informations de référence du programmeur OLE DB** du SDK Windows.

Par exemple, si vous avez pris en charge la restriction TABLE_NAME sur DBSCHEMA_TABLES, effectuez ce qui suit :

Tout d’abord, consultez DBSCHEMA_TABLES et vérifiez s’il prend en charge quatre restrictions (dans l’ordre).

|Restriction d’ensemble de lignes de schéma|Valeur de restriction|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1 (1 en binaire)|
|TABLE_SCHEMA|0x2 (10 en binaire)|
|TABLE_NAME|0x4 (100 en binaire)|
|TABLE_TYPE|0x8 (1000 en binaire)|

Ensuite, il y a un bit pour chaque restriction. Étant donné que vous souhaitez prendre en charge TABLE_NAME uniquement, vous retournerez 0x4 dans l’élément `rgRestrictions`. Si vous preniez en charge TABLE_CATALOG et TABLE_NAME, vous retourneriez 0x5 (101 en binaire).

Par défaut, l’implémentation retourne 0 (aucune restriction prise en charge) pour toutes les requêtes. UpdatePV constitue un exemple de fournisseur qui prend en charge les restrictions.

### <a name="example"></a>Exemple

Le code suivant est extrait de l’exemple [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV). `UpdatePv` prend en charge les trois ensembles de lignes de schéma requis : DBSCHEMA_TABLES, DBSCHEMA_COLUMNS, et DBSCHEMA_PROVIDER_TYPES. Pour illustrer comment implémenter la prise en charge du schéma dans votre fournisseur, cette rubrique passe en revue l’implémentation de l’ensemble de lignes DBSCHEMA_TABLE.

> [!NOTE]
> L’exemple de code peut différer de ce qui est répertorié ici. Considérez cet exemple de code comme la version la plus récente.

La première étape de l’ajout de la prise en charge du schéma consiste à décider des restrictions que vous allez prendre en charge. Pour déterminer les restrictions disponibles pour votre ensemble de lignes de schéma, consultez la spécification OLE DB pour la définition de `IDBSchemaRowset`. Après la définition principale, vous trouverez un tableau contenant le nom de l’ensemble de lignes de schéma, le nombre de restrictions et les colonnes de restriction. Sélectionnez l’ensemble de lignes de schéma que vous souhaitez prendre en charge et notez le nombre de restrictions et les colonnes de restriction. Par exemple, DBSCHEMA_TABLES prend en charge quatre restrictions (TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME et TABLE_TYPE) :

```cpp
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,
   ULONG* rgRestrictions)
{
    for (ULONG l=0; l<cRestrictions; l++)
    {
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
            rgRestrictions[l] = 0x0C;
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))
                 rgRestrictions[l] = 0x04;
             else if (InlineIsEqualGUID(rguidSchema[l],
                                        DBSCHEMA_PROVIDER_TYPES))
                      rgRestrictions[l] = 0x00;
   }
}
```

Un bit représente chaque colonne de restriction. Si vous souhaitez prendre en charge une restriction (c’est-à-dire, pouvoir envoyer une requête par cette restriction), définissez ce bit sur 1. Si vous ne souhaitez pas prendre en charge une restriction, définissez ce bit sur zéro. À partir de la ligne de code ci-dessus, `UpdatePV` prend en charge les restrictions TABLE_NAME et TABLE_TYPE sur l’ensemble de lignes DBSCHEMA_TABLES. Il s’agit de la troisième (masque de bits 100) et de la quatrième (masque de bits 1000) restriction. Par conséquent, le masque de bits pour `UpdatePv` est 1100 (ou 0x0C) :

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

La fonction `Execute` suivante est similaire à celles des ensembles de lignes ordinaires. Vous avez trois arguments : *pcRowsAffected*, *cRestrictions*, et *rgRestrictions*. La variable *pcRowsAffected* est un paramètre de sortie permettant au fournisseur de renvoyer le nombre de lignes de l’ensemble de lignes de schéma. Le paramètre *cRestrictions* est un paramètre d’entrée qui contient le nombre de restrictions passées par le consommateur au fournisseur. Le paramètre *rgRestrictions* est un tableau de valeurs VARIANT contenant les valeurs de restriction.

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

La variable *cRestrictions* est basée sur le nombre total de restrictions pour un ensemble de lignes de schéma, indépendamment du fait que le fournisseur les prenne en charge ou non. Étant donné que UpdatePv prend en charge deux restrictions (la troisième et la quatrième), ce code recherche uniquement une valeur *cRestrictions* supérieure ou égale à trois.

La valeur de la restriction TABLE_NAME est stockée dans *rgRestrictions[2]* (là encore, la troisième restriction dans un tableau de base zéro est 2). Vérifiez que la restriction n’est pas VT_EMPTY pour pouvoir réellement le prendre en charge. Notez que VT_NULL n’est pas égal à VT_EMPTY. VT_NULL spécifie une valeur de restriction valide.

La définition `UpdatePv` d’un nom de tableau est le nom de chemin d’accès complet d’un fichier texte. Extrayez la valeur de restriction et puis essayez d’ouvrir le fichier pour vous assurer que le fichier existe réellement. Si le fichier n’existe pas, retournez S_OK. Cela peut sembler un peu simpliste mais le code indique réellement au consommateur qu’il n’y a aucun tableau pris en charge par le nom spécifié. La valeur de retour S_OK signifie que le code s’est exécuté correctement.

```cpp
USES_CONVERSION;
enum {
            sizeOfszFile = 255
};
CTABLESRow  trData;
FILE        *pFile = NULL;
TCHAR       szFile[ sizeOfszFile ];
errcode     err = 0;

// Handle any restrictions sent to us. This only handles
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04
// for a total of (0x0C)
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)
{
    CComBSTR bstrName = rgRestrictions[2].bstrVal;
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))
    {
        // Check to see if the file exists
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));
        if (szFile[0] == _T('\0') ||
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))
        {
            return S_OK;// Their restriction was invalid return no data
        }
        else
        {
            fclose(pFile);
        }
    }
}
```

La prise en charge de la quatrième restriction (TABLE_TYPE) est similaire à la restriction de la troisième. Vérifiez que la valeur n’est pas VT_EMPTY. Cette restriction retourne uniquement le type de tableau, TABLE. Pour déterminer les valeurs valides pour DBSCHEMA_TABLES, regardez l’**Annexe B** des **Informations de référence du programmeur OLE DB**, dans la section d’ensemble de lignes TABLES.

```cpp
// TABLE_TYPE restriction:
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)
{
    CComBSTR bstrType = rgRestrictions[3].bstrVal;
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))
    {
        // This is kind of a blind restriction.
        // This only actually supports
        // TABLES so if you get anything else,
        // just return an empty rowset.
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)
            return S_OK;
    }
}
```

C’est ici que vous créez une entrée de ligne pour l’ensemble de lignes. La variable `trData` correspond à `CTABLESRow`, une structure définie dans les modèles du fournisseur OLE DB. `CTABLESRow` correspond à la définition de l’ensemble de lignes TABLES dans l’**Annexe B** de la spécification OLE DB. Vous n’avez qu’une ligne à ajouter, car vous pouvez prendre uniquement en charge un seul tableau à la fois.

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` définit seulement trois colonnes : TABLE_NAME, TABLE_TYPE et DESCRIPTION. Prenez note des colonnes pour lesquelles vous retournez des informations, car ces informations sont nécessaires lorsque vous implémentez `GetDBStatus` :

```cpp
    _ATLTRY
    {
        m_rgRowData.Add(trData);
    }
    _ATLCATCHALL()
    {
        return E_OUTOFMEMORY;
    }
    //if (!m_rgRowData.Add(trData))
    //    return E_OUTOFMEMORY;
    *pcRowsAffected = 1;
    return S_OK;
}
```

La fonction `GetDBStatus` est importante pour le bon fonctionnement de l’ensemble de lignes de schéma. Étant donné que vous ne renvoyez pas les données pour chaque colonne dans l’ensemble de lignes TABLES, vous devez spécifier les colonnes pour lesquelles vous retournez ou non des données.

```cpp
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pColInfo != NULL);

    switch(pColInfo->iOrdinal)
    {
    case 3:     // TABLE_NAME
    case 4:     // TABLE_TYPE
    case 6:     // DESCRIPTION
        return DBSTATUS_S_OK;
        break;
    default:
        return DBSTATUS_S_ISNULL;
    break;
    }
}
```

Étant donné que votre fonction `Execute` retourne des données pour les champs TABLE_NAME, TABLE_TYPE et DESCRIPTION de l’ensemble de lignes TABLES, vous pouvez rechercher dans l’**Annexe B** de la spécification OLE DB et déterminer (en comptant du haut vers le bas) qu’ils correspondent aux ordinaux 3, 4 et 6. Pour chacune de ces colonnes, retournez DBSTATUS_S_OK. Pour toutes les autres colonnes, retournez DBSTATUS_S_ISNULL. Il est important de retourner cet état, car un consommateur pourrait ne pas comprendre que la valeur que vous retournez est NULL ou autre chose. Là encore, notez que NULL n’est pas équivalent à vide.

Pour plus d’informations sur l’interface d’ensemble de lignes de schéma OLE DB, consultez l’interface [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) dans les **Informations de référence du programmeur OLE DB**.

Pour plus d’informations sur la façon dont les utilisateurs peuvent utiliser les méthodes`IDBSchemaRowset`, consultez [Récupération de métadonnées avec les ensembles de lignes de schéma](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).

Pour obtenir un exemple de fournisseur qui prend en charge les ensembles de lignes de schéma, consultez l’exemple [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="see-also"></a>Voir aussi

[Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)

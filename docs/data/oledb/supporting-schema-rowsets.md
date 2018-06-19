---
title: Prise en charge des ensembles de lignes de schéma | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 95f1455fde75ec835486cbcc3d590822891d14f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111755"
---
# <a name="supporting-schema-rowsets"></a>Prise en charge des ensembles de lignes de schéma
Ensembles de lignes de schéma permettent aux consommateurs d’obtenir des informations sur une banque de données sans connaître sa structure sous-jacente, ou son schéma. Par exemple, un magasin de données peut avoir des tables organisés selon une hiérarchie définie par l’utilisateur, afin qu’il n’y aucun moyen pour vous assurer de la connaissance du schéma à l’exception de par sa lecture. (Un autre exemple, notez que les Assistants Visual C++ utilisent les ensembles de lignes de schéma pour générer des accesseurs pour le consommateur.) Pour permettre au consommateur pour ce faire, objet de session du fournisseur expose des méthodes sur le [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) interface. Dans les applications Visual C++, vous utilisez la [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) classe pour implémenter **IDBSchemaRowset**.  
  
 `IDBSchemaRowsetImpl` prend en charge les méthodes suivantes :  
  
-   [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) vérifie la validité des restrictions par rapport à un ensemble de lignes de schéma.  
  
-   [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implémente une fonction de créateur d’objet COM pour l’objet spécifié par le paramètre de modèle.  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) spécifie les restrictions que vous prenez en charge sur un ensemble de lignes de schéma particulier.  
  
-   [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) renvoie un ensemble de lignes du schéma (hérité de l’interface).  
  
-   [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) retourne une liste d’ensembles de lignes de schéma accessible par `IDBSchemaRowsetImpl::GetRowset` (hérité de l’interface).  
  
## <a name="atl-ole-db-provider-wizard-support"></a>Prise en charge de l’Assistant fournisseur OLE DB ATL  
 L’Assistant fournisseur OLE DB ATL crée trois classes de schéma dans le fichier d’en-tête de session :  
  
-   **C** *ShortName* **SessionTRSchemaRowset**  
  
-   **C** *ShortName* **SessionColSchemaRowset**  
  
-   **C** *ShortName* **SessionPTSchemaRowset**  
  
 Ces classes de répondent aux demandes de consommateur des informations de schéma ; Notez que la spécification OLE DB exige que ces trois jeux de lignes pris en charge :  
  
-   **C** *ShortName* **SessionTRSchemaRowset** gère les demandes d’informations sur la table (le `DBSCHEMA_TABLES` ensemble de lignes de schéma).  
  
-   **C** *ShortName* **SessionColSchemaRowset** gère les demandes d’informations sur les colonnes (le **DBSCHEMA_COLUMNS** ensemble de lignes de schéma). L’Assistant fournit des exemples d’implémentation de ces classes, qui retournent des informations de schéma pour un fournisseur de déni de service.  
  
-   **C** *ShortName* **SessionPTSchemaRowset** gère les demandes d’informations de schéma sur le type de fournisseur (le **DBSCHEMA_PROVIDER_TYPES** schéma ensemble de lignes). L’implémentation par défaut fournie par l’Assistant retourne `S_OK`.  
  
 Vous pouvez personnaliser ces classes pour gérer les informations de schéma appropriées à votre fournisseur :  
  
-   Dans **C***ShortName***SessionTRSchemaRowset**, vous devez renseigner les champs de catalogue, de table et de description (**trData.m_szType**, **trData.m_szTable** , et **trData.m_szDesc**). L’exemple générées par l’Assistant n'utilise qu’une seule ligne (table). Autres fournisseurs peuvent retourner plusieurs tables.  
  
-   Dans **C***ShortName***SessionColSchemaRowset**, vous passez le nom de la table comme un **DBID**.  
  
## <a name="setting-restrictions"></a>Définition de Restrictions  
 Un concept important dans la prise en charge du jeu de lignes de schéma est définition des restrictions, que vous effectuez à l’aide de `SetRestrictions`. Les restrictions permettent aux consommateurs de récupérer uniquement les lignes correspondantes (par exemple, toutes les colonnes de la table « MaTable »). Les restrictions sont facultatives, et dans le cas où aucune n’est prise en charge (par défaut), toutes les données sont systématiquement retournées. Pour obtenir un exemple d’un fournisseur qui ne prend pas en charge les restrictions, consultez la [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) exemple.  
  
## <a name="setting-up-the-schema-map"></a>Configurer le mappage de schéma  
 Vous pouvez configurer un mappage de schéma comme celui-ci dans Session.h dans UpdatePV :  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 Pour prendre en charge **IDBSchemaRowset**, vous devez prendre en charge `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, et **DBSCHEMA_PROVIDER_TYPES**. Vous pouvez ajouter des ensembles de lignes de schéma supplémentaires à votre convenance.  
  
 Déclarez une classe d’ensemble de lignes de schéma avec un `Execute` méthode telle que `CUpdateSessionTRSchemaRowset` dans UpdatePV :  
  
```  
class CUpdateSessionTRSchemaRowset :   
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,   
                              CTABLESRow, CUpdateSession >  
...  
// Execute looks like this; what pointers does the consumer use?  
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,   
                    ULONG cRestrictions, const VARIANT* rgRestrictions)  
```  
  
 Notez que `CUpdateSession` hérite `IDBSchemaRowsetImpl`, de sorte que toutes les restrictions des méthodes de gestion. À l’aide de `CSchemaRowsetImpl`, déclarez trois classes enfant (énumérées dans le mappage du schéma ci-dessus) : `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, et `CUpdateSessionPTSchemaRowset`. Chacune de ces classes enfant a un `Execute` méthode qui gère son jeu de restrictions (critères de recherche) respectif. Chaque `Execute` méthode compare les valeurs de la `cRestrictions` et `rgRestrictions` paramètres. Consultez la description de ces paramètres dans [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
 Pour plus d’informations sur les restrictions correspondant à un ensemble de lignes du schéma particulier, consultez la table de l’ensemble de lignes de schéma GUID dans [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) dans les *de référence du programmeur OLE DB* dans le SDK Windows.  
  
 Par exemple, si vous prenez en charge la **TABLE_NAME** restriction sur `DBSCHEMA_TABLES`, vous devez procédez comme suit :  
  
 Tout d’abord, recherchez `DBSCHEMA_TABLES` et qu’il prend en charge quatre restrictions (dans l’ordre).  
  
|Restriction d’ensemble de lignes de schéma|Valeur de restriction|  
|-------------------------------|-----------------------|  
|**TABLE_CATALOG**|0 x 1 (binaire 1)|  
|**TABLE_SCHEMA**|0 x 2 (binaire 10)|  
|**NOM_TABLE**|0 x 4 (binaire 100)|  
|**TABLE_TYPE**|0 x 8 (binaire 1000)|  
  
 Ensuite, notez qu’il existe un bit pour chaque restriction. Étant donné que vous souhaitez prendre en charge **TABLE_NAME** uniquement, vous devez retourner 0 x 4 dans la `rgRestrictions` élément. Si vous prenez en charge **TABLE_CATALOG** et **nom_table**, vous devez retourner 0 x 5 (binaire 101).  
  
 Par défaut, l’implémentation retourne 0 (ne prend pas en charge toutes les restrictions) pour une demande. UpdatePV est un exemple d’un fournisseur qui ne prend pas en charge les restrictions.  
  
### <a name="example"></a>Exemple  
 Ce code provient de la [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) exemple. UpdatePv prend en charge les trois ensembles de lignes de schéma requis : `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, et **DBSCHEMA_PROVIDER_TYPES**. Par exemple montrant comment implémenter la prise en charge du schéma dans votre fournisseur, cette rubrique vous guide Mise en œuvre le **DBSCHEMA_TABLE** ensemble de lignes.  
  
> [!NOTE]
>  L’exemple de code peut-être différer de ceux répertoriés ici ; Considérez l’exemple de code en tant que la version la plus récente.  
  
 La première étape lors de l’ajout de prise en charge du schéma consiste à déterminer les restrictions que vous vous apprêtez à prendre en charge. Pour déterminer les restrictions sont disponibles pour votre ensemble de lignes du schéma, consultez la spécification OLE DB pour la définition de **IDBSchemaRowset**. Après la définition principale, vous consultez une table qui contient le nom d’ensemble de lignes de schéma, le nombre de restrictions et les colonnes de restriction. Sélectionnez les lignes du schéma que vous souhaitez prendre en charge et prenez note du nombre de restrictions et les colonnes de restriction. Par exemple, `DBSCHEMA_TABLES` prend en charge quatre restrictions (**TABLE_CATALOG**, **TABLE_SCHEMA**, **TABLE_NAME**, et **TABLE_TYPE** ):  
  
```  
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
  
 Un bit représente chaque colonne de restriction. Si vous souhaitez prendre en charge une restriction (autrement dit, vous pouvez interroger par celui-ci), affectez à ce bit à 1. Si vous ne souhaitez pas prendre en charge une restriction, affectez à ce bit à zéro. À partir de la ligne de code ci-dessus, UpdatePV prend en charge la **TABLE_NAME** et **TABLE_TYPE** restrictions sur les `DBSCHEMA_TABLES` ensemble de lignes. Il s’agit du troisième (masque binaire 100) et le quatrième (masque binaire 1000) restrictions. Par conséquent, le masque de bits pour UpdatePv est 1100 (ou 0x0C) :  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 Les éléments suivants `Execute` fonction est similaire à celles des jeux de lignes ordinaires. Vous avez trois arguments : `pcRowsAffected`, `cRestrictions`, et `rgRestrictions`. Le `pcRowsAffected` variable est un paramètre de sortie que le fournisseur peut retourner le nombre de lignes dans l’ensemble de lignes de schéma. Le `cRestrictions` paramètre est un paramètre d’entrée qui contient le nombre de restrictions passées par le consommateur au fournisseur. Le `rgRestrictions` paramètre est un tableau de **VARIANT** les valeurs qui contiennent les valeurs de restriction.  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 Le `cRestrictions` variable est basée sur le nombre total de restrictions pour un ensemble de lignes de schéma, indépendamment de si le fournisseur prend en charge les. Étant donné que UpdatePv prend en charge deux restrictions (les troisième et quatrième), ce code recherche uniquement une `cRestrictions` valeur supérieure ou égale à trois.  
  
 La valeur de la **TABLE_NAME** restriction est stockée dans `rgRestrictions[2]` (là encore, la troisième restriction dans un tableau de base zéro est 2). Vous devez vérifier que la restriction n’est pas `VT_EMPTY` effectivement prendre en charge. Notez que **VT_NULL** n’est pas égal à `VT_EMPTY`. **VT_NULL** spécifie une valeur de restriction valide.  
  
 La définition UpdatePv d’un nom de table est un nom de chemin d’accès complet à un fichier texte. Extrayez la valeur de restriction et puis que vous tentez d’ouvrir le fichier pour vous assurer que le fichier existe réellement. Si le fichier n’existe pas, retournez `S_OK`. Cela peut sembler un peu en arrière, mais ce que le code réellement informe le consommateur est qu’il n’existait aucune table n’est pris en charge par le nom spécifié. Le `S_OK` retour signifie que le code exécuté correctement.  
  
```  
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
  
 Prise en charge de la quatrième restriction (**TABLE_TYPE**) est similaire à la troisième restriction. Vérifiez que la valeur n’est pas `VT_EMPTY`. Cette restriction retourne uniquement le type de table, **TABLE**. Pour déterminer les valeurs valides pour le `DBSCHEMA_TABLES`, consultez l’annexe B de la *de référence du programmeur OLE DB* dans les **TABLES** section de l’ensemble de lignes.  
  
```  
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
  
 Il s’agit réellement où que vous créez une entrée de ligne pour l’ensemble de lignes. La variable `trData` correspond à **CTABLESRow**, une structure définie dans les modèles du fournisseur OLE DB. **CTABLESRow** correspond à la **TABLES** définition de l’ensemble de lignes dans l’annexe B de la spécification OLE DB. Il vous suffit d’une ligne à ajouter, car vous pouvez prennent uniquement en charge une seule table à la fois.  
  
```  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 UpdatePV définit trois colonnes seulement : **TABLE_NAME**, **TABLE_TYPE**, et **DESCRIPTION**. Vous prenez note des colonnes pour lesquelles vous retournez des informations, car vous avez besoin de ces informations lorsque vous implémentez `GetDBStatus`:  
  
```  
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
  
 Le `GetDBStatus` fonction est très importante pour le fonctionnement correct de l’ensemble de lignes de schéma. Étant donné que vous ne retournent pas de données pour chaque colonne dans la **TABLES** ensemble de lignes, vous devez spécifier les colonnes de retourner des données et que vous n'effectuez pas.  
  
```  
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
  
 Étant donné que votre `Execute` fonction retourne des données pour le **TABLE_NAME**, **TABLE_TYPE**, et **DESCRIPTION** des champs la **TABLES**ensemble de lignes, vous pouvez consulter l’annexe B de la spécification OLE DB et déterminer (en comptant à partir du haut vers le bas) qu’ils sont les ordinaux 3, 4 et 6. Pour chacune de ces colonnes, retournez **DBSTATUS_S_OK**. Pour toutes les autres colonnes, retournez **DBSTATUS_S_ISNULL**. Il est important de retourner cet état, car un consommateur peut ne pas comprend que la valeur que vous retournez est **NULL** ou autre chose. Là encore, notez que **NULL** n’est pas équivalent à vide.  
  
 Pour plus d’informations sur l’interface d’ensemble de lignes de schéma OLE DB, consultez le [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) interface dans la référence du programmeur OLE DB.  
  
 Pour plus d’informations sur la façon dont les utilisateurs peuvent utiliser **IDBSchemaRowset** méthodes, consultez [récupération de métadonnées avec les ensembles de lignes de schéma](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).  
  
 Pour obtenir un exemple de fournisseur qui prend en charge les ensembles de lignes de schéma, consultez le [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)
---
title: Création d'un fournisseur actualisable
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 2811cd56bdc87282b9d4395a9a79ba9b333dadee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211391"
---
# <a name="creating-an-updatable-provider"></a>Création d'un fournisseur actualisable

Visual C++ prend en charge les fournisseurs pouvant être mis à jour ou les fournisseurs pouvant mettre à jour (écrire dans) le magasin de données. Cette rubrique explique comment créer des fournisseurs pouvant être mis à jour à l’aide de modèles de OLE DB.

Cette rubrique suppose que vous démarrez avec un fournisseur exploitable. La création d’un fournisseur actualisable s’exécute en deux étapes. Vous devez d’abord déterminer la manière dont le fournisseur apporte des modifications au magasin de données. en particulier, si les modifications doivent être effectuées immédiatement ou différées jusqu’à l’émission d’une commande de mise à jour. La section «[rendre les fournisseurs pouvant être mis à jour](#vchowmakingprovidersupdatable)» décrit les modifications et les paramètres que vous devez effectuer dans le code du fournisseur.

Ensuite, vous devez vous assurer que votre fournisseur contient toutes les fonctionnalités pour prendre en charge tout ce que le consommateur peut en demander. Si le consommateur souhaite mettre à jour le magasin de données, le fournisseur doit contenir du code qui rend les données persistantes dans le magasin de données. Par exemple, vous pouvez utiliser la bibliothèque Runtime C ou MFC pour effectuer ces opérations sur votre source de données. La section «[écriture dans la source de données](#vchowwritingtothedatasource)» décrit comment écrire dans la source de données, gérer les valeurs NULL et par défaut, et définir des indicateurs de colonne.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) est un exemple de fournisseur pouvant être mis à jour. UpdatePV est identique à MyProv, mais avec une prise en charge pouvant être mise à jour.

##  <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>Rendre les fournisseurs pouvant être mis à jour

La clé de la mise à jour d’un fournisseur consiste à comprendre les opérations que votre fournisseur doit effectuer sur le magasin de données et la façon dont vous souhaitez que le fournisseur effectue ces opérations. Plus précisément, le problème majeur est de savoir si les mises à jour du magasin de données doivent être effectuées immédiatement ou différées (par lot) jusqu’à l’émission d’une commande de mise à jour.

Vous devez d’abord décider s’il faut hériter de `IRowsetChangeImpl` ou `IRowsetUpdateImpl` dans votre classe rowset. En fonction de ce que vous choisissez d’implémenter, les fonctionnalités de trois méthodes seront affectées : `SetData`, `InsertRows`et `DeleteRows`.

- Si vous héritez de [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), l’appel de ces trois méthodes modifie immédiatement le magasin de données.

- Si vous héritez de [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), les méthodes diffèrent les modifications apportées au magasin de données jusqu’à ce que vous appeliez `Update`, `GetOriginalData`ou `Undo`. Si la mise à jour implique plusieurs modifications, elles sont exécutées en mode batch (Notez que les modifications de traitement par lot peuvent ajouter une surcharge de mémoire considérable).

Notez que `IRowsetUpdateImpl` dérive de `IRowsetChangeImpl`. Ainsi, `IRowsetUpdateImpl` vous donne la possibilité de modifier la fonctionnalité de traitement par lots.

### <a name="to-support-updatability-in-your-provider"></a>Pour prendre en charge la mise à jour de votre fournisseur

1. Dans votre classe rowset, héritez de `IRowsetChangeImpl` ou `IRowsetUpdateImpl`. Ces classes fournissent les interfaces appropriées pour modifier le magasin de données :

   **Ajout de IRowsetChange**

   Ajoutez `IRowsetChangeImpl` à votre chaîne d’héritage à l’aide de la forme suivante :

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   Ajoutez également des `COM_INTERFACE_ENTRY(IRowsetChange)` à la section `BEGIN_COM_MAP` de votre classe rowset.

   **Ajout d’IRowsetUpdate**

   Ajoutez `IRowsetUpdate` à votre chaîne d’héritage à l’aide de la forme suivante :

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > Vous devez supprimer la ligne de `IRowsetChangeImpl` de votre chaîne d’héritage. Cette exception à la directive mentionnée précédemment doit inclure le code pour `IRowsetChangeImpl`.

1. Ajoutez ce qui suit à votre mappage COM (`BEGIN_COM_MAP ... END_COM_MAP`) :

   |  Si vous implémentez   |           Ajouter à la carte COM             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Si vous implémentez | Ajouter au mappage de jeu de propriétés |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. Dans votre commande, ajoutez le code suivant à votre mappage de jeu de propriétés (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`) :

   |  Si vous implémentez   |                                             Ajouter au mappage de jeu de propriétés                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. Dans votre mappage de jeu de propriétés, vous devez également inclure tous les paramètres suivants tels qu’ils apparaissent ci-dessous :

    ```cpp
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)

    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)
    ```

   Vous pouvez trouver les valeurs utilisées dans ces appels de macro en recherchant dans Atldb. h les ID de propriété et les valeurs (si Atldb. h diffère de la documentation en ligne, Atldb. h remplace la documentation).

   > [!NOTE]
   > La plupart des paramètres de `VARIANT_FALSE` et de `VARIANT_TRUE` sont requis par les modèles de OLE DB ; la spécification OLE DB indique qu’elles peuvent être en lecture/écriture, mais les modèles de OLE DB ne peuvent prendre en charge qu’une seule valeur.

   **Si vous implémentez IRowsetChangeImpl**

   Si vous implémentez `IRowsetChangeImpl`, vous devez définir les propriétés suivantes sur votre fournisseur. Ces propriétés sont principalement utilisées pour demander des interfaces via `ICommandProperties::SetProperties`.

   - `DBPROP_IRowsetChange`: la définition de cette option définit automatiquement `DBPROP_IRowsetChange`.

   - `DBPROP_UPDATABILITY`: masque de masque spécifiant les méthodes prises en charge sur `IRowsetChange`: `SetData`, `DeleteRows`ou `InsertRow`.

   - `DBPROP_CHANGEINSERTEDROWS`: le consommateur peut appeler `IRowsetChange::DeleteRows` ou `SetData` pour les lignes nouvellement insérées.

   - `DBPROP_IMMOBILEROWS`: l’ensemble de lignes ne réorganise pas les lignes insérées ou mises à jour.

   **Si vous implémentez IRowsetUpdateImpl**

   Si vous implémentez `IRowsetUpdateImpl`, vous devez définir les propriétés suivantes sur votre fournisseur, en plus de définir toutes les propriétés de `IRowsetChangeImpl` précédemment listées :

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: doit être READ_ONLY et VARIANT_TRUE.

   - `DBPROP_OWNUPDATEDELETE`: doit être READ_ONLY et VARIANT_TRUE.

   - `DBPROP_OTHERINSERT`: doit être READ_ONLY et VARIANT_TRUE.

   - `DBPROP_OTHERUPDATEDELETE`: doit être READ_ONLY et VARIANT_TRUE.

   - `DBPROP_REMOVEDELETED`: doit être READ_ONLY et VARIANT_TRUE.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > Si vous prenez en charge les notifications, vous pouvez également avoir d’autres propriétés. consultez la section sur `IRowsetNotifyCP` pour cette liste.

##  <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>Écriture dans la source de données

Pour lire à partir de la source de données, appelez la fonction `Execute`. Pour écrire dans la source de données, appelez la fonction `FlushData`. (Dans un sens général, flush signifie enregistrer les modifications apportées à une table ou un index sur disque.)

```cpp
FlushData(HROW, HACCESSOR);
```

Les arguments descripteur de ligne (HROW) et handle d’accesseur (HACCESSOR) vous permettent de spécifier la région à écrire. En général, vous écrivez un seul champ de données à la fois.

La méthode `FlushData` écrit des données au format dans lequel elles ont été stockées à l’origine. Si vous ne substituez pas cette fonction, votre fournisseur fonctionnera correctement, mais les modifications ne seront pas vidées dans le magasin de données.

### <a name="when-to-flush"></a>Quand vider

Les modèles de fournisseur appellent FlushData chaque fois que les données doivent être écrites dans le magasin de données ; Cela se produit généralement (mais pas toujours) suite à des appels aux fonctions suivantes :

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` (s’il existe de nouvelles données à insérer dans la ligne)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Fonctionnement

Le consommateur effectue un appel qui requiert un vidage (par exemple, Update) et cet appel est passé au fournisseur, qui effectue toujours les opérations suivantes :

- Appelle `SetDBStatus` chaque fois que vous avez une valeur d’État liée.

- Vérifie les indicateurs de colonne.

- Appelle `IsUpdateAllowed`.

Ces trois étapes permettent de garantir la sécurité. Le fournisseur appelle ensuite `FlushData`.

### <a name="how-to-implement-flushdata"></a>Comment implémenter FlushData

Pour implémenter `FlushData`, vous devez prendre en compte plusieurs problèmes :

S’assurer que le magasin de données peut gérer les modifications.

Gestion des valeurs NULL.

### <a name="handling-default-values"></a>Gestion des valeurs par défaut.

Pour implémenter votre propre méthode `FlushData`, vous devez :

- Accédez à votre classe rowset.

- Dans la classe rowset, placez la déclaration de :

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Fournissez une implémentation de `FlushData`.

Une bonne implémentation de `FlushData` stocke uniquement les lignes et les colonnes qui sont réellement mises à jour. Vous pouvez utiliser les paramètres HROW et HACCESSOR pour déterminer la ligne et la colonne en cours de stockage à des fins d’optimisation.

En règle générale, le plus grand défi consiste à utiliser votre propre banque de données native. Si possible, essayez d’effectuer les opérations suivantes :

- Conservez la méthode d’écriture dans votre magasin de données aussi simple que possible.

- Gérer les valeurs NULL (facultatif mais recommandé).

- Gérer les valeurs par défaut (facultatif mais recommandé).

La meilleure chose à faire est d’avoir des valeurs réelles spécifiées dans votre magasin de données pour les valeurs NULL et par défaut. C’est mieux si vous pouvez extrapoler ces données. Si ce n’est pas le cas, il est recommandé de ne pas autoriser les valeurs NULL et par défaut.

L’exemple suivant montre comment `FlushData` est implémentée dans la classe `RUpdateRowset` de l’exemple `UpdatePV` (consultez Rowset. h dans l’exemple de code) :

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)
...
HRESULT FlushData(HROW, HACCESSOR)
{
    ATLTRACE2(atlTraceDBProvider, 0, "RUpdateRowset::FlushData\n");

    USES_CONVERSION;
    enum {
        sizeOfString = 256,
        sizeOfFileName = MAX_PATH
    };
    FILE*    pFile = NULL;
    TCHAR    szString[sizeOfString];
    TCHAR    szFile[sizeOfFileName];
    errcode  err = 0;

    ObjectLock lock(this);

    // From a filename, passed in as a command text,
    // scan the file placing data in the data array.
    if (m_strCommandText == (BSTR)NULL)
    {
        ATLTRACE( "RRowsetUpdate::FlushData -- "
                  "No filename specified\n");
        return E_FAIL;
    }

    // Open the file
    _tcscpy_s(szFile, sizeOfFileName, OLE2T(m_strCommandText));
    if ((szFile[0] == _T('\0')) ||
        ((err = _tfopen_s(&pFile, &szFile[0], _T("w"))) != 0))
    {
        ATLTRACE("RUpdateRowset::FlushData -- Could not open file\n");
        return DB_E_NOTABLE;
    }

    // Iterate through the row data and store it.
    for (long l=0; l<m_rgRowData.GetSize(); l++)
    {
        CAgentMan am = m_rgRowData[l];

        _putw((int)am.dwFixed, pFile);

        if (_tcscmp(&am.szCommand[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szCommand2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);
    }

    if (fflush(pFile) == EOF || fclose(pFile) == EOF)
    {
        ATLTRACE("RRowsetUpdate::FlushData -- "
                 "Couldn't flush or close file\n");
    }

    return S_OK;
}
```

### <a name="handling-changes"></a>Gestion des modifications

Pour que votre fournisseur gère les modifications, vous devez d’abord vous assurer que votre magasin de données (tel qu’un fichier texte ou un fichier vidéo) possède des fonctionnalités qui vous permettent d’y apporter des modifications. Si ce n’est pas le cas, vous devez créer ce code séparément du projet du fournisseur.

### <a name="handling-null-data"></a>Gestion des données de type NULL

Il est possible qu’un utilisateur final envoie des données NULL. Lorsque vous écrivez des valeurs NULL dans les champs de la source de données, il peut y avoir des problèmes potentiels. Imaginez une application acceptant les commandes qui accepte des valeurs pour la ville et le code postal. elle peut accepter l’une ou les deux valeurs, mais pas aucune, car dans ce cas, la remise serait impossible. Vous devez donc restreindre certaines combinaisons de valeurs NULL dans les champs qui ont un sens pour votre application.

En tant que développeur, vous devez réfléchir à la façon dont vous allez stocker ces données, comment vous allez les lire à partir du magasin de données et comment les spécifier à l’utilisateur. Plus précisément, vous devez réfléchir à la manière de modifier l’état des données des données de l’ensemble de lignes dans la source de données (par exemple, DataStatus = NULL). Vous décidez de la valeur à retourner lorsqu’un consommateur accède à un champ contenant une valeur NULL.

Examinez le code dans l’exemple UpdatePV. Il illustre comment un fournisseur peut gérer des données NULL. Dans UpdatePV, le fournisseur stocke les données NULL en écrivant la chaîne « NULL » dans le magasin de données. Lorsqu’il lit les données NULL dans le magasin de données, il voit cette chaîne, puis vide la mémoire tampon, en créant une chaîne NULL. Elle a également une substitution de `IRowsetImpl::GetDBStatus` dans laquelle elle retourne DBSTATUS_S_ISNULL si cette valeur de données est vide.

### <a name="marking-nullable-columns"></a>Marquage de colonnes Nullable

Si vous implémentez également des ensembles de lignes de schéma (voir `IDBSchemaRowsetImpl`), votre implémentation doit spécifier dans l’ensemble de lignes DBSCHEMA_COLUMNS (généralement marqué dans votre fournisseur par CxxxSchemaColSchemaRowset) que la colonne accepte les valeurs NULL.

Vous devez également spécifier que toutes les colonnes Nullable contiennent la valeur DBCOLUMNFLAGS_ISNULLABLE dans votre version du `GetColumnInfo`.

Dans l’implémentation des modèles OLE DB, si vous ne Marquez pas les colonnes comme Nullable, le fournisseur suppose qu’elles doivent contenir une valeur et n’autorise pas le consommateur à lui envoyer des valeurs NULL.

L’exemple suivant montre comment la fonction `CommonGetColInfo` est implémentée dans CUpdateCommand (consultez reprovs. cpp) dans UpdatePV. Notez la manière dont les colonnes ont cette DBCOLUMNFLAGS_ISNULLABLE pour les colonnes Nullable.

```cpp
/////////////////////////////////////////////////////////////////////////////
// CUpdateCommand (in UpProvRS.cpp)

ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols, bool bBookmark)
{
    static ATLCOLUMNINFO _rgColumns[6];
    ULONG ulCols = 0;

    if (bBookmark)
    {
        ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                            sizeof(DWORD), DBTYPE_BYTES,
                            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                            DBCOLUMNFLAGS_ISBOOKMARK)
        ulCols++;
    }

    // Next set the other columns up.
    // Add a fixed length entry for OLE DB conformance testing purposes
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Fixed"), 1, 4, DBTYPE_UI4,
                        10, 255, GUID_NULL, CAgentMan, dwFixed,
                        DBCOLUMNFLAGS_WRITE |
                        DBCOLUMNFLAGS_ISFIXEDLENGTH)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command"), 2, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text"), 3, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command2"), 4, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text2"), 5, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    if (pcCols != NULL)
    {
        *pcCols = ulCols;
    }

    return _rgColumns;
}
```

### <a name="default-values"></a>Valeurs par défaut

Comme avec les données NULL, vous devez gérer la modification des valeurs par défaut.

La valeur par défaut de `FlushData` et `Execute` consiste à retourner S_OK. Par conséquent, si vous ne remplacez pas cette fonction, les modifications semblent être exécutées (S_OK sont retournées), mais elles ne sont pas transmises au magasin de données.

Dans l’exemple `UpdatePV` (dans rowset. h), la méthode `SetDBStatus` gère les valeurs par défaut comme suit :

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* pdbStatus, CSimpleRow* pRow,
                            ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pRow != NULL && pColInfo != NULL && pdbStatus != NULL);

    void* pData = NULL;
    char* pDefaultData = NULL;
    DWORD* pFixedData = NULL;

    switch (*pdbStatus)
    {
        case DBSTATUS_S_DEFAULT:
            pData = (void*)&m_rgRowData[pRow->m_iRowset];
            if (pColInfo->wType == DBTYPE_STR)
            {
                pDefaultData = (char*)pData + pColInfo->cbOffset;
                strcpy_s(pDefaultData, "Default");
            }
            else
            {
                pFixedData = (DWORD*)((BYTE*)pData +
                                          pColInfo->cbOffset);
                *pFixedData = 0;
                return S_OK;
            }
            break;
        case DBSTATUS_S_ISNULL:
        default:
            break;
    }
    return S_OK;
}
```

### <a name="column-flags"></a>Indicateurs de colonne

Si vous prenez en charge les valeurs par défaut sur vos colonnes, vous devez les définir à l’aide de métadonnées dans la classe de fournisseur \<\>classe SchemaRowset. Définissez `m_bColumnHasDefault = VARIANT_TRUE`.

Vous avez également la responsabilité de définir les indicateurs de colonne, qui sont spécifiés à l’aide du type énuméré DBCOLUMNFLAGS. Les indicateurs de colonne décrivent les caractéristiques de colonne.

Par exemple, dans la classe `CUpdateSessionColSchemaRowset` dans `UpdatePV` (dans session. h), la première colonne est configurée de la façon suivante :

```cpp
// Set up column 1
trData[0].m_ulOrdinalPosition = 1;
trData[0].m_bIsNullable = VARIANT_FALSE;
trData[0].m_bColumnHasDefault = VARIANT_TRUE;
trData[0].m_nDataType = DBTYPE_UI4;
trData[0].m_nNumericPrecision = 10;
trData[0].m_ulColumnFlags = DBCOLUMNFLAGS_WRITE |
                            DBCOLUMNFLAGS_ISFIXEDLENGTH;
lstrcpyW(trData[0].m_szColumnDefault, OLESTR("0"));
m_rgRowData.Add(trData[0]);
```

Ce code spécifie, entre autres choses, que la colonne prend en charge la valeur par défaut 0, qu’elle peut être écrite et que toutes les données de la colonne ont la même longueur. Si vous souhaitez que les données d’une colonne aient une longueur variable, vous ne devez pas définir cet indicateur.

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur OLE DB](creating-an-ole-db-provider.md)

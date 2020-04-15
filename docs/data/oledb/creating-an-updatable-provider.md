---
title: Création d'un fournisseur actualisable
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 720ceba397d17642402de4d44cbb4481852fa153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365555"
---
# <a name="creating-an-updatable-provider"></a>Création d'un fournisseur actualisable

Visual CMD prend en charge les fournisseurs ou les fournisseurs updatables qui peuvent mettre à jour (écrire à) le magasin de données. Ce sujet traite de la façon de créer des fournisseurs updatables à l’aide de modèles OLE DB.

Ce sujet suppose que vous commencez avec un fournisseur réalisable. Il y a deux étapes pour créer un fournisseur updatable. Vous devez d’abord décider comment le fournisseur apportera des modifications au magasin de données; précisément, si des modifications doivent être apportées immédiatement ou reportées jusqu’à ce qu’une commande de mise à jour soit émise. La section «[Making Providers Updatable](#vchowmakingprovidersupdatable)» décrit les modifications et les paramètres que vous devez effectuer dans le code fournisseur.

Ensuite, vous devez vous assurer que votre fournisseur contient toutes les fonctionnalités pour prendre en charge tout ce que le consommateur pourrait en demander. Si le consommateur veut mettre à jour le magasin de données, le fournisseur doit contenir du code qui persiste les données au magasin de données. Par exemple, vous pouvez utiliser la bibliothèque C Run-Time ou MFC pour effectuer de telles opérations sur votre source de données. La section «[Écrire à la source de données](#vchowwritingtothedatasource)» décrit comment écrire à la source de données, traiter les valeurs NULL et par défaut, et définir des indicateurs de colonne.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) est un exemple de fournisseur updatable. UpdatePV est le même que MyProv, mais avec un support updatable.

## <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>Rendre les fournisseurs Updatable

La clé pour rendre un fournisseur updatable est de comprendre quelles opérations vous voulez que votre fournisseur effectue sur le magasin de données et comment vous voulez que le fournisseur effectue ces opérations. Plus précisément, la question principale est de savoir si les mises à jour du magasin de données doivent être effectuées immédiatement ou reportées (par lots) jusqu’à ce qu’une commande de mise à jour soit émise.

Vous devez d’abord `IRowsetChangeImpl` décider `IRowsetUpdateImpl` d’hériter ou de dans votre classe de rowset. Selon lequel d’entre eux vous choisissez d’implémenter, `InsertRows`la `DeleteRows`fonctionnalité de trois méthodes sera affectée: `SetData`, , et .

- Si vous héritez [d’IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), appeler ces trois méthodes change immédiatement le magasin de données.

- Si vous héritez de [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), les méthodes `Update`reportent les modifications au magasin de données jusqu’à ce que vous appeliez, `GetOriginalData`, ou `Undo`. Si la mise à jour comporte plusieurs modifications, elles sont effectuées en mode lot (notez que les modifications de lotage peuvent ajouter des frais généraux de mémoire considérables).

Notez `IRowsetUpdateImpl` qui `IRowsetChangeImpl`dérive de . Ainsi, `IRowsetUpdateImpl` vous donne la capacité de changement plus la capacité de lot.

### <a name="to-support-updatability-in-your-provider"></a>Pour soutenir la facilité d’accès dans votre fournisseur

1. Dans votre classe rowset, héritez de `IRowsetChangeImpl` ou `IRowsetUpdateImpl`. Ces classes fournissent des interfaces appropriées pour changer le magasin de données :

   **Ajout d’IRowsetChange**

   Ajoutez `IRowsetChangeImpl` à votre chaîne d’héritage en utilisant ce formulaire :

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   Ajoutez `COM_INTERFACE_ENTRY(IRowsetChange)` également `BEGIN_COM_MAP` à la section dans votre classe rowset.

   **Ajout d’IRowsetUpdate**

   Ajoutez `IRowsetUpdate` à votre chaîne d’héritage en utilisant ce formulaire :

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > Vous devez `IRowsetChangeImpl` supprimer la ligne de votre chaîne d’héritage. Cette seule exception à la directive mentionnée `IRowsetChangeImpl`précédemment doit inclure le code pour .

1. Ajoutez ce qui suit`BEGIN_COM_MAP ... END_COM_MAP`à votre carte COM ( ):

   |  Si vous implémentez   |           Ajouter à la carte COM             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Si vous implémentez | Ajouter à la carte de l’ensemble de propriété |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. Dans votre commande, ajoutez ce qui`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`suit à votre carte d’ensemble de propriété ( )

   |  Si vous implémentez   |                                             Ajouter à la carte de l’ensemble de propriété                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. Dans votre carte d’ensemble de propriété, vous devez également inclure tous les paramètres suivants tels qu’ils apparaissent ci-dessous :

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

   Vous pouvez trouver les valeurs utilisées dans ces appels macro en regardant dans Atldb.h pour les pièces d’identité et les valeurs de propriété (si Atldb.h diffère de la documentation en ligne, Atldb.h remplace la documentation).

   > [!NOTE]
   > Bon nombre `VARIANT_FALSE` `VARIANT_TRUE` des modèles OLE DB et les paramètres sont requis; les spécifications OLE DB dit qu’ils peuvent être lus / écrire, mais les modèles OLE DB ne peut prendre en charge qu’une seule valeur.

   **Si vous implémentez IRowsetChangeImpl**

   Si vous `IRowsetChangeImpl`implémentez, vous devez définir les propriétés suivantes sur votre fournisseur. Ces propriétés sont principalement utilisées `ICommandProperties::SetProperties`pour demander des interfaces à travers .

   - `DBPROP_IRowsetChange`: Réglage de `DBPROP_IRowsetChange`ce réglage automatiquement .

   - `DBPROP_UPDATABILITY`: Un bitmask précisant `IRowsetChange`les `SetData` `DeleteRows`méthodes `InsertRow`prises en charge sur : , , ou .

   - `DBPROP_CHANGEINSERTEDROWS`: Le `IRowsetChange::DeleteRows` consommateur `SetData` peut appeler ou pour les rangées nouvellement insérées.

   - `DBPROP_IMMOBILEROWS`: Rowset ne réorganisera pas les lignes insérées ou mises à jour.

   **Si vous implémentez IRowsetUpdateImpl**

   Si vous `IRowsetUpdateImpl`implémentez, vous devez définir les propriétés suivantes `IRowsetChangeImpl` sur votre fournisseur, en plus de définir toutes les propriétés pour précédemment énumérés:

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: Doit être READ_ONLY ET VARIANT_TRUE.

   - `DBPROP_OWNUPDATEDELETE`: Doit être READ_ONLY ET VARIANT_TRUE.

   - `DBPROP_OTHERINSERT`: Doit être READ_ONLY ET VARIANT_TRUE.

   - `DBPROP_OTHERUPDATEDELETE`: Doit être READ_ONLY ET VARIANT_TRUE.

   - `DBPROP_REMOVEDELETED`: Doit être READ_ONLY ET VARIANT_TRUE.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > Si vous prenez en charge les notifications, vous pourriez également avoir d’autres propriétés ainsi; voir la `IRowsetNotifyCP` section sur cette liste.

## <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>Écrire à la source de données

Pour lire à partir de `Execute` la source de données, appelez la fonction. Pour écrire à la source `FlushData` de données, appelez la fonction. (Dans un sens général, rincer les moyens pour enregistrer les modifications que vous faites à une table ou un index à disque.)

```cpp
FlushData(HROW, HACCESSOR);
```

Les arguments de poignée de ligne (HROW) et de poignée d’accesseur (HACCESSOR) vous permettent de spécifier la région à écrire. En règle générale, vous écrivez un seul champ de données à la fois.

La `FlushData` méthode écrit des données dans le format dans lequel elles ont été stockées à l’origine. Si vous ne remplacez pas cette fonction, votre fournisseur fonctionnera correctement, mais les modifications ne seront pas rincées au magasin de données.

### <a name="when-to-flush"></a>Quand à Flush

Les modèles fournisseurs appellent FlushData chaque fois que les données doivent être écrites au magasin de données; cela se produit généralement (mais pas toujours) à la suite d’appels aux fonctions suivantes :

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows`(s’il y a de nouvelles données à insérer dans la rangée)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Fonctionnement

Le consommateur fait un appel qui nécessite une couleur (comme la mise à jour) et cet appel est transmis au fournisseur, ce qui fait toujours ce qui suit:

- Appels `SetDBStatus` chaque fois que vous avez une valeur de statut liée.

- Vérifie les drapeaux de colonne.

- Appelle `IsUpdateAllowed`.

Ces trois étapes aident à assurer la sécurité. Ensuite, le `FlushData`fournisseur appelle .

### <a name="how-to-implement-flushdata"></a>Comment mettre en œuvre FlushData

Pour `FlushData`implémenter, vous devez prendre en compte plusieurs questions :

S’assurer que le magasin de données peut gérer les changements.

Gestion des valeurs NULL.

### <a name="handling-default-values"></a>Gestion des valeurs par défaut.

Pour mettre `FlushData` en œuvre votre propre méthode, vous devez :

- Allez à votre classe de rowset.

- Dans la classe rowset mettre la déclaration de:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Fournir une `FlushData`mise en œuvre de .

Une bonne `FlushData` mise en œuvre des magasins que les lignes et les colonnes qui sont effectivement mis à jour. Vous pouvez utiliser les paramètres HROW et HACCESSOR pour déterminer la ligne et la colonne actuelles stockées pour l’optimisation.

Typiquement, le plus grand défi est de travailler avec votre propre magasin de données natif. Si possible, essayez de :

- Gardez la méthode d’écriture à votre magasin de données aussi simple que possible.

- Gérer les valeurs NULL (facultatives mais conseillées).

- Gérer les valeurs par défaut (facultatives mais conseillées).

La meilleure chose à faire est d’avoir des valeurs spécifiées réelles dans votre magasin de données pour les valeurs NULL et par défaut. Il est préférable si vous pouvez extrapoler ces données. Si ce n’est pas le cas, il vous est conseillé de ne pas autoriser les valeurs NULL et par défaut.

L’exemple suivant `FlushData` montre comment `RUpdateRowset` est `UpdatePV` mis en œuvre dans la classe de l’échantillon (voir Rowset.h dans le code de l’échantillon) :

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

### <a name="handling-changes"></a>Manipulation des changements

Pour que votre fournisseur gère les modifications, vous devez d’abord vous assurer que votre magasin de données (comme un fichier texte ou un fichier vidéo) dispose d’installations qui vous permettent d’apporter des modifications à ce sujet. Si ce n’est pas le cas, vous devez créer ce code séparément du projet fournisseur.

### <a name="handling-null-data"></a>Manipulation des données NULL

Il est possible qu’un utilisateur final envoie des données NULL. Lorsque vous écrivez des valeurs NULL aux champs de la source de données, il peut y avoir des problèmes potentiels. Imaginez une demande de prise de commandes qui accepte les valeurs pour la ville et le code postal; elle pourrait accepter l’une ou l’autre des valeurs, mais pas non plus, parce que dans ce cas, la livraison serait impossible. Vous devez donc restreindre certaines combinaisons de valeurs NULL dans des domaines qui ont du sens pour votre application.

En tant que développeur fournisseur, vous devez considérer comment vous stockerez ces données, comment vous lirez ces données à partir du magasin de données, et comment vous le spécifiez à l’utilisateur. Plus précisément, vous devez réfléchir à la façon de modifier l’état des données de l’ensemble de données dans la source de données (par exemple, DataStatus et NULL). Vous décidez de la valeur à laquelle retourner lorsqu’un consommateur accède à un champ contenant une valeur NULL.

Regardez le code dans l’échantillon UpdatePV; il illustre comment un fournisseur peut gérer les données NULL. Dans UpdatePV, le fournisseur stocke les données NULL en écrivant la chaîne "NULL" dans le magasin de données. Lorsqu’il lit les données NULL du magasin de données, il voit cette chaîne et vide ensuite le tampon, créant une chaîne NULL. Il a également un `IRowsetImpl::GetDBStatus` remplacement dans lequel il retourne DBSTATUS_S_ISNULL si cette valeur de données est vide.

### <a name="marking-nullable-columns"></a>Marquage Des colonnes nuls

Si vous implémentez également `IDBSchemaRowsetImpl`des rames de schéma (voir ), votre implémentation doit spécifier dans le DBSCHEMA_COLUMNS ligne (généralement marquée dans votre fournisseur par CxxxSchemaColSchemaRowset) que la colonne est annulée.

Vous devez également spécifier que toutes les colonnes in `GetColumnInfo`nullables contiennent la valeur DBCOLUMNFLAGS_ISNULLABLE dans votre version de la .

Dans la mise en œuvre des modèles OLE DB, si vous ne marquez pas les colonnes comme étant nulles, le fournisseur suppose qu’elles doivent contenir une valeur et ne permettront pas au consommateur de lui envoyer des valeurs nulles.

L’exemple suivant `CommonGetColInfo` montre comment la fonction est implémentée dans CUpdateCommand (voir UpProvRS.cpp) dans UpdatePV. Notez comment les colonnes ont cette DBCOLUMNFLAGS_ISNULLABLE pour les colonnes annulables.

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

Comme pour les données NULL, vous avez la responsabilité de faire face à l’évolution des valeurs par défaut.

Le défaut `FlushData` `Execute` et est de retourner S_OK. Par conséquent, si vous ne l’emportez pas sur cette fonction, les modifications semblent réussir (S_OK seront retournées), mais elles ne seront pas transmises au magasin de données.

Dans `UpdatePV` l’échantillon (dans Rowset.h), la `SetDBStatus` méthode gère les valeurs par défaut comme suit :

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

### <a name="column-flags"></a>Drapeaux de colonne

Si vous soutenez les valeurs par défaut sur vos colonnes,\>vous devez la définir à l’aide de métadonnées dans la classe SchemaRowset de classe \<fournisseur. Définissez `m_bColumnHasDefault = VARIANT_TRUE`.

Vous avez également la responsabilité de définir les drapeaux de colonne, qui sont spécifiés à l’aide du type DBCOLUMNFLAGS énumérés. Les drapeaux de colonne décrivent les caractéristiques de la colonne.

Par exemple, `CUpdateSessionColSchemaRowset` dans `UpdatePV` la classe dans (dans Session.h), la première colonne est configuré de cette façon:

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

Ce code précise, entre autres choses, que la colonne prend en charge une valeur par défaut de 0, qu’elle soit écrivante et que toutes les données de la colonne ont la même longueur. Si vous voulez que les données dans une colonne aient une longueur variable, vous ne définiriez pas ce drapeau.

## <a name="see-also"></a>Voir aussi

[Création d’un fournisseur OLE DB](creating-an-ole-db-provider.md)

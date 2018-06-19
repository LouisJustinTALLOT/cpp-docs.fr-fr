---
title: Création d’un fournisseur actualisable | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 317ccd043b3a69489f9cbd2737ad7741389863c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098639"
---
# <a name="creating-an-updatable-provider"></a>Création d'un fournisseur actualisable
Visual C++ prend en charge les fournisseurs actualisables ou des fournisseurs qui peuvent mettre à jour (modifier) le magasin de données. Cette rubrique explique comment créer des fournisseurs de mettre à jour à l’aide de modèles OLE DB.  
  
 Cette rubrique suppose que vous démarrez avec un fournisseur opérationnel. Il existe deux étapes pour créer un fournisseur actualisable. Vous devez d’abord déterminer comment le fournisseur d’apporter des modifications au magasin de données ; plus précisément, si modifications doivent être effectuées immédiatement ou différée jusqu'à ce que l’émission d’une commande de mise à jour. La section «[fournisseurs actualisables](#vchowmakingprovidersupdatable)» décrit les modifications et les paramètres que vous devez effectuer dans le code du fournisseur.  
  
 Ensuite, il se peut que vous devez vous assurer que votre fournisseur contient toutes les fonctionnalités pour prendre en charge tout ce que le consommateur peut demander de celui-ci. Si le consommateur souhaite mettre à jour le magasin de données, le fournisseur doit contenir du code qui conserve les données de la banque de données. Par exemple, vous pouvez utiliser la bibliothèque C Run-Time ou MFC pour effectuer ces opérations sur votre source de données. La section «[l’écriture dans la Source de données](#vchowwritingtothedatasource)» décrit comment écrire dans la source de données, traiter les **NULL** et valeurs par défaut et définir des indicateurs de colonnes.  
  
> [!NOTE]
>  UpdatePV est un exemple d’un fournisseur actualisable. UpdatePV est le même que MyProv, mais avec prise en charge de mettre à jour.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Fournisseurs actualisables  
 La clé pour rendre un fournisseur actualisable est de comprendre les opérations que vous souhaitez que votre fournisseur d’effectuer sur le magasin de données et comment vous souhaitez que le fournisseur pour effectuer ces opérations. Plus précisément, le principal problème est si les mises à jour de la banque de données doivent être effectuées immédiatement ou différée (traités par lot) jusqu'à ce qu’une commande de mise à jour est émise.  
  
 Vous devez d’abord déterminer s’il faut hériter `IRowsetChangeImpl` ou `IRowsetUpdateImpl` dans votre classe rowset. Selon que vous choisissez d’implémenter les fonctionnalités des trois méthodes seront affectées : `SetData`, **InsertRows**, et `DeleteRows`.  
  
-   Si vous héritez [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), appel de ces trois méthodes modifie immédiatement le magasin de données.  
  
-   Si vous héritez [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), les méthodes de différeront des modifications au magasin de données jusqu'à ce que vous appeliez **mise à jour**, `GetOriginalData`, ou **Annuler**. Si la mise à jour implique plusieurs modifications, elles sont exécutées en mode de traitement par lots (Notez que le traitement par lot de modifications peut ajouter des ressources mémoire considérables).  
  
 Notez que `IRowsetUpdateImpl` dérive `IRowsetChangeImpl`. Par conséquent, `IRowsetUpdateImpl` permet de modifier de capacité plus de capacité de traitement par lots.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Pour prendre en charge les mises à jour dans votre fournisseur  
  
1.  Dans votre classe rowset, héritez `IRowsetChangeImpl` ou `IRowsetUpdateImpl`. Ces classes fournissent les interfaces appropriées pour la modification de la banque de données :  
  
     **Ajout de IRowsetChange**  
  
     Ajoutez `IRowsetChangeImpl` à votre chaîne d’héritage à l’aide de ce formulaire :  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Ajoutez également `COM_INTERFACE_ENTRY(IRowsetChange)` à la `BEGIN_COM_MAP` section dans votre classe rowset.  
  
     **Ajout de IRowsetUpdate**  
  
     Ajoutez `IRowsetUpdate` à votre chaîne d’héritage à l’aide de ce formulaire :  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Vous devez supprimer la `IRowsetChangeImpl` ligne à partir de votre chaîne d’héritage. Cette unique exception à la directive mentionnée doit inclure le code de `IRowsetChangeImpl`.  
  
2.  Ajoutez le code suivant à votre mappage COM (**BEGIN_COM_MAP... END_COM_MAP**) :  
  
    |Si vous implémentez|Ajouter au mappage COM|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  Dans votre commande, ajoutez le code suivant à votre carte de jeu de propriétés (**BEGIN_PROPSET_MAP... END_PROPSET_MAP**) :  
  
    |Si vous implémentez|Ajoutez au mappage des propriétés|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  Dans le mappage de jeu de propriétés, vous incluez également tous les paramètres suivants de telles qu’elles apparaissent ci-dessous :  
  
    ```  
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
  
     Vous pouvez trouver les valeurs utilisées dans ces appels de macros dans Atldb.h pour l’ID de propriété et les valeurs (si Atldb.h diffère de la documentation en ligne, Atldb.h remplace la documentation).  
  
    > [!NOTE]
    >  Un grand nombre de la **VARIANT_FALSE** et `VARIANT_TRUE` paramètres sont requis par les modèles OLE DB ; la spécification OLE DB indique qu’ils peuvent être en lecture/écriture, mais les modèles OLE DB peuvent prendre uniquement en charge une seule valeur.  
  
     **Si vous implémentez IRowsetChangeImpl**  
  
     Si vous implémentez `IRowsetChangeImpl`, vous devez définir les propriétés suivantes sur votre fournisseur. Ces propriétés sont principalement utilisées pour demander les interfaces via **ICommandProperties::SetProperties**.  
  
    -   `DBPROP_IRowsetChange`: Définition de ce automatiquement définit **DBPROP_IRowsetChange**.  
  
    -   `DBPROP_UPDATABILITY`: Masque de bits spécifiant les méthodes prises en charge sur `IRowsetChange`: `SetData`, `DeleteRows`, ou `InsertRow`.  
  
    -   `DBPROP_CHANGEINSERTEDROWS`: Le consommateur peut appeler **IRowsetChange::DeleteRows** ou `SetData` pour les lignes nouvellement insérées.  
  
    -   `DBPROP_IMMOBILEROWS`: Ensemble de lignes ne réorganise pas les lignes insérées ou mises à jour.  
  
     **Si vous implémentez IRowsetUpdateImpl**  
  
     Si vous implémentez `IRowsetUpdateImpl`, vous devez définir les propriétés suivantes sur votre fournisseur, parallèlement à la définition de toutes les propriétés de `IRowsetChangeImpl` mentionnés précédemment :  
  
    -   `DBPROP_IRowsetUpdate`.  
  
    -   `DBPROP_OWNINSERT`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    -   `DBPROP_OWNUPDATEDELETE`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    -   `DBPROP_OTHERINSERT`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    -   `DBPROP_OTHERUPDATEDELETE`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    -   `DBPROP_REMOVEDELETED`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    -   `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Si vous prenez en charge les notifications, peut également avoir d’autres propriétés ; consultez la section sur `IRowsetNotifyCP` pour cette liste.  
  
     Par exemple, de la façon dont les propriétés sont définies, consultez définie la propriété dans **CUpdateCommand** (dans Rowset.h) dans [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f).  
  
##  <a name="vchowwritingtothedatasource"></a> Écriture dans la Source de données  
 Pour lire à partir de la source de données, appelez le **Execute** (fonction). Pour écrire dans la source de données, appelez le `FlushData` (fonction). (Dans un sens général, flush signifie enregistrer les modifications que vous apportez à une table ou un index sur le disque).  
  
```  
FlushData(HROW, HACCESSOR);  
```  
  
 Le handle de ligne (*HROW*) et le handle d’accesseur (*HACCESSOR*) arguments permettent de spécifier la zone d’écriture. En règle générale, vous écrivez un champ de données à la fois.  
  
 Le `FlushData` méthode écrit des données dans le format dans lequel elle a été enregistrée à l’origine. Si vous ne substituez pas cette fonction, votre fournisseur fonctionnera correctement mais les modifications ne sont pas vidées vers le magasin de données.  
  
### <a name="when-to-flush"></a>Quand effectuer un vidage  
 Le modèles du fournisseur appellent `FlushData` chaque fois que les données doivent être écrites dans le magasin de données ; cela généralement (mais pas toujours) se produit suite à des appels aux fonctions suivantes :  
  
-   **IRowsetChange::DeleteRows**  
  
-   **IRowsetChange::SetData**  
  
-   **IRowsetChange::InsertRows** (il s'est nouvelles données à insérer dans la ligne)  
  
-   **IRowsetUpdate::Update**  
  
### <a name="how-it-works"></a>Son fonctionnement  
 Le consommateur effectue un appel qui requiert un vidage (tel que **mise à jour**) et cet appel est passé au fournisseur, qui effectue toujours les éléments suivants :  
  
-   Appels `SetDBStatus` chaque fois que vous avez une valeur d’état liée (consultez *de référence des programmeurs OLE DB*, chapitre 6, *parties de données : état*).  
  
-   Vérifie les indicateurs de colonne.  
  
-   Appelle `IsUpdateAllowed`.  
  
 Ces trois étapes assurent la sécurité. Ensuite, le fournisseur appelle `FlushData`.  
  
### <a name="how-to-implement-flushdata"></a>Comment implémenter FlushData  
 Pour implémenter `FlushData`, vous devez prendre en compte plusieurs problèmes :  
  
-   S’assurer que le magasin de données peut gérer les modifications.  
  
-   La gestion des **NULL** valeurs.  
  
-   La gestion des valeurs par défaut.  
  
 Pour implémenter votre propre `FlushData` (méthode), vous devez :  
  
-   Accédez à votre classe rowset.  
  
-   Dans l’ensemble de lignes classe placer la déclaration de :  
  
```  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    // Insert your implementation here and return an HRESULT.  
}  
```  
  
-   Fournir une implémentation de `FlushData`.  
  
 Une implémentation correcte de `FlushData` stocke uniquement les lignes et les colonnes qui sont effectivement mises à jour. Vous pouvez utiliser la *HROW* et *HACCESSOR* paramètres pour déterminer la ligne actuelle et la colonne qui sont stockées pour l’optimisation.  
  
 En règle générale, le principal défi fonctionne avec votre propre magasin de données en mode natif. Si possible, essayez :  
  
-   Conserver la méthode d’écriture à votre magasin de données aussi simple que possible.  
  
-   Gérer les **NULL** values (facultatif mais conseillées).  
  
-   Gérer les valeurs par défaut (facultatives mais conseillées).  
  
 La meilleure chose à faire est d’avoir vraies valeurs spécifiées dans le magasin de données pour **NULL** et valeurs par défaut. Il est préférable si vous pouvez extrapoler ces données. Si non, nous vous recommandons ne pas autoriser **NULL** et valeurs par défaut.  
  
 L’exemple suivant montre comment `FlushData` est implémenté dans le `RUpdateRowset` classe dans le [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) exemple (consultez Rowset.h dans l’exemple de code) :  
  
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
 Pour votre fournisseur gère les modifications, vous devez tout d’abord s’assurer que votre banque de données (par exemple, un fichier texte ou un fichier vidéo) comporte des fonctionnalités qui vous permettent d’apporter des modifications. Si elle n’est pas le cas, vous devez créer ce code séparément à partir du projet du fournisseur.  
  
### <a name="handling-null-data"></a>La gestion des données de type NULL  
 Il est possible qu’un utilisateur final envoie **NULL** données. Lorsque vous écrivez **NULL** valeurs aux champs de la source de données, il peut y avoir des problèmes potentiels. Imaginez une application de prise de commande qui accepte des valeurs pour la ville et le code postal ; elle peut accepter un ou les deux valeurs, mais pas aucune des deux, car dans ce cas, remise serait impossible. Vous devez donc restreindre certaines combinaisons de **NULL** valeurs dans les champs qui ont un sens pour votre application.  
  
 En tant que développeur de fournisseurs, vous devez prendre en compte la façon dont vous souhaitez stocker ces données, comment vous lirez ces données à partir du magasin de données et la façon dont vous spécifiez que pour l’utilisateur. Plus précisément, vous devez considérer comment changer l’état des données du jeu de lignes dans la source de données (par exemple, DataStatus = **NULL**). Vous déterminez la valeur à retourner quand un consommateur accède à un champ contenant une **NULL** valeur.  
  
 Examinez le code dans le [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) exemple ; il illustre la façon dont un fournisseur peut gérer **NULL** données. Dans UpdatePV, le fournisseur stocke **NULL** données en écrivant la chaîne « NULL » dans le magasin de données. Lorsqu’il lit **NULL** du magasin de données à partir des données, il visualise cette chaîne puis vide la mémoire tampon, création d’un **NULL** chaîne. Il dispose également d’une substitution de `IRowsetImpl::GetDBStatus` dans laquelle il retourne **DBSTATUS_S_ISNULL** si cette valeur de données est vide.  
  
### <a name="marking-nullable-columns"></a>Marquage des colonnes autorisant des valeurs null  
 Si vous implémentez également des ensembles de lignes de schéma (voir `IDBSchemaRowsetImpl`), votre implémentation doit spécifier dans le **DBSCHEMA_COLUMNS** ensemble de lignes (généralement marqué dans le fournisseur par **C***xxx***SchemaColSchemaRowset**) que la colonne est nullable.  
  
 Vous devez également spécifier que toutes les colonnes contiennent le **DBCOLUMNFLAGS_ISNULLABLE** valeur dans votre version de la `GetColumnInfo`.  
  
 Dans l’implémentation des modèles OLE DB, si vous ne marquez pas les colonnes comme autorisant la valeur null, le fournisseur suppose qu’ils doivent contenir une valeur et ne permettra pas au consommateur de lui envoyer des valeurs null.  
  
 L’exemple suivant montre comment la **CommonGetColInfo** (fonction) est implémentée dans **CUpdateCommand** (consultez UpProvRS.cpp) dans UpdatePV. Notez la façon dont les colonnes ont cela **DBCOLUMNFLAGS_ISNULLABLE** pour les colonnes autorisant des valeurs NULL.  
  
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
 Comme avec **NULL** des données, vous avez la responsabilité de modifier les valeurs par défaut.  
  
 La valeur par défaut de `FlushData` et **Execute** doit retourner `S_OK`. Par conséquent, si vous ne substituez pas cette fonction, les modifications apparaissent réussisse (`S_OK` sera retourné), mais ils ne sont pas transmis au magasin de données.  
  
 Dans le [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) sample (dans Rowset.h), la `SetDBStatus` méthode gère les valeurs par défaut comme suit :  
  
```  
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
 Si vous prenez en charge les valeurs par défaut sur les colonnes, vous devez définir à l’aide de métadonnées dans le **\<***classe de fournisseur***>SchemaRowset** classe. Définissez *m_bColumnHasDefault* = `VARIANT_TRUE`.  
  
 Vous pouvez définir les indicateurs de colonnes, qui sont spécifiées à l’aide de la **DBCOLUMNFLAGS** type énuméré. Les indicateurs de colonnes décrivent les caractéristiques de la colonne.  
  
 Par exemple, dans le `CUpdateSessionColSchemaRowset` classe dans [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) (dans Session.h), la première colonne est configurée de cette façon :  
  
```  
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
  
 Ce code spécifie, entre autres choses, que la colonne prend en charge une valeur par défaut 0, qu’il soit accessible en écriture, et que toutes les données dans la colonne ont la même longueur. Si vous souhaitez que les données dans une colonne doit avoir une longueur variable, vous définiriez pas cet indicateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
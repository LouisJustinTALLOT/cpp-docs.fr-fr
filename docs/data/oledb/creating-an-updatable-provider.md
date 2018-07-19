---
title: Création d’un fournisseur actualisable | Microsoft Docs
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
ms.openlocfilehash: cbcd69168b70e8d85bf2b90c3f456f79cd1c228c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954582"
---
# <a name="creating-an-updatable-provider"></a>Création d'un fournisseur actualisable

Visual C++ prend en charge les fournisseurs actualisables ou des fournisseurs qui peuvent mettre à jour (modifier) le magasin de données. Cette rubrique explique comment créer des fournisseurs d’être mise à jour à l’aide de modèles OLE DB.  
  
 Cette rubrique suppose que vous démarrez avec un fournisseur opérationnel. Il existe deux étapes pour créer un fournisseur actualisable. Vous devez d’abord déterminer comment le fournisseur sera apportée à la banque de données ; plus précisément, si modifications doivent être effectuées immédiatement ou différée jusqu'à ce que l’émission d’une commande de mise à jour. La section «[fournisseurs actualisables](#vchowmakingprovidersupdatable)» décrit les modifications et les paramètres que vous devez effectuer dans le code du fournisseur.  
  
 Ensuite, il se peut que vous devez vous assurer que votre fournisseur contient toutes les fonctionnalités pour prendre en charge tout ce que le consommateur peut lui demander. Si le consommateur souhaite mettre à jour le magasin de données, le fournisseur doit contenir du code qui rend persistantes les données au magasin de données. Par exemple, vous pouvez utiliser la bibliothèque du Run-Time C ou MFC pour exécuter des opérations sur votre source de données. La section «[écriture dans la Source de données](#vchowwritingtothedatasource)» explique comment écrire dans la source de données, pour traiter des `NULL` et valeurs par défaut et définir des indicateurs de la colonne.  
  
> [!NOTE]
>  UpdatePV est un exemple d’un fournisseur actualisable. UpdatePV est le même que MyProv, mais avec prise en charge de mettre à jour.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Fournisseurs actualisables  

 La clé pour rendre un fournisseur actualisable consiste à comprendre les opérations que vous voulez que votre fournisseur d’effectuer sur le magasin de données et comment vous voulez que le fournisseur pour effectuer ces opérations. Plus précisément, le problème majeur est indique si les mises à jour au magasin de données doivent être effectuées immédiatement ou différée (lot) jusqu'à ce qu’une commande de mise à jour est émise.  
  
 Vous devez d’abord déterminer s’il faut hériter `IRowsetChangeImpl` ou `IRowsetUpdateImpl` dans votre classe rowset. Selon que vous choisissez d’implémenter les fonctionnalités des trois méthodes seront affectées : `SetData`, `InsertRows`, et `DeleteRows`.  
  
- Si vous héritez de [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), appel de ces trois méthodes modifie immédiatement le magasin de données.  
  
- Si vous héritez de [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), les méthodes différeront des modifications au magasin de données jusqu'à ce que vous appeliez `Update`, `GetOriginalData`, ou `Undo`. Si la mise à jour implique plusieurs modifications, elles sont exécutées en mode batch (Notez que le traitement par lot de modifications peut ajouter des ressources mémoire considérables).  
  
 Notez que `IRowsetUpdateImpl` dérive `IRowsetChangeImpl`. Par conséquent, `IRowsetUpdateImpl` donne vous modifiez la fonction de traitement par lots en plus de fonctionnalité.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Pour prendre en charge les mises à jour dans votre fournisseur  
  
1. Dans votre classe rowset, héritent de `IRowsetChangeImpl` ou `IRowsetUpdateImpl`. Ces classes fournissent des interfaces appropriées pour la modification de la banque de données :  
  
     **Ajout de IRowsetChange**  
  
     Ajouter `IRowsetChangeImpl` à votre chaîne d’héritage à l’aide de ce formulaire :  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Ajoutez également `COM_INTERFACE_ENTRY(IRowsetChange)` à la `BEGIN_COM_MAP` section dans votre classe rowset.  
  
     **Ajout de IRowsetUpdate**  
  
     Ajouter `IRowsetUpdate` à votre chaîne d’héritage à l’aide de ce formulaire :  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Vous devez supprimer la `IRowsetChangeImpl` ligne à partir de votre chaîne d’héritage. Cette seule exception à la directive mentionnée précédemment doit inclure le code pour `IRowsetChangeImpl`.  
  
2.  Ajoutez le code suivant à votre mappage COM (`BEGIN_COM_MAP ... END_COM_MAP`) :  
  
    |Si vous implémentez|Ajouter au mappage COM|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  Dans votre commande, ajoutez le code suivant au mappage des propriétés (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`) :  
  
    |Si vous implémentez|Ajoutez au mappage de propriété|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  Dans le mappage de jeu de propriété, vous incluez également tous les paramètres suivants de telles qu’elles apparaissent ci-dessous :  
  
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
  
     Vous trouverez les valeurs utilisées dans ces appels de macro en recherchant dans Atldb.h les ID de propriété et les valeurs (si Atldb.h diffère de la documentation en ligne, Atldb.h remplace la documentation).  
  
    > [!NOTE]
    >  Un grand nombre de la `VARIANT_FALSE` et `VARIANT_TRUE` paramètres sont requis par les modèles OLE DB ; la spécification OLE DB indique qu’ils peuvent être en lecture/écriture, mais les modèles OLE DB peuvent prendre uniquement en charge une seule valeur.  
  
     **Si vous implémentez IRowsetChangeImpl**  
  
     Si vous implémentez `IRowsetChangeImpl`, vous devez définir les propriétés suivantes sur votre fournisseur. Ces propriétés sont principalement utilisées pour demander les interfaces via `ICommandProperties::SetProperties`.  
  
    - `DBPROP_IRowsetChange`: Définition de cette opération effectue automatiquement définit `DBPROP_IRowsetChange`.  
  
    - `DBPROP_UPDATABILITY`: Masque de bits spécifiant les méthodes prises en charge sur `IRowsetChange`: `SetData`, `DeleteRows`, ou `InsertRow`.  
  
    - `DBPROP_CHANGEINSERTEDROWS`: Le consommateur peut appeler `IRowsetChange::DeleteRows` ou `SetData` des lignes nouvellement insérées.  
  
    - `DBPROP_IMMOBILEROWS`: Ensemble de lignes ne réorganise pas les lignes insérées ou mises à jour.  
  
     **Si vous implémentez IRowsetUpdateImpl**  
  
     Si vous implémentez `IRowsetUpdateImpl`, vous devez définir les propriétés suivantes sur votre fournisseur, en outre à la définition de toutes les propriétés pour `IRowsetChangeImpl` mentionnés précédemment :  
  
    - `DBPROP_IRowsetUpdate`.  
  
    - `DBPROP_OWNINSERT`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    - `DBPROP_OWNUPDATEDELETE`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    - `DBPROP_OTHERINSERT`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    - `DBPROP_OTHERUPDATEDELETE`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    - `DBPROP_REMOVEDELETED`: Doit être READ_ONLY et VARIANT_TRUE.  
  
    - `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Si vous prenez en charge les notifications, vous pouvez être amené d’autres propriétés ; consultez la section sur `IRowsetNotifyCP` pour cette liste.  
  
##  <a name="vchowwritingtothedatasource"></a> Écriture dans la Source de données  
 Pour lire à partir de la source de données, appelez le `Execute` (fonction). Pour écrire dans la source de données, appelez le `FlushData` (fonction). (Dans un sens général, flush signifie pour enregistrer les modifications à qu'apporter à une table ou un index sur le disque).  


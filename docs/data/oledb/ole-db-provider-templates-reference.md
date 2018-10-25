---
title: Référence de modèles du fournisseur OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a49294ea864357e111abe4d6bfc6d2cbb1c8a61f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077632"
---
# <a name="ole-db-provider-templates-reference"></a>Référence des modèles du fournisseur OLE DB

Les classes et interfaces pour les modèles du fournisseur OLE DB peuvent être regroupées dans les catégories suivantes. La documentation de référence inclut également des informations sur le [macros pour les modèles du fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).

Les classes utilisent la convention d’affectation de noms suivante : une classe nommée avec le modèle `IWidgetImpl` fournirait une implémentation de l’interface `IWidget`.

## <a name="session-classes"></a>Classes de session

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
Crée une nouvelle session de l’objet de source de données et retourne l’interface demandée sur la session nouvellement créée. Interface obligatoire sur les objets de source de données.

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
Implémente des propriétés d’une session en appelant une fonction statique définie par le mappage de jeu de propriétés. Le mappage de jeu de propriétés doit être spécifié dans votre classe session. Interface obligatoire sur les sessions.

## <a name="rowset-classes"></a>Classes de l’ensemble de lignes

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

Fournit une implémentation d’ensemble de lignes OLE DB standard sans nécessiter l’héritage multiple de nombreuses interfaces d’implémentation. La seule méthode pour laquelle vous devez fournir l’implémentation est `Execute`.

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
Fournit une implémentation par défaut pour le handle de ligne, qui est utilisé dans le `IRowsetImpl` classe. Un handle de ligne est logiquement une balise unique pour une ligne de résultat. `IRowsetImpl` Crée un `CSimpleRow` pour chaque ligne demandée dans `IRowsetImpl::GetNextRows`.

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB requiert des fournisseurs implémenter un `HACCESSOR`, qui est une balise à un tableau de `DBBINDING` structures. Fournit des `HACCESSOR`s qui sont des adresses de la `BindType` structures. Obligatoire sur les ensembles de lignes et de commandes.

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
Délégués à une fonction statique définie par le mappage de colonne du fournisseur. Interface obligatoire sur les ensembles de lignes et de commandes.

[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
Fournit des informations sur la disponibilité de conversions de type sur une commande ou sur un ensemble de lignes. Obligatoire sur les commandes, les ensembles de lignes et les ensembles de lignes index. Implémente le `IConvertType` interface par délégation à l’objet de conversion fourni par OLE DB.

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
Implémente le `IDBSchemaRowset` interface et la fonction de créateur mise en modèle `CreateSchemaRowset`.

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
Ouvre et retourne un ensemble de lignes qui inclut toutes les lignes à partir d’une seule table de base ou un index. Interface obligatoire pour un objet de session.

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
Implémente la norme OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790) interface, ce qui permet la mise à jour des valeurs de colonnes dans les lignes existantes, la suppression de lignes et l’insertion de nouvelles lignes.

[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
Cette classe hérite de [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) et remplace [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite). `IRowsetCreatorImpl` effectue les mêmes fonctions que `IObjectWithSite` mais permet également les propriétés OLE DB `DBPROPCANSCROLLBACKWARDS` et `DBPROPCANFETCHBACKWARDS`.

[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
Implémente le `IRowsetIdentity` interface, ce qui vous permet de comparer si deux lignes de données sont identiques ou non.

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
Fournit une implémentation de la `IRowset` interface, qui est l’interface de l’ensemble de lignes de base.

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
Implémente les propriétés de l’ensemble de lignes à l’aide de la propriété jeu plan défini dans votre classe de commande. Interface obligatoire sur les ensembles de lignes.

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
Implémente la norme OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190) interface, qui extrait des lignes arbitraires à partir d’un ensemble de lignes. Pour prendre en charge des signets de OLE DB dans un ensemble de lignes, vérifiez l’ensemble de lignes à hériter de cette classe.

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
Implémente des fonctions pour informer les écouteurs sur le point de connexion de diffusion `IID_IRowsetNotify` des modifications apportées au contenu de l’ensemble de lignes. Implémentent des consommateurs qui gèrent les notifications [IRowsetNotify](/previous-versions/windows/desktop/ms712959) et l’inscrire sur ce point de connexion.

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
Implémente la norme OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401) interface, ce qui permet aux consommateurs de retarder la transmission des modifications apportées avec [IRowsetChange](/previous-versions/windows/desktop/ms715790) à source de données et annuler les modifications avant la transmission.

## <a name="command-classes"></a>Classes de commande

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
Fournit une implémentation de l’interface `ICommand`. Cette interface n’est pas visible, mais il est gérée par `ICommandTextImpl`. Une interface obligatoire sur l’objet command.

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
Cette implémentation de la `ICommandProperties` interface est fournie par une fonction statique définie par le `BEGIN_PROPSET_MAP` (macro). Obligatoire sur les commandes.

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
Définit, stocke et retourne le texte de commande. Obligatoire sur les commandes.

[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
Crée une nouvelle commande à partir de l’objet de session et retourne l’interface demandée sur la commande qui vient d’être créée. Interface facultative sur les objets de session.

Autres classes de commande sont `IColumnsInfoImpl` et `IAccessorImpl`, comme décrit dans la section de Classes de l’ensemble de lignes ci-dessus.

## <a name="data-source-classes"></a>Classes de Source de données

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
Crée et supprime la connexion avec le consommateur. Interface obligatoire sur les objets source de données et une interface facultative sur les énumérateurs.

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` est une interface obligatoire pour les objets de source de données et une interface facultative pour les énumérateurs. Toutefois, si un énumérateur expose `IDBInitialize`, elle doit exposer `IDBProperties` (propriétés sur la source de données).

[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
Obtient un pointeur d’interface à l’objet de source de données. Interface obligatoire sur la session.

## <a name="other-classes"></a>Autres Classes

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
Implémente des propriétés d’une série d’interfaces de propriété OLE DB (par exemple, `IDBProperties`, `ISessionProperties`, et `IRowsetInfo`).

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

Implémente la norme OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112) interface, ajout d’enregistrements à et récupérer des enregistrements d’un membre de données.

## <a name="see-also"></a>Voir aussi

[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Modèles OLE DB](../../data/oledb/ole-db-templates.md)
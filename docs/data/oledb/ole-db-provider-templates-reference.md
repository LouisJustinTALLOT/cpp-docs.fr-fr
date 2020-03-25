---
title: Référence des modèles du fournisseur OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: 567d4131229ee25d0d69ff4456398e05af387f0e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210039"
---
# <a name="ole-db-provider-templates-reference"></a>Référence des modèles du fournisseur OLE DB

Les classes et interfaces pour les modèles de fournisseur OLE DB peuvent être regroupées dans les catégories suivantes. La documentation de référence comprend également des informations sur les [macros pour les modèles de fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).

Les classes utilisent la Convention d’affectation de noms suivante : une classe nommée avec le modèle `IWidgetImpl` fournirait une implémentation de l’interface `IWidget`.

## <a name="session-classes"></a>Classes de session

[Idbcreatesessionimpl,](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
Crée une nouvelle session à partir de l’objet source de données et retourne l’interface demandée sur la session nouvellement créée. Interface obligatoire sur les objets de source de données.

[Isessionpropertiesimpl,](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
Implémente les propriétés de session en appelant une fonction statique définie par le mappage de jeu de propriétés. Le mappage de jeu de propriétés doit être spécifié dans votre classe de session. Interface obligatoire sur les sessions.

## <a name="rowset-classes"></a>Classes d’ensemble de lignes

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

Fournit une implémentation de l’ensemble de lignes standard OLE DB sans nécessiter plusieurs héritages de nombreuses interfaces d’implémentation. La seule méthode pour laquelle vous devez fournir l’implémentation est `Execute`.

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
Fournit une implémentation par défaut pour le handle de ligne, qui est utilisé dans la classe `IRowsetImpl`. Un descripteur de ligne est logiquement une étiquette unique pour une ligne de résultats. `IRowsetImpl` crée une `CSimpleRow` pour chaque ligne demandée dans `IRowsetImpl::GetNextRows`.

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB exige que les fournisseurs implémentent un `HACCESSOR`, qui est une balise d’un tableau de structures de `DBBINDING`. Fournit des `HACCESSOR`qui sont des adresses des structures `BindType`. Obligatoire sur les ensembles de lignes et les commandes.

[Icolumnsinfoimpl,](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
Délègue à une fonction statique définie par le mappage de colonnes du fournisseur. Interface obligatoire sur les ensembles de lignes et les commandes.

[Iconverttypeimpl,](../../data/oledb/iconverttypeimpl-class.md)<br/>
Donne des informations sur la disponibilité des conversions de type sur une commande ou sur un ensemble de lignes. Obligatoire sur les commandes, les ensembles de lignes et les ensembles de lignes d’index. Implémente l’interface `IConvertType` en déléguant à l’objet de conversion fourni par OLE DB.

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
Implémente l’interface `IDBSchemaRowset` et la fonction de créateur mise en œuvre `CreateSchemaRowset`.

[Iopenrowsetimpl,](../../data/oledb/iopenrowsetimpl-class.md)<br/>
Ouvre et retourne un ensemble de lignes qui comprend toutes les lignes d’une table ou d’un index de base unique. Interface obligatoire pour un objet de session.

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
Implémente l’interface OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) , qui permet la mise à jour des valeurs de colonnes dans les lignes existantes, la suppression de lignes et l’insertion de nouvelles lignes.

[IRowsetCreatorImpl,](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
Cette classe hérite de [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) et remplace [IObjectWithSite :: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). `IRowsetCreatorImpl` effectue les mêmes fonctions que `IObjectWithSite` mais active également les propriétés de OLE DB `DBPROPCANSCROLLBACKWARDS` et `DBPROPCANFETCHBACKWARDS`.

[Irowsetidentityimpl,](../../data/oledb/irowsetidentityimpl-class.md)<br/>
Implémente l’interface `IRowsetIdentity`, qui vous permet de comparer si deux lignes de données sont identiques ou non.

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
Fournit une implémentation de l’interface `IRowset`, qui est l’interface de l’ensemble de lignes de base.

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
Implémente les propriétés de l’ensemble de lignes à l’aide du mappage de jeu de propriétés défini dans votre classe Command. Interface obligatoire sur les ensembles de lignes.

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
Implémente l’interface OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) , qui extrait des lignes arbitraires d’un ensemble de lignes. Pour prendre en charge les signets OLE DB dans un ensemble de lignes, faites en sorte que l’ensemble de lignes hérite de cette classe.

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
Implémente des fonctions de diffusion pour informer les écouteurs sur le point de connexion `IID_IRowsetNotify` des modifications apportées au contenu de l’ensemble de lignes. Les consommateurs qui gèrent les notifications implémentent [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) et l’inscrivent sur ce point de connexion.

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
Implémente l’interface [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) OLE DB, qui permet aux consommateurs de retarder la transmission des modifications apportées à [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) à la source de données et d’annuler les modifications avant la transmission.

## <a name="command-classes"></a>Classes de commande

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
Fournit une implémentation de l’interface `ICommand`. Cette interface n’est pas visible, mais elle est gérée par `ICommandTextImpl`. Interface obligatoire sur l’objet de commande.

[Icommandpropertiesimpl,](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
Cette implémentation de l’interface `ICommandProperties` est fournie par une fonction statique définie par la macro `BEGIN_PROPSET_MAP`. Obligatoire sur les commandes.

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
Définit, stocke et retourne le texte de la commande. Obligatoire sur les commandes.

[Idbcreatecommandimpl,](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
Crée une nouvelle commande à partir de l’objet session et retourne l’interface demandée sur la commande nouvellement créée. Interface facultative sur les objets de session.

D’autres classes de commandes sont `IColumnsInfoImpl` et `IAccessorImpl`, décrites dans la section classes d’ensemble de lignes ci-dessus.

## <a name="data-source-classes"></a>Classes de source de données

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
Crée et supprime la connexion avec le consommateur. Interface obligatoire sur les objets de source de données et interface facultative sur les énumérateurs.

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` est une interface obligatoire pour les objets de source de données et une interface facultative pour les énumérateurs. Toutefois, si un énumérateur expose `IDBInitialize`, il doit exposer `IDBProperties` (propriétés sur la source de données).

[Igetdatasourceimpl,](../../data/oledb/igetdatasourceimpl-class.md)<br/>
Obtient un pointeur d’interface vers l’objet source de données. Interface obligatoire sur la session.

## <a name="other-classes"></a>Autres classes

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
Implémente des propriétés pour diverses OLE DB interfaces de propriété (par exemple, `IDBProperties`, `ISessionProperties`et `IRowsetInfo`).

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

Implémente OLE DB l’interface [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) , en ajoutant des enregistrements et en extrayant des enregistrements à partir d’un membre de données.

## <a name="see-also"></a>Voir aussi

[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Modèles OLE DB](../../data/oledb/ole-db-templates.md)

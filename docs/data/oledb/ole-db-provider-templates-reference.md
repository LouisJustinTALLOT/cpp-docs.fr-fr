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
ms.openlocfilehash: 04ee2d36d269d3bc9324b10dffd8840f9f68a8ab
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220885"
---
# <a name="ole-db-provider-templates-reference"></a>Référence des modèles du fournisseur OLE DB
Les classes et interfaces pour les modèles du fournisseur OLE DB peuvent être regroupées dans les catégories suivantes. La documentation de référence inclut également des informations sur le [macros pour les modèles du fournisseur OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).  
  
 Les classes utilisent la convention d’affectation de noms suivante : une classe nommée avec le modèle `IWidgetImpl` fournirait une implémentation de l’interface `IWidget`.  
  
## <a name="session-classes"></a>Classes de session  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 Crée une nouvelle session de l’objet de source de données et retourne l’interface demandée sur la session nouvellement créée. Interface obligatoire sur les objets de source de données.  
  
 [ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)  
 Implémente des propriétés d’une session en appelant une fonction statique définie par le mappage de jeu de propriétés. Le mappage de jeu de propriétés doit être spécifié dans votre classe session. Interface obligatoire sur les sessions.  
  
## <a name="rowset-classes"></a>Classes de l’ensemble de lignes  
 [CRowsetImpl](../../data/oledb/crowsetimpl-class.md)  
  
 Fournit une implémentation d’ensemble de lignes OLE DB standard sans nécessiter l’héritage multiple de nombreuses interfaces d’implémentation. La seule méthode pour laquelle vous devez fournir l’implémentation est `Execute`.  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 Fournit une implémentation par défaut pour le handle de ligne, qui est utilisé dans le `IRowsetImpl` classe. Un handle de ligne est logiquement une balise unique pour une ligne de résultat. `IRowsetImpl` Crée un `CSimpleRow` pour chaque ligne demandée dans `IRowsetImpl::GetNextRows`.  
  
 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB requiert des fournisseurs implémenter un `HACCESSOR`, qui est une balise à un tableau de `DBBINDING` structures. Fournit des `HACCESSOR`s qui sont des adresses de la `BindType` structures. Obligatoire sur les ensembles de lignes et de commandes.  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 Délégués à une fonction statique définie par le mappage de colonne du fournisseur. Interface obligatoire sur les ensembles de lignes et de commandes.  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 Fournit des informations sur la disponibilité de conversions de type sur une commande ou sur un ensemble de lignes. Obligatoire sur les commandes, les ensembles de lignes et les ensembles de lignes index. Implémente le `IConvertType` interface par délégation à l’objet de conversion fourni par OLE DB.  
  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)  
 Implémente le `IDBSchemaRowset` interface et la fonction de créateur mise en modèle `CreateSchemaRowset`.  
  
 [IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)  
 Ouvre et retourne un ensemble de lignes qui inclut toutes les lignes à partir d’une seule table de base ou un index. Interface obligatoire pour un objet de session.  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 Implémente la norme OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\)) interface, ce qui permet la mise à jour des valeurs de colonnes dans les lignes existantes, la suppression de lignes et l’insertion de nouvelles lignes.  
  
 [IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)  
 Cette classe hérite de [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) et remplace [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite). `IRowsetCreatorImpl` effectue les mêmes fonctions que `IObjectWithSite` mais permet également les propriétés OLE DB `DBPROPCANSCROLLBACKWARDS` et `DBPROPCANFETCHBACKWARDS`.  
  
 [IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)  
 Implémente le `IRowsetIdentity` interface, ce qui vous permet de comparer si deux lignes de données sont identiques ou non.  
  
 [IRowsetImpl](../../data/oledb/irowsetimpl-class.md)  
 Fournit une implémentation de la `IRowset` interface, qui est l’interface de l’ensemble de lignes de base.  
  
 [IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)  
 Implémente les propriétés de l’ensemble de lignes à l’aide de la propriété jeu plan défini dans votre classe de commande. Interface obligatoire sur les ensembles de lignes.  
  
 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)  
 Implémente la norme OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190\(v=vs.85\)) interface, qui extrait des lignes arbitraires à partir d’un ensemble de lignes. Pour prendre en charge des signets de OLE DB dans un ensemble de lignes, vérifiez l’ensemble de lignes à hériter de cette classe.  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 Implémente des fonctions pour informer les écouteurs sur le point de connexion de diffusion `IID_IRowsetNotify` des modifications apportées au contenu de l’ensemble de lignes. Implémentent des consommateurs qui gèrent les notifications [IRowsetNotify](/previous-versions/windows/desktop/ms712959\(v=vs.85\)) et l’inscrire sur ce point de connexion.  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 Implémente la norme OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401\(v=vs.85\)) interface, ce qui permet aux consommateurs de retarder la transmission des modifications apportées avec [IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\)) à source de données et annuler les modifications avant la transmission.  
  
## <a name="command-classes"></a>Classes de commande  
 [ICommandImpl](../../data/oledb/icommandimpl-class.md)  
 Fournit une implémentation de l’interface `ICommand`. Cette interface n’est pas visible, mais il est gérée par `ICommandTextImpl`. Une interface obligatoire sur l’objet command.  
  
 [ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)  
 Cette implémentation de la `ICommandProperties` interface est fournie par une fonction statique définie par le `BEGIN_PROPSET_MAP` (macro). Obligatoire sur les commandes.  
  
 [ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)  
 Définit, stocke et retourne le texte de commande. Obligatoire sur les commandes.  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 Crée une nouvelle commande à partir de l’objet de session et retourne l’interface demandée sur la commande qui vient d’être créée. Interface facultative sur les objets de session.  
  
 Autres classes de commande sont `IColumnsInfoImpl` et `IAccessorImpl`, comme décrit dans la section de Classes de l’ensemble de lignes ci-dessus.  
  
## <a name="data-source-classes"></a>Classes de Source de données  
 [IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)  
 Crée et supprime la connexion avec le consommateur. Interface obligatoire sur les objets source de données et une interface facultative sur les énumérateurs.  
  
 [IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties` est une interface obligatoire pour les objets de source de données et une interface facultative pour les énumérateurs. Toutefois, si un énumérateur expose `IDBInitialize`, elle doit exposer `IDBProperties` (propriétés sur la source de données).  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 Obtient un pointeur d’interface à l’objet de source de données. Interface obligatoire sur la session.  
  
## <a name="other-classes"></a>Autres Classes  
 [CUtlProps](../../data/oledb/cutlprops-class.md)  
 Implémente des propriétés d’une série d’interfaces de propriété OLE DB (par exemple, `IDBProperties`, `ISessionProperties`, et `IRowsetInfo`).  
  
 [IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 Implémente la norme OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112\(v=vs.85\)) interface, ajout d’enregistrements à et récupérer des enregistrements d’un membre de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Modèles OLE DB](../../data/oledb/ole-db-templates.md)
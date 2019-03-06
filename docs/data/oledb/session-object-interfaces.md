---
title: Interfaces de l'objet session
ms.date: 11/19/2018
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
ms.openlocfilehash: 7e8a9cd204a07afc2b14c6a1e31e7c970c27cfc2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423376"
---
# <a name="session-object-interfaces"></a>Interfaces de l'objet session

Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de session.

|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85))|Obligatoire|Oui|
|[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85))|Obligatoire|Oui|
|[ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))|Obligatoire|Oui|
|[IAlterIndex](/previous-versions/windows/desktop/ms714943(v=vs.85))|Facultatif|Aucune|
|[IAlterTable](/previous-versions/windows/desktop/ms719764(v=vs.85))|Facultatif|Aucune|
|[IBindResource](/previous-versions/windows/desktop/ms714936(v=vs.85))|Facultatif|Aucune|
|[ICreateRow](/previous-versions/windows/desktop/ms716832(v=vs.85))|Facultatif|Aucune|
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85))|Facultatif|Oui|
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))|Facultatif|Oui|
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593(v=vs.85))|Facultatif|Aucune|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Facultatif|Oui|
|[ITableCreation](/previous-versions/windows/desktop/ms713639(v=vs.85))|Facultatif|Aucune|
|[ITableDefinition](/previous-versions/windows/desktop/ms714277(v=vs.85))|Facultatif|Aucune|
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947(v=vs.85))|Facultatif|Aucune|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Facultatif|Aucune|
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071(v=vs.85))|Facultatif|Aucune|
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893(v=vs.85))|Facultatif|Aucune|
|[ITransactionObject](/previous-versions/windows/desktop/ms713659(v=vs.85))|Facultatif|Aucune|

L’objet session crée un objet d’ensemble de lignes. Si le fournisseur prend en charge les commandes, la session crée également un objet de commande (`CCommand`, implémentation OLE DB `TCommand`). Implémente l’objet de commande le `ICommand` interface et utilise le `ICommand::Execute` méthode à exécuter des commandes sur l’ensemble de lignes, comme indiqué dans l’illustration suivante.

![Diagramme conceptuel des fournisseurs](../../data/oledb/media/vc4u551.gif "diagramme conceptuel des fournisseurs")

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>

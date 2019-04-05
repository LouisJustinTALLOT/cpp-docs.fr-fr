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
ms.openlocfilehash: 2fb91365fec0709e1bb2a26afa519e6565862681
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031446"
---
# <a name="session-object-interfaces"></a>Interfaces de l'objet session

Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de session.

|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85))|Obligatoire|Oui|
|[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85))|Obligatoire|Oui|
|[ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))|Obligatoire|Oui|
|[IAlterIndex](/previous-versions/windows/desktop/ms714943(v=vs.85))|Facultatif|Non|
|[IAlterTable](/previous-versions/windows/desktop/ms719764(v=vs.85))|Facultatif|Non|
|[IBindResource](/previous-versions/windows/desktop/ms714936(v=vs.85))|Facultatif|Non|
|[ICreateRow](/previous-versions/windows/desktop/ms716832(v=vs.85))|Facultatif|Non|
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85))|Facultatif|Oui|
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))|Facultatif|Oui|
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593(v=vs.85))|Facultatif|Non|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Facultatif|Oui|
|[ITableCreation](/previous-versions/windows/desktop/ms713639(v=vs.85))|Facultatif|Non|
|[ITableDefinition](/previous-versions/windows/desktop/ms714277(v=vs.85))|Facultatif|Non|
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947(v=vs.85))|Facultatif|Non|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Facultatif|Non|
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071(v=vs.85))|Facultatif|Non|
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893(v=vs.85))|Facultatif|Non|
|[ITransactionObject](/previous-versions/windows/desktop/ms713659(v=vs.85))|Facultatif|Non|

L’objet session crée un objet d’ensemble de lignes. Si le fournisseur prend en charge les commandes, la session crée également un objet de commande (`CCommand`, implémentation OLE DB `TCommand`). Implémente l’objet de commande le `ICommand` interface et utilise le `ICommand::Execute` méthode à exécuter des commandes sur l’ensemble de lignes, comme indiqué dans l’illustration suivante.

![Diagramme conceptuel des fournisseurs](../../data/oledb/media/vc4u551.gif "diagramme conceptuel des fournisseurs")

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>

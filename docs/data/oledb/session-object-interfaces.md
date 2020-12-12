---
description: 'En savoir plus sur : interfaces d’objet de session'
title: Interfaces de l'objet Session
ms.date: 11/19/2018
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
ms.openlocfilehash: dc4f5644258b0ced4c97a5cda6de1b69abb8c2f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286577"
---
# <a name="session-object-interfaces"></a>Interfaces de l'objet Session

Le tableau suivant indique les interfaces obligatoires et facultatives définies par OLE DB pour un objet de session.

|Interface|Requis ?|Implémenté par OLE DB modèles ?|
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

L’objet session crée un objet rowset. Si le fournisseur prend en charge les commandes, la session crée également un objet Command ( `CCommand` , implémentant le OLE DB `TCommand` ). L’objet Command implémente l' `ICommand` interface et utilise la `ICommand::Execute` méthode pour exécuter des commandes sur l’ensemble de lignes, comme indiqué dans l’illustration suivante.

![Diagramme conceptuel des fournisseurs](../../data/oledb/media/vc4u551.gif "Diagramme conceptuel des fournisseurs")

## <a name="see-also"></a>Voir aussi

[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>

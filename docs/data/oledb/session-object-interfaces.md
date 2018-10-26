---
title: Interfaces de l’objet session | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0b88a2b04862743839b3cd438b31506c8aea0883
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079915"
---
# <a name="session-object-interfaces"></a>Interfaces de l'objet session

Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de session.

|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](/previous-versions/windows/desktop/ms709721)|Obligatoire|Oui|
|[IOpenRowset](/previous-versions/windows/desktop/ms716946)|Obligatoire|Oui|
|[ISessionProperties](/previous-versions/windows/desktop/ms713721)|Obligatoire|Oui|
|[IAlterIndex](/previous-versions/windows/desktop/ms714943)|Facultatif|Non|
|[IAlterTable](/previous-versions/windows/desktop/ms719764)|Facultatif|Non|
|[IBindResource](/previous-versions/windows/desktop/ms714936)|Facultatif|Non|
|[ICreateRow](/previous-versions/windows/desktop/ms716832)|Facultatif|Non|
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625)|Facultatif|Oui|
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)|Facultatif|Oui|
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593)|Facultatif|Non|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|Facultatif|Oui|
|[ITableCreation](/previous-versions/windows/desktop/ms713639)|Facultatif|Non|
|[ITableDefinition](/previous-versions/windows/desktop/ms714277)|Facultatif|Non|
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947)|Facultatif|Non|
|[ITransaction](/previous-versions/windows/desktop/ms723053)|Facultatif|Non|
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071)|Facultatif|Non|
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893)|Facultatif|Non|
|[ITransactionObject](/previous-versions/windows/desktop/ms713659)|Facultatif|Non|

L’objet session crée un objet d’ensemble de lignes. Si le fournisseur prend en charge les commandes, la session crée également un objet de commande (`CCommand`, implémentation OLE DB `TCommand`). Implémente l’objet de commande le `ICommand` interface et utilise le `ICommand::Execute` méthode à exécuter des commandes sur l’ensemble de lignes, comme indiqué dans l’illustration suivante.

![Diagramme conceptuel des fournisseurs](../../data/oledb/media/vc4u551.gif "vc4u551")

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
---
description: 'En savoir plus sur : TN047 : assouplissement des exigences relatives aux transactions de base de données'
title: 'TN047 : assouplissement des spécifications relatives aux transactions de base de données'
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
ms.openlocfilehash: 6f356db75df93466bc392e555246a363e6b52187
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215116"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047 : assouplissement des spécifications relatives aux transactions de base de données

Cette note technique, qui a abordé les exigences en matière de transactions des classes de base de données ODBC MFC, est désormais obsolète. Avant MFC 4,2, les classes de base de données nécessitaient que les curseurs soient conservés sur les recordsets après une opération **CommitTrans** ou **Rollback** . Si le pilote ODBC et le SGBD ne prenaient pas en charge ce niveau de conservation des curseurs, les classes de base de données n’activaient pas de transactions.

À partir de MFC 4,2, les classes de base de données ont allégé la restriction de la conservation du curseur. Les transactions sont activées si le pilote les prend en charge. Toutefois, vous devez maintenant vérifier l’effet d’une opération **CommitTrans** ou **Rollback** sur les recordsets ouverts. Pour plus d’informations, consultez fonctions membres [CDatabase :: GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) et [CDatabase :: GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) .

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

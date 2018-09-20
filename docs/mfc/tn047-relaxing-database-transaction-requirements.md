---
title: 'TN047 : Assouplissement des spécifications de Transaction de base de données | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96f3116f503ffa0ffc461ea2c1a0bdaf8947a0be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427015"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047 : assouplissement des exigences relatives aux transactions de base de données

Cette note technique, qui décrit les critères de transaction des classes de base de données ODBC MFC, est désormais obsolète. Avant de 4.2 de MFC, les classes de base de données requis que les curseurs conservé sur les jeux d’enregistrements après un **CommitTrans** ou **Rollback** opération. Si le pilote ODBC et le SGBD ne prenait pas en charge ce niveau de la conservation de curseur, les classes de base de données n’avez pas activé les transactions.

Depuis la version 4.2 de MFC, les classes de base de données ont allégées la restriction de nécessiter la conservation de curseur. Transactions seront activées si le pilote prend en charge les. Toutefois, vous devez maintenant vérifier l’effet d’un **CommitTrans** ou **Rollback** opération sur les recordsets ouverts. Consultez les fonctions membres [CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) et [CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)


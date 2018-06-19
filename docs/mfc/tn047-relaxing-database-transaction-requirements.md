---
title: 'TN047 : Assouplissement des spécifications de Transaction de base de données aux | Documents Microsoft'
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
ms.openlocfilehash: be5870efacb61d5c0bb74f85427c41f787d2edd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380931"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047 : assouplissement des exigences relatives aux transactions de base de données
Cette note technique, qui décrit les spécifications des transactions des classes de base de données ODBC MFC, est désormais obsolète. Avant de 4.2 de MFC, les classes de base de données requis que les curseurs être conservés sur des jeux d’enregistrements après un **CommitTrans** ou **restauration** opération. Si le pilote ODBC et le SGBD ne prenait pas en charge ce niveau de la conservation de curseur, les classes de base de données n’avez pas activé les transactions.  
  
 Depuis la version 4.2 de MFC, les classes de base de données ont allégées la restriction de nécessiter la préservation de curseur. Transactions seront activées si le pilote prend en charge les. Toutefois, vous devez vérifier maintenant l’effet d’un **CommitTrans** ou **restauration** opération sur les jeux d’enregistrements ouverts. Consultez les fonctions membres [CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) et [CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)


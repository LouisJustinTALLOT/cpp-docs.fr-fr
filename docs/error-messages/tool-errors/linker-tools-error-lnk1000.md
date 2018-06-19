---
title: LNK1000 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1000
dev_langs:
- C++
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f67df9c53b79fabfc9559380b5b57a72e64cb8a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298234"
---
# <a name="linker-tools-error-lnk1000"></a>Erreur des outils Éditeur de liens LNK1000
Erreur inconnue ; consultez la documentation pour les options de support technique  
  
 Notez les circonstances de l’erreur, essayez d’isoler le problème et de créer un cas de test reproductible, puis contactez `Microsoft Product Support Services`. Pour plus d’informations sur la façon d’examiner et de signaler ces erreurs, consultez [ http://support.microsoft.com/default.aspx?scid=kb; en-us ; 134650](http://support.microsoft.com/default.aspx?scid=kb;en-us;134650).  
  
 Vous pouvez obtenir cette erreur si vous combinez des fichiers d’en-tête standard (par exemple, dos.h) et vos propres fichiers. `#include` les en-têtes standard en premier lieu, suivi par vos propres fichiers d’en-tête.
---
title: LNK1000 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 06/18/2018
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
ms.openlocfilehash: 7a01db36200995813ec4b6862e9ddd04c6f069ba
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238680"
---
# <a name="linker-tools-error-lnk1000"></a>Erreur des outils Éditeur de liens LNK1000

> Erreur inconnue ; consultez la documentation pour les options de support technique

Notez les circonstances de l’erreur, puis essayez d’isoler le problème et de créer un cas de test reproductible. Pour plus d’informations sur la façon d’examiner et de signaler ces erreurs, consultez [comment signaler un problème avec l’ensemble d’outils Visual C++ ou la documentation](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Vous pouvez obtenir cette erreur si vous combinez des fichiers d’en-tête standard (par exemple, Windows.h) et vos propres fichiers. Inclure un en-tête précompilé, si un, en premier, puis les en-têtes standards, suivi de vos propres fichiers d’en-tête.
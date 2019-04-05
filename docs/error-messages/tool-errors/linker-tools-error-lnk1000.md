---
title: Erreur des outils Éditeur de liens LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: b0e6eb3ba44216e9300506eb84adb61a6529903d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781495"
---
# <a name="linker-tools-error-lnk1000"></a>Erreur des outils Éditeur de liens LNK1000

> Erreur inconnue ; consultez la documentation pour les options de support technique

Notez les circonstances de l’erreur, puis essayez d’isoler le problème et de créer un cas de test reproductible. Pour plus d’informations sur la façon d’examiner et de signaler ces erreurs, consultez [comment signaler un problème avec l’ensemble d’outils Visual C++ ou la documentation](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Vous pouvez obtenir cette erreur si vous combinez vos propres fichiers et les fichiers d’en-tête standard (par exemple, Windows.h). Inclure un en-tête précompilé, si un, en premier, puis les en-têtes standard, suivi de vos propres fichiers d’en-tête.
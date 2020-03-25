---
title: Erreur des outils Éditeur de liens LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 48b976f6e996d0e076849dc9b20b4cedd47dfbcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195420"
---
# <a name="linker-tools-error-lnk1000"></a>Erreur des outils Éditeur de liens LNK1000

> erreur inconnue ; consulter la documentation pour les options de support technique

Notez les circonstances de l’erreur, puis essayez d’isoler le problème et de créer un cas de test reproductible. Pour plus d’informations sur la façon d’examiner et de signaler ces erreurs, consultez [Guide pratique pour signaler C++ un problème avec l’ensemble d’outils ou la documentation de Visual](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Vous pouvez obtenir cette erreur si vous combinez des fichiers d’en-tête standard (par exemple, Windows. h) et vos propres fichiers. Incluez un en-tête précompilé, le cas échéant, d’abord, puis les en-têtes standard, suivis de vos propres fichiers d’en-tête.

---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1000'
title: Erreur des outils Éditeur de liens LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 54692b635b83756a26490779c0205ccc5f20d3bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261604"
---
# <a name="linker-tools-error-lnk1000"></a>Erreur des outils Éditeur de liens LNK1000

> erreur inconnue ; consulter la documentation pour les options de support technique

Notez les circonstances de l’erreur, puis essayez d’isoler le problème et de créer un cas de test reproductible. Pour plus d’informations sur la façon d’examiner et de signaler ces erreurs, consultez [Guide pratique pour signaler un problème avec l’ensemble d’outils Visual C++ ou la documentation](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Vous pouvez obtenir cette erreur si vous combinez des fichiers d’en-tête standard (par exemple, Windows. h) et vos propres fichiers. Incluez un en-tête précompilé, le cas échéant, d’abord, puis les en-têtes standard, suivis de vos propres fichiers d’en-tête.

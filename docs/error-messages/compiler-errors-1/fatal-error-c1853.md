---
title: Erreur irrécupérable C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: ec2d6bf6bac46cca8bdc2e3b8fe7cc6b7799d78a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165916"
---
# <a name="fatal-error-c1853"></a>Erreur irrécupérable C1853

> «*filename*« fichier d’en-tête précompilé est d’une version précédente du compilateur, ou l’en-tête précompilé est en C++ et vous l’utilisez C (ou inversement)

Causes possibles :

- L’en-tête précompilé a été compilé avec une version précédente du compilateur. Essayez de recompiler l’en-tête avec le compilateur actuel.

- L’en-tête précompilé est en C++ et vous l’utilisez de réessayez C. recompiler l’en-tête pour une utilisation avec C en spécifiant un de le [TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) options du compilateur, ou en remplaçant le suffixe du fichier source par « c ». Pour plus d’informations, consultez [deux possibilités pour précompiler le Code](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).
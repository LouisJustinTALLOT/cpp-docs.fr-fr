---
title: Erreur irrécupérable C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 056db975fecef4e101dbbba7e2084236489498c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202863"
---
# <a name="fatal-error-c1853"></a>Erreur irrécupérable C1853

> le fichier d’en-tête précompilé'*nom_fichier*'provient d’une version antérieure du compilateur, ou l’en C++ -tête précompilé est et vous l’utilisez à partir de C (ou vice versa)

Causes possibles :

- L’en-tête précompilé a été compilé avec une version antérieure du compilateur. Essayez de recompiler l’en-tête avec le compilateur actuel.

- L’en-tête précompilé est C++ et vous l’utilisez à partir de c. essayez de recompiler l’en-tête pour l’utiliser avec c en spécifiant l’une des options du compilateur [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) ou en remplaçant le suffixe du fichier source par « C ». Pour plus d’informations, consultez [deux options pour la précompilation du code](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).

---
description: 'En savoir plus sur : erreur irrécupérable C1853'
title: Erreur irrécupérable C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 60c8e254e9bd36f52bddb4d6dce56c987b6c31e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276229"
---
# <a name="fatal-error-c1853"></a>Erreur irrécupérable C1853

> le fichier d’en-tête précompilé'*nom_fichier*'provient d’une version antérieure du compilateur, ou l’en-tête précompilé est en C++ et vous l’utilisez à partir de C (ou vice versa)

Causes possibles :

- L’en-tête précompilé a été compilé avec une version antérieure du compilateur. Essayez de recompiler l’en-tête avec le compilateur actuel.

- L’en-tête précompilé est en C++ et vous l’utilisez à partir de C. essayez de recompiler l’en-tête pour l’utiliser avec C en spécifiant l’une des options du compilateur [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) ou en remplaçant le suffixe du fichier source par « C ». Pour plus d’informations, consultez [deux options pour la précompilation du code](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).
